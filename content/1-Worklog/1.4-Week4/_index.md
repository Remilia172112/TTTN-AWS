---
title: "Week 4 Worklog"
date: 2026-03-30
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Gain comprehensive knowledge of AWS's core Object Storage service, specifically Amazon S3.
* Understand access control methods, performance optimization, and data lifecycle management (S3 Glacier).
* Explore backup solutions (AWS Backup), hybrid storage (Storage Gateway), and large-scale data migration (Snow Family).
* Practice integrating services (EC2, S3, Lambda, SNS) to build a fully automated backup and alerting workflow.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Read and study documentation on Amazon S3 (Buckets, Objects) <br> - Learn about S3 Access Points, configuring Static Website hosting, and handling CORS (Cross-Origin Resource Sharing) | 03/30/2026 | 03/30/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Research Access Control in S3 (IAM Policies, Bucket Policies, ACLs) <br> - Read documentation on naming Object Keys to optimize Performance <br> - Learn about cold storage classes (S3 Glacier, Glacier Deep Archive) | 03/31/2026 | 03/31/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Explore physical data migration solutions: AWS Snow Family (Snowcone, Snowball, Snowmobile) <br> - Read documentation on AWS Storage Gateway (hybrid storage) and the overall AWS Backup architecture | 04/01/2026 | 04/01/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - **Service Initialization Practice:** <br>&emsp; + Create an EC2 instance and an S3 bucket <br>&emsp; + Set up an IAM Role allowing EC2 to read/write data to S3 <br>&emsp; + Create Topics and Subscriptions in Amazon SNS | 04/02/2026 | 04/02/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Automation Practice (Serverless Backup):** <br>&emsp; + Write an AWS Lambda function in Python/Node.js to automate data backup (from EC2 to S3 or creating EBS Snapshots) <br>&emsp; + Integrate the Lambda function with SNS | 04/03/2026 | 04/03/2026 | |

### Week 4 Achievements:

* Deeply understood Amazon S3's storage architecture and learned how to configure S3 as a static web server to host frontend applications.
* Mastered strict security authorization strategies on S3 and how to design Object Key prefixes to achieve maximum I/O performance.
* Distinguished between practical use cases: When to use Storage Gateway (connecting on-premises with cloud) and when to use the Snow Family (moving petabytes of physical data).
* Successfully configured an email/SMS notification flow using Amazon SNS.
* Successfully built a practical Serverless architecture: Utilized AWS Lambda to automatically trigger the backup process and send status notifications (success/failure) via SNS.