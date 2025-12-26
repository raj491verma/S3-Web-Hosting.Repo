# AWS Portfolio Hosting Project

## Project Overview
This project demonstrates hosting a static portfolio website using Amazon S3, while maintaining source files on Amazon EFS mounted to an EC2 Linux instance.

## Architecture
- S3: Static website hosting
- EC2 (Amazon Linux): Admin & sync server
- EFS: Centralized file storage
- IAM: Permissions management

## Workflow
1. Portfolio files are stored in EFS
2. EFS is mounted on EC2
3. EC2 syncs files from EFS to S3 using AWS CLI
4. S3 serves the website publicly

## Key Commands Used
```bash
aws s3 sync /efs/portfolio s3://your-bucket-raja-portfolio.site

## Bucket policy
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::raja-portfolio-site/*"
    }
  ]
}

## AWS Services Used

Amazon S3

Amazon EC2

Amazon EFS

IAM

## Outcome

Highly available static website

Centralized storage using EFS

Scalable and cost-effective hosting

## Author

Raja Verma

