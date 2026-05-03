---
title : "Architecture Overview"
date : 2026-05-03
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Wild Rydes Application Overview

In this tutorial, you will build a simple serverless web application that allows users to request "unicorn" rides (essentially a ride-sharing service like Uber or Grab) from the **Wild Rydes** fleet.

The application will provide a front-end interface based on HTML and JavaScript, allowing users to select a pickup location. On the backend, it will communicate with a RESTful web service to submit requests and dispatch a nearby unicorn to the user's location. The application will also include complete registration and login functionality for users to access the service.

#### Application Architecture

The architecture of this application leverages various AWS managed services to eliminate the need for server management. These include **AWS Lambda**, **Amazon API Gateway**, **Amazon DynamoDB**, **Amazon Cognito**, and **AWS Amplify**.

![Architecture Diagram](/images/5-Workshop/5.1-Architecture-overview/diagram1.png)

#### Core Components

+ **Static Web Hosting:** **AWS Amplify** provides continuous deployment (CI/CD) and hosts static resources such as HTML, CSS, JavaScript, and image files. These resources are loaded by the user's browser to display the interface.
+ **User Management:** **Amazon Cognito** provides authentication, registration, and user management functions to secure the backend API. Only authenticated users are authorized to request rides.
+ **Serverless Backend:** **AWS Lambda** handles the core business logic, and **Amazon DynamoDB** serves as a persistent data storage layer where ride requests are recorded.
+ **RESTful API:** JavaScript executed in the browser interacts with the backend via **Amazon API Gateway**. It acts as the entry point for HTTP requests and triggers the corresponding Lambda functions.

#### Workshop Information

| Feature | Details |
| :--- | :--- |
| **AWS Experience** | Beginner |
| **Time to Complete** | Approximately 2 hours |
| **Estimated Cost** | Free (within AWS Free Tier) or less than $0.25 USD |
| **Recommended Browser** | Google Chrome (latest version) |

#### Implementation Modules

This workshop is divided into 5 main modules. Each module will guide you step-by-step through the implementation and verification of each architectural component:

1. **Static Web Hosting (15 min):** Configure AWS Amplify to host the web interface with built-in continuous deployment.
2. **User Management (30 min):** Create an Amazon Cognito User Pool to manage customer accounts.
3. **Serverless Backend (30 min):** Build a Lambda function and a DynamoDB table to process ride requests.
4. **RESTful API (15 min):** Use Amazon API Gateway to expose your Lambda function as a RESTful API.
5. **Resource Cleanup (10 min):** Terminate all resources created during the tutorial to avoid unwanted charges.

---
**Note:** If your AWS account was created within the last 24 hours, you may need to wait a short period for the system to fully activate access to the resources required for this lab.