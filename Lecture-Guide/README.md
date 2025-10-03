## 📅 Day 1 – Foundations & Core Services (3h Lecture)

### **1. Introduction to Cloud Computing (45 min)**
- Define **Cloud Computing** in simple terms
- Compare **IaaS vs PaaS vs SaaS** with real-world analogies
- Explain **benefits**: scalability, elasticity, pay-as-you-go
- Introduce the **Shared Responsibility Model**
  - AWS vs Customer responsibilities
  - Example: AWS secures the data center, you secure your EC2 instance

**References**
- [What is Cloud Computing?](https://aws.amazon.com/what-is-cloud-computing/)
- [Types of Cloud Computing](https://aws.amazon.com/types-of-cloud-computing/)
- [Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)

**Reflection Questions**
- How does cloud computing differ from traditional on-premises infrastructure you may have used before?
- Which service model (IaaS, PaaS, SaaS) do you think most companies adopt first, and why?
- In the Shared Responsibility Model, what’s one example of a security task AWS handles vs one you must handle?

---

### **2. AWS Global Infrastructure (30 min)**
- Define **Regions, Availability Zones, Edge Locations**
- Show AWS Global Infrastructure map
- Discuss **latency, redundancy, compliance** considerations
- Example: Why choose `eu-central-1` vs `us-east-1`

**References**
- [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)
- [Regions & Availability Zones](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html)
- [CloudFront & Edge Locations](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)

**Reflection Questions**
- If your users are in Europe but your servers are in the US, what challenges might arise?
- Why might a company choose to deploy in multiple Availability Zones?
- How do edge locations improve user experience?

---

### **3. Core AWS Services Overview (60 min)**
- **Compute**: EC2 basics, Lambda intro
- **Storage**: S3 buckets, objects, durability
- **Networking**: VPC basics, security groups, IAM basics

**References**
- [Amazon EC2](https://docs.aws.amazon.com/ec2/index.html)
- [AWS Lambda](https://docs.aws.amazon.com/lambda/index.html)
- [Amazon S3](https://docs.aws.amazon.com/s3/index.html)
- [Amazon VPC](https://docs.aws.amazon.com/vpc/index.html)
- [Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)
- [IAM Overview](https://docs.aws.amazon.com/iam/index.html)

**Reflection Questions**
- When would you choose EC2 over Lambda for running code?
- Why is S3 considered “infinitely scalable” storage?
- How do security groups differ from IAM policies in controlling access?

---

### **4. Identity & Access Management (IAM) (45 min)**
- IAM **users, groups, roles, policies**
- JSON policy structure
- Principle of **least privilege**
- Best practices: MFA, avoid root account, use roles

**References**
- [IAM Introduction](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
- [IAM Policy Elements](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html)
- [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)

**Reflection Questions**
- Why is it dangerous to use the root account for daily tasks?
- What’s the difference between a role and a user in IAM?
- How would you explain “least privilege” to a non-technical stakeholder?

---

## 📅 Day 2 – Building & Observability (3h Lecture)

### **1. Elasticity & Scaling (45 min)**
- Auto Scaling Groups (ASG) basics
- Scaling policies
- Load Balancers (ALB)

**References**
- [Auto Scaling Groups](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)
- [Application Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)

**Reflection Questions**
- Why is elasticity one of the biggest advantages of cloud?
- How does an ALB improve availability compared to a single EC2 instance?
- Can you think of a scenario where scaling down is just as important as scaling up?

---

### **2. Databases in AWS (45 min)**
- RDS overview (relational DB)
- DynamoDB overview (NoSQL DB)
- Compare RDS vs DynamoDB

**References**
- [Amazon RDS](https://docs.aws.amazon.com/rds/index.html)
- [Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/index.html)
- [Choosing Between RDS & DynamoDB](https://aws.amazon.com/nosql/)

**Reflection Questions**
- What are the trade-offs between relational and NoSQL databases?
- Why might a startup choose DynamoDB over RDS?
- How does AWS handle backups differently in RDS vs DynamoDB?

---

### **3. Monitoring & Logging (45 min)**
- CloudWatch metrics, alarms, dashboards
- CloudTrail for auditing

**References**
- [Amazon CloudWatch](https://docs.aws.amazon.com/cloudwatch/index.html)
- [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)

**Reflection Questions**
- Why is monitoring critical even for small applications?
- How would you use CloudWatch alarms to prevent downtime?
- What kind of suspicious activity might CloudTrail help you detect?

---

### **4. Cost Management & Best Practices (45 min)**
- Pricing models (On-Demand, Reserved, Spot)
- AWS Free Tier & Budgets
- Well-Architected Framework (5 pillars)

**References**
- [AWS Pricing](https://aws.amazon.com/pricing/)
- [AWS Free Tier](https://aws.amazon.com/free/)
- [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html)
- [Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)

**Reflection Questions**
- Why might a company choose Reserved Instances over On-Demand?
- How can poor architecture decisions lead to higher costs?
- Which of the Well-Architected pillars do you think is most often overlooked, and why?

---

## 🎯 Teaching Notes
- Use **whiteboard sketches** for VPCs, scaling, and architecture diagrams.
- Sprinkle in **CLI vs Console comparisons** to plant seeds for automation.
- Encourage **student reflection** after each section using the questions above.
