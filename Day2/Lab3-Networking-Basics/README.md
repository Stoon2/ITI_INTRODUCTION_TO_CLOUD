# 📘 README 3 — Lab 3: Networking Basics (VPC & Security Groups)

## 🎯 Objective
- Create a custom VPC with public and private subnets  
- Launch instances in each subnet  
- Test connectivity with security groups  

## ✅ Prerequisites
- Completed Lab 2 (EC2 familiarity)  

## ⏱ Estimated Time
~1.5 hours  

## 📝 Step-by-Step Instructions
1. **Create VPC**  
   - Navigate: **VPC → Create VPC**.  
   - Name: `student-vpc`  
   - CIDR: `10.0.0.0/16`.  

2. **Create Subnets**  
   - Public subnet: `10.0.1.0/24`  
   - Private subnet: `10.0.2.0/24`.  

3. **Internet Gateway**  
   - Create IGW, attach to VPC.  
   - Update route table for public subnet → `0.0.0.0/0` via IGW.  

4. **Launch Instances**  
   - Public subnet: EC2 with public IP.  
   - Private subnet: EC2 without public IP.  

5. **Security Groups**  
   - Public SG: allow SSH + HTTP.  
   - Private SG: allow SSH only from Public SG.  

6. **Test Connectivity**  
   - SSH into public EC2.  
   - From there, SSH into private EC2.  

## 🔍 Validation
- Public EC2 accessible from internet.  
- Private EC2 only accessible via public EC2.  

## 💡 Reflection
- Why isolate workloads into private subnets?  
- How do security groups differ from firewalls?  

## 📚 References
- [Amazon VPC Documentation](https://docs.aws.amazon.com/vpc/index.html)  
- [Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)  