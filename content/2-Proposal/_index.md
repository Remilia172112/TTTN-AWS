---
title: "Proposal"
date: 2026-05-03
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Healthcare Data Lake & Analytics Platform
## Secure AWS Data Lake System Supporting Healthcare Data Analysis and Assessment (ICU)

### 1. Executive Summary
The **Healthcare Data Lake** project is designed to build a centralized, secure, and high-performance medical data infrastructure on the AWS platform. This system addresses the challenges of collecting, migrating, and cleansing large volumes of clinical patient data. The core objective is to create a standardized Data Pipeline to serve visual monitoring (Dashboards) and provide clean datasets for Deep Learning models assessing patient survival rates in the Intensive Care Unit (ICU).

### 2. Problem Statement & Proposed Solution
*Current Problem:*
Medical data (vital signs, medical history, test results) is often scattered across legacy on-premise relational database systems, with inconsistent data structures and poor scalability. Retrieving this massive volume of data to train machine learning models faces many computational performance limitations and potential risks of leaking sensitive information.

*Proposed Solution:*
The platform utilizes the AWS ecosystem with a strong focus on security and big data:
- **Data Migration:** Use AWS Database Migration Service (DMS) and Schema Conversion Tool (SCT) to migrate legacy databases to Amazon RDS.
- **Core Storage (Data Lake):** Ingest all raw data into Amazon S3. Use AWS KMS to encrypt data at rest to meet healthcare security standards.
- **Processing & Analytics:** Use AWS Glue for data cleansing (ETL) and Amazon Athena for direct SQL querying.
- **Visualization:** Use Amazon QuickSight to build dashboards monitoring vital signs and risk rates of ICU patients.

*Value Delivered (ROI):*
The solution completely modernizes the healthcare data architecture. After passing through AWS Glue, the data will be cleansed and noise will be removed, creating a solid foundation to feed directly into future Deep Learning models. Costs are optimized using a Serverless architecture (pay-per-query).

### 3. Solution Architecture
The platform applies a Data Lake architecture combined with multi-layered security controls.

![Healthcare Data Lake Architecture](/images/2-Proposal/healthcare_datalake_architecture.png)

*List of Applied AWS Services:*
- **Amazon VPC & Security Groups:** Establish a virtual private network to completely isolate the database from the public internet.
- **Amazon RDS (PostgreSQL/MySQL):** Store structured medical record data after migration.
- **Amazon S3:** Tiered Data Lake storage (Raw zone, Cleansed zone, Curated zone).
- **AWS KMS & IAM:** Manage medical data encryption keys and enforce strict Permission Boundaries.
- **AWS Glue (Crawlers & ETL jobs):** Data indexing and automatic cleansing of erroneous records.
- **Amazon Athena:** Serverless data querying.
- **Amazon QuickSight:** Build Dashboards for doctors/researchers.

### 4. Technical Implementation
*Implementation Phases:*
1. **Network & Security Infrastructure Setup:** Provision VPC, Public/Private Subnets. Create IAM Roles with Least Privilege and enable AWS Security Hub.
2. **Migration & Storage:** Create Amazon RDS. Simulate legacy medical data and use AWS DMS to push data to S3 (Raw Zone).
3. **Build Analytics Pipeline:** Write AWS Glue scripts (Python) to convert raw data into optimized Parquet format, stored in S3 (Curated Zone). Set up Athena for querying.
4. **Data Visualization:** Configure Amazon QuickSight to connect with Athena, design charts correlating vital signs (blood pressure, heart rate) and patient status.

### 5. Roadmap & Milestones
- **Weeks 1-2:** Complete VPC, security (KMS, IAM), and set up the database environment (RDS).
- **Weeks 3-4:** Configure AWS DMS for data synchronization. Establish the Amazon S3 Data Lake structure.
- **Weeks 5-6:** Deploy AWS Glue ETL jobs, run Crawlers to identify Schemas, and test SQL queries using Athena.
- **Weeks 7-8:** Integrate QuickSight, build the complete Dashboard, optimize costs, and write the final summary report.

### 6. Budget Estimation

*Summary of Cloud Infrastructure Costs (Monthly):*
- **Amazon RDS (t2.micro - Multi-AZ):** ~$15.00 USD (Free if within Free Tier).
- **Amazon S3 (Standard):** ~$0.25 USD (Storing about 10 GB of text/JSON/CSV medical data).
- **AWS KMS:** ~$1.00 USD (For 1 Custom Key managing data encryption).
- **AWS Glue & Athena:** ~$2.00 USD (Depending on ETL runtime and amount of data scanned).
- **Amazon QuickSight:** ~$9.00 USD (Author account).
**=> Total AWS Cost:** Approximately **$27.25 USD/month**. *(Note: Most of this can leverage the AWS Free Tier during the internship).*

### 7. Risk Assessment
*Risk Matrix & Mitigation Strategies:*
- **Sensitive Data Leakage:** Very High Impact. *Mitigation:* Mandate encryption for all S3 Buckets using AWS KMS, disable Public Access, and manage via IAM Roles.
- **Data Loss during Migration:** High Impact. *Mitigation:* Enable Validation on AWS DMS and use AWS Backup to create periodic Snapshots for RDS.
- **Spike in Athena Query Costs:** Medium Probability. *Mitigation:* AWS Glue converts data into Parquet format (compressed columnar format) and applies Partitioning to minimize the amount of data scanned per query.

### 8. Expected Outcomes
The project is not merely a practical Cloud infrastructure exercise but also brings immense value to the Digital Healthcare sector. Possessing a systematically planned Data Lake on AWS eliminates "Data Silos," enables rapid information extraction, and provides a high-quality dataset to deploy the most advanced medical predictive Deep Learning algorithms.