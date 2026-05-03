---
title: "Week 6 Worklog"
date: 2026-04-13
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Review and master fundamental Database Concepts in a cloud computing environment.
* Understand the architecture, features, and practical applications of Amazon RDS, Amazon Aurora, Amazon Redshift, and Amazon ElastiCache.
* Practice deploying, connecting to, and managing a relational database management system on Amazon RDS.
* Master the workflow and utilize tools for safe Schema Conversion and Database Migration to AWS.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Review Database Concepts (Relational, NoSQL, In-memory) <br> - Read documentation on Amazon RDS: Supported DB Engines, Multi-AZ deployments, and Read Replicas | 04/13/2026 | 04/13/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Research the high-performance architecture of Amazon Aurora <br> - Explore Data Warehouse solutions with Amazon Redshift and In-memory caching with Amazon ElastiCache (Redis/Memcached) | 04/14/2026 | 04/14/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Amazon RDS Practice:** <br>&emsp; + Launch an RDS Database instance (MySQL or PostgreSQL) in a Private Subnet <br>&emsp; + Configure Security Groups to allow EC2 to connect to the Database <br>&emsp; + Use a DB Client (DBeaver, MySQL Workbench) or CLI to connect and query | 04/15/2026 | 04/15/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Read documentation and research AWS data migration tools: <br>&emsp; + AWS Schema Conversion Tool (SCT) <br>&emsp; + AWS Database Migration Service (DMS) | 04/16/2026 | 04/16/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Migration Practice:** <br>&emsp; + Use AWS SCT to analyze and convert schemas from the source DB to the target DB <br>&emsp; + Configure AWS DMS to create Endpoints and Tasks for migrating data to Amazon RDS | 04/17/2026 | 04/17/2026 | |

### Week 6 Achievements:

* Clearly differentiated AWS database services and learned how to select the right service (RDS, Aurora, Redshift, ElastiCache) for specific use cases.
* Successfully provisioned, configured, and secured an Amazon RDS instance, ensuring the database resides in a private network partition while communicating with the Application server.
* Learned the methodology for assessing compatibility between heterogeneous Database Engines using AWS SCT.
* Successfully implemented a complete schema conversion and database migration process using AWS DMS without data loss.