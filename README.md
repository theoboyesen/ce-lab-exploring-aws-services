# Lab: Exploring AWS Services

## Overview

In this lab, you'll explore the AWS Management Console, learn to navigate services efficiently, and practice using the AWS CLI. You'll research pricing, find documentation, and become comfortable with the AWS ecosystem.

**Estimated Time:** 45-60 minutes

## Learning Objectives

By the end of this lab, you will be able to:
- Navigate the AWS Management Console effectively
- Identify and categorize AWS services
- Use the AWS CLI to retrieve account information
- Find service documentation and pricing
- Understand AWS regions and availability zones

## Prerequisites

- AWS account with configured access
- AWS CLI installed and configured
- Completed "AWS Account Setup" lesson

---

## Exercise 1: Console Navigation Mastery

### Part A: Service Discovery

**Find and document the following services:**

1. Navigate to **EC2** (Compute category)
   - Note: What is EC2 used for?
   - Screenshot the EC2 Dashboard

2. Navigate to **S3** (Storage category)
   - Note: What is S3 used for?
   - Screenshot the S3 Dashboard

3. Navigate to **RDS** (Database category)
   - Note: What is RDS used for?
   - Screenshot the RDS Dashboard

4. Navigate to **VPC** (Networking category)
   - Note: What is VPC used for?
   - Screenshot the VPC Dashboard

5. Navigate to **IAM** (Security category)
   - Note: What is IAM used for?
   - Screenshot the IAM Dashboard

### Part B: Console Features

**Complete the following tasks:**

1. **Use the Search Bar**
   - Search for "Lambda"
   - Document: Which category does Lambda belong to?

2. **Pin a Favorite Service**
   - Pin S3 to your favorites
   - Screenshot showing S3 pinned

3. **Check Recently Visited**
   - Navigate to 3 different services
   - Screenshot showing "Recently visited" section

4. **Change Regions**
   - Note your current region
   - Change to a different region (e.g., us-west-2)
   - Screenshot showing region selector
   - Change back to your original region

### Deliverables:
- Screenshots for all requested items in `screenshots/console-navigation/`
- Notes in `SOLUTION.md` about each service's purpose

---

## Exercise 2: Service Categorization

### Task: Complete the Service Matrix

For each category, identify 3-5 services and their use cases:

| Category | Services | Primary Use Case |
|----------|----------|------------------|
| Compute | EC2, Lambda, Elastic Beanstalk | Running applications |
| Storage | S3, EBS, EFS | Storing data |
| Database | RDS, DynamoDB, ElastiCache | Managing data |
| Networking | VPC, CloudFront, Route 53 | Connecting resources |
| Security | IAM, KMS, CloudTrail | Securing resources |
| Management | CloudWatch, CloudFormation, Systems Manager | Monitoring & automation |

### Research Questions:

1. **What's the difference between EC2 and Lambda?**
2. **When would you use S3 vs EBS?**
3. **What's the difference between RDS and DynamoDB?**
4. **Why do you need a VPC?**
5. **What does CloudWatch monitor?**

Document your answers in `SOLUTION.md`.

---

## Exercise 3: AWS CLI Basics

### Part A: Verify CLI Installation

```bash
# Check AWS CLI version
aws --version

# Check current configuration
aws configure list
```

**Document output in `SOLUTION.md`**

### Part B: Account Information Commands

Run the following commands and save outputs:

```bash
# 1. Get your caller identity
aws sts get-caller-identity

# 2. List all available regions
aws ec2 describe-regions --output table

# 3. Get your default region
aws configure get region

# 4. List S3 buckets (might be empty)
aws s3 ls
```

### Part C: Service Exploration

```bash
# List EC2 instance types available in your region
aws ec2 describe-instance-types --query 'InstanceTypes[?contains(InstanceType, `t2`) || contains(InstanceType, `t3`)].InstanceType' --output table

# Get information about your account
aws iam get-account-summary
```

### Deliverables:
- Save all command outputs to `cli-outputs.txt`
- Answer reflection questions in `SOLUTION.md`

---

## Exercise 4: Pricing Research

### Task: Research and document pricing for the following:

**1. EC2 t3.micro instance:**
- Region: us-east-1 (N. Virginia)
- Operating System: Linux
- Running 24/7 for one month (730 hours)
- On-Demand pricing: $_____ per hour
- Monthly cost: $_____
- Free Tier eligible? Yes / No

**2. S3 Standard Storage:**
- Region: us-east-1
- 100 GB of data stored
- Monthly cost: $_____
- Free Tier: First ___ GB free

**3. RDS db.t3.micro instance:**
- Region: us-east-1
- Engine: MySQL
- 20 GB storage
- Running 24/7
- Monthly cost: $_____
- Free Tier eligible? Yes / No

**4. Data Transfer:**
- Transferring 100 GB OUT of AWS
- Cost: $_____

### Resources to Use:
- AWS Pricing Calculator: https://calculator.aws/
- Individual service pricing pages
- AWS Free Tier page

### Deliverables:
- Complete pricing worksheet in `SOLUTION.md`
- Screenshot of AWS Pricing Calculator estimate: `screenshots/pricing-calculator.png`

---

## Exercise 5: Documentation Hunt

### Find and document the following:

**1. EC2 Instance Types:**
- URL to EC2 instance types documentation: ____________
- How many vCPUs does t3.medium have? ______
- How much memory does t3.medium have? ______

**2. S3 Storage Classes:**
- URL to S3 storage classes documentation: ____________
- List all S3 storage classes: ____________
- Which is cheapest for archive storage? ____________

**3. IAM Best Practices:**
- URL to IAM best practices: ____________
- List 3 IAM best practices: ____________

**4. Free Tier Limits:**
- URL to Free Tier page: ____________
- How many hours of EC2 t2.micro per month? ______
- How much S3 storage is free? ______

### Deliverables:
- Complete documentation worksheet in `SOLUTION.md`
- Bookmarks/links saved

---

## Exercise 6: Regions and Availability Zones

### Research and Document:

**1. Your Current Region:**
- Region Name: ____________
- Region Code: ____________
- Number of Availability Zones: ______

**2. Find Answers:**
- What is the difference between a Region and an Availability Zone?
- Why does AWS have multiple regions?
- How many Availability Zones does each region typically have?
- Can you deploy resources in multiple regions simultaneously?

**3. Region Selection Criteria:**

For each scenario, choose the best region and explain why:

| Scenario | Best Region | Reasoning |
|----------|-------------|-----------|
| Serving users primarily in Europe | | |
| Lowest cost for non-critical workloads | | |
| GDPR compliance required | | |
| Serving users in Asia-Pacific | | |
| Need newest AWS services | | |

### Deliverables:
- Complete region analysis in `SOLUTION.md`

---

## Bonus Challenges

### Challenge 1: Create a Cost Estimate
Use AWS Pricing Calculator to estimate monthly cost for:
- 1x t3.medium EC2 instance (24/7)
- 1x db.t3.micro RDS instance (24/7)
- 50 GB S3 storage
- 100 GB data transfer out

**Save estimate and include link in `SOLUTION.md`**

---

### Challenge 2: Service Comparison
Research and compare AWS services to their Azure and GCP equivalents:

| AWS | Azure | GCP |
|-----|-------|-----|
| EC2 | | |
| S3 | | |
| RDS | | |
| Lambda | | |

---

### Challenge 3: CLI Advanced Commands
Run and document output:

```bash
# List all EC2 instance types sorted by memory
aws ec2 describe-instance-types --query 'sort_by(InstanceTypes, &MemoryInfo.SizeInMiB)[*].[InstanceType,MemoryInfo.SizeInMiB]' --output table

# Get AWS service quotas for EC2
aws service-quotas list-service-quotas --service-code ec2 --query 'Quotas[?contains(QuotaName, `Running On-Demand`)]'
```

---

## Submission

### Required Deliverables:

1. **Screenshots folder** with:
   - Console navigation screenshots
   - Service dashboards
   - Region selector
   - Pricing calculator

2. **SOLUTION.md** with:
   - Service matrix completed
   - All research questions answered
   - Pricing research completed
   - Documentation URLs
   - Region analysis

3. **cli-outputs.txt** with all CLI command outputs

### How to Submit:

```bash
git add .
git commit -m "Complete exploring AWS services lab"
git push origin main
```

Create Pull Request and submit URL to Student Portal.

---

## Success Criteria

- ✅ Navigated all major AWS service categories
- ✅ Identified 3-5 services per category
- ✅ AWS CLI commands executed successfully
- ✅ Pricing research completed for all services
- ✅ Documentation URLs found and documented
- ✅ Region and AZ concepts understood
- ✅ All screenshots captured
- ✅ All questions answered
- ✅ Work committed and PR created

---

## Troubleshooting

**CLI not working?**
- Run: `aws configure`
- Ensure access keys are entered
- Check IAM user has necessary permissions

**Can't find a service?**
- Use search bar
- Check region (some services region-specific)

**Pricing seems different?**
- Verify region (us-east-1 usually cheapest)
- Check Free Tier eligibility

---

**Happy exploring! 🚀**
