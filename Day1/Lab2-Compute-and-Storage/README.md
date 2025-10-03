# 📘 README 2 — Lab 2: Compute & Storage (EC2 + S3)

## 🎯 Objective
- Launch and connect to an EC2 instance
- Install a web server
- Upload and download files from S3

## ✅ Prerequisites
- Completed Lab 1 (IAM + CLI setup)
- SSH client installed (Linux/macOS: built-in, Windows: PuTTY or WSL)

## ⏱ Estimated Time
~1.5 hours

## 📝 Step-by-Step Instructions
1. **Launch EC2 Instance**
   - Navigate: **EC2 → Launch Instance**.
   - AMI: Amazon Linux 2
   - Instance type: `t2.micro` (Free Tier)
   - Key pair: create/download `.pem` file
   - Security group: allow SSH (22) + HTTP (80).

2. **Connect via SSH**
   ```bash
   chmod 400 mykey.pem
   ssh -i mykey.pem ec2-user@<public-ip>
