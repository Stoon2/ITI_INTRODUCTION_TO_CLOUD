# 📘 README 1 — Lab 1: Getting Started with AWS Console & CLI

## 🎯 Objective
- Familiarize with the AWS Management Console  
- Create an IAM user with limited permissions  
- Configure AWS CLI for programmatic access  

## ✅ Prerequisites
- AWS account (root credentials available for setup)  
- Laptop with internet access  
- Installed [AWS CLI v2](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)  
- Basic knowledge of Linux terminal  

## ⏱ Estimated Time
~1.5 hours  

## 📝 Step-by-Step Instructions
1. **Sign in to AWS Console**  
   - Go to [AWS Console](https://aws.amazon.com/console/).  
   - Log in with root credentials.  

2. **Create IAM User**  
   - Navigate to **IAM → Users → Add User**.  
   - Username: `student-user`  
   - Select **Programmatic access** + **AWS Management Console access**.  
   - Attach policy: `AdministratorAccess` (for now, later restrict).  
   - Save credentials (Access Key + Secret Key).  

3. **Set up AWS CLI**  
   - Run:  
     ```bash
     aws configure
     ```
   - Enter Access Key, Secret Key, region (`us-east-1`), output format (`json`).  

4. **Verify CLI**  
   ```bash
   aws s3 ls
   aws ec2 describe-regions --output table
