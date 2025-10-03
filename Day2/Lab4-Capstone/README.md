# 📘 README 4 — Lab 4: High Availability Web App (EC2 + RDS + ALB, Python Version)

## 🎯 Objective
- Deploy a two-tier application: Flask web app (web tier) + MySQL RDS (database tier)
- Connect EC2 instance to RDS securely
- Place EC2 behind an Application Load Balancer (ALB) for high availability

## ✅ Prerequisites
- Completed Lab 3 (VPC setup with public/private subnets)
- AWS CLI configured with IAM user credentials
- SSH key pair available for EC2 login
- Basic familiarity with Python and Linux terminal

## ⏱ Estimated Time
~1.5 hours

---

## 📝 Step-by-Step Instructions

### 1. Create RDS Database
1. In the AWS Console, go to **RDS → Databases → Create database**.
2. Select **Standard Create**.
3. Engine: **MySQL** (Free Tier eligible).
4. Templates: **Free tier**.
5. DB instance identifier: `student-db`.
6. Master username: `admin`.
7. Master password: choose a secure password.
8. Instance class: `db.t3.micro`.
9. Storage: default (20 GB).
10. Connectivity:
    - VPC: select your custom VPC.
    - Subnet group: private subnets.
    - Public access: **No**.
    - Security group: allow **MySQL (3306)** inbound from your web EC2’s security group.
11. Create database and wait until status = **Available**.
12. Note the **RDS endpoint** (e.g., `student-db.xxxxx.us-east-1.rds.amazonaws.com`).

---

### 2. Launch Web EC2 Instance
1. Navigate to **EC2 → Launch Instance**.
2. Name: `flask-web`.
3. AMI: **Amazon Linux 2**.
4. Instance type: `t2.micro`.
5. Key pair: select existing or create new.
6. Network: place in **public subnet** of your VPC.
7. Security group: allow **SSH (22)** and **HTTP (80)**.
8. Launch instance.
9. Connect via SSH:
   ```bash
   ssh -i mykey.pem ec2-user@<EC2-PUBLIC-IP>
   ```

---

### 3. Install Python & Flask on EC2
Run the following commands on your EC2 instance:

```bash
# Update system packages
sudo yum update -y

# Enable Python 3.8
sudo amazon-linux-extras enable python3.8

# Install Python 3.8 and pip
sudo yum install -y python3.8 python3-pip git

# Upgrade pip
pip3 install --upgrade pip

# Install Flask and PyMySQL
pip3 install flask pymysql
```

---

### 4. Create Flask App
1. Create a project folder:
   ```bash
   mkdir ~/flaskapp && cd ~/flaskapp
   ```
2. Create `app.py`:
   ```bash
   nano app.py
   ```
3. Paste the following code (replace `DB-ENDPOINT`, `USERNAME`, `PASSWORD`, `DBNAME` with your RDS values):

   ```python
   from flask import Flask
   import pymysql

   app = Flask(__name__)

   @app.route("/")
   def index():
       try:
           conn = pymysql.connect(
               host="DB-ENDPOINT",
               user="USERNAME",
               password="PASSWORD",
               database="DBNAME",
               connect_timeout=5
           )
           return "✅ Connected to RDS successfully!"
       except Exception as e:
           return f"❌ Connection failed: {e}"

   if __name__ == "__main__":
       app.run(host="0.0.0.0", port=80)
   ```

---

### 5. Run Flask App
```bash
sudo python3 app.py
```

- Open a browser and visit: `http://<EC2-PUBLIC-IP>`
- You should see either a success or failure message.

---

### 6. Run Flask App as a Service (Optional but Recommended)
To keep the app running after logout, configure it as a systemd service:

```bash
sudo nano /etc/systemd/system/flaskapp.service
```

Paste:

```ini
[Unit]
Description=Flask App
After=network.target

[Service]
User=ec2-user
WorkingDirectory=/home/ec2-user/flaskapp
ExecStart=/usr/bin/python3 /home/ec2-user/flaskapp/app.py
Restart=always

[Install]
WantedBy=multi-user.target
```

Enable and start:

```bash
sudo systemctl daemon-reload
sudo systemctl enable flaskapp
sudo systemctl start flaskapp
```

Check status:

```bash
sudo systemctl status flaskapp
```

---

### 7. Create Application Load Balancer
1. Go to **EC2 → Load Balancers → Create Load Balancer**.
2. Choose **Application Load Balancer**.
3. Name: `student-alb`.
4. Scheme: **Internet-facing**.
5. Listeners: HTTP (80).
6. VPC: select your custom VPC.
7. Availability Zones: select at least 2 public subnets.
8. Create a **Target Group**:
   - Type: Instances
   - Protocol: HTTP (80)
   - Register your EC2 instance.
9. Finish ALB creation.
10. Once ALB is active, copy its **DNS name**.

---

### 8. Test the Setup
- Visit `http://<ALB-DNS-NAME>` in your browser.
- You should see the Flask app response confirming RDS connectivity.

---

## 🔍 Validation
- Flask app loads via EC2 public IP.
- ALB DNS name serves the app.
- App confirms successful connection to RDS.

---

## 💡 Reflection
- Why is the database placed in a private subnet?
- How does ALB improve fault tolerance and scalability?
- What additional steps would you take to make this app production-ready (e.g., Auto Scaling, secrets management, HTTPS with ACM)?

---

## 📚 References
- [Amazon RDS Documentation](https://docs.aws.amazon.com/rds/index.html)
- [Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/index.html)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [PyMySQL Documentation](https://pymysql.readthedocs.io/)
- [AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
