# AWS Portfolio Hosting Architecture

## Architecture Overview
This project demonstrates hosting a static portfolio website using Amazon S3, while maintaining centralized storage using Amazon EFS mounted on an EC2 Linux instance.

S3 is used for scalable static website hosting, while EC2 and EFS are used for file management and synchronization.

---

## High-Level Architecture Diagram (Logical View)

User
  |
  |  HTTP Request
  v
Amazon S3 (Static Website Hosting)
  |
  | 
  v
Amazon EC2 (Amazon Linux)
  |
  |  NFS Mount
  v
Amazon EFS (Centralized Storage)

---

## Architecture Components

### 1. Amazon S3
- Hosts the static portfolio website
- Public read access enabled
- Static website hosting enabled
- Highly available and scalable

### 2. Amazon EC2 (Amazon Linux)
- Acts as an admin and automation server
- Mounted with Amazon EFS


### 3. Amazon EFS
- Centralized shared storage
- Mounted on EC2 using NFS (port 2049)
- Stores portfolio source files

### 4. IAM
- EC2 IAM role with permissions:
  - AmazonS3FullAccess
  - AmazonElasticFileSystemClientReadWriteAccess

---

## Data Flow

1. Portfolio files are created or updated in EFS
2. EFS is mounted on the EC2 instance
3. EC2 syncs files from EFS to S3 using AWS CLI
4. End users access the website via the S3 static website endpoint

---

## Sync Command Used

```bash
aws s3 sync /efs/portfolio s3://<>
