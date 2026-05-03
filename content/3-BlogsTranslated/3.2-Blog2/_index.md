---
title: "Blog 2"
date: 2026-04-30
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS Security Best Practices: Applying the Principle of Least Privilege

Security is always "Job Zero" at AWS. When you start building applications on AWS, one of the most critical design decisions is how you manage identity and access through **AWS Identity and Access Management (IAM)**. 

In this blog post, I will share how modern cloud engineering teams design IAM policies to adhere to the principle of **Least Privilege** – meaning granting only the exact permissions needed to perform a task, nothing more, nothing less, to minimize security risks.

---

## The Problem with Overly Permissive IAM Policies

Many engineers new to AWS tend to use `AdministratorAccess` permissions or use the asterisk `*` (Wildcard) in IAM policies to avoid `AccessDenied` errors that hinder development progress. 

> *Granting `s3:*` permissions for an application environment might help the application run immediately, but it also means that the application has the permission to delete the entire bucket (`s3:DeleteBucket`) – a potential catastrophic risk.*

---

## 3 Levels of Access Control on AWS

To achieve a tightly secured environment, you need to combine multiple layers of protection:

| Protection Layer | Control Responsibility | AWS Tool Used |
| :--- | :--- | :--- |
| **Organization Level** | Establish maximum security boundaries for all sub-accounts (Accounts). | Service Control Policies (SCPs) |
| **Boundary Level** | Prevent an Admin from escalating privileges (Privilege Escalation). | IAM Permissions Boundaries |
| **Execution Level** | Grant specific permissions to a User or an AWS Service (like Lambda, EC2). | IAM Identity-based Policies |

---

## How to Build Least Privilege Policies

To write strict policies, you should use **IAM Access Analyzer**. This tool monitors the services your Role actually calls during operation, and automatically generates a minimal JSON file containing only the used permissions.

### Restrictive Policy Example

Instead of granting write access to the entire S3 bucket, you should limit the allowed actions to a specific bucket, and even to a specific folder within that bucket:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:PutObject",
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::my-company-data-lake/processed-data/*"
    }
  ]
}