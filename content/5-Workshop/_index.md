---
title: "Workshop"
date: 2026-05-03
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Building a Serverless Web Application on AWS (Wild Rydes)

#### Overview

**AWS Serverless Computing** allows you to build and run applications and services without the need to manage servers. While your applications still run on servers, all server management is handled by AWS.

In this workshop, we will learn how to build a complete Serverless web application from scratch called **Wild Rydes** (a unicorn ride-sharing app). This application will allow users to register accounts, log in, and request rides.

We will utilize core AWS services to complete each component of the application:
+ **Web Hosting** - Use **AWS Amplify** to host static web resources (HTML, CSS, JavaScript) for the user interface.
+ **User Management** - Use **Amazon Cognito** to create a User Pool to manage user registration, authentication, and authorization.
+ **Serverless Backend** - Use **Amazon DynamoDB** to create a database table for storing ride requests and **AWS Lambda** to execute computing code whenever a new request is made.
+ **RESTful API** - Use **Amazon API Gateway** to securely route HTTP requests from the web frontend to the backend Lambda functions.

#### Content

1. [Application Architecture Overview](5.1-Architecture-overview/)
2. [Static Web Hosting](5.2-Static-web-hosting/)
3. [User Management](5.3-User-management/)
4. [Build a Serverless Backend](5.4-Serverless-backend/)
5. [Deploy the Backend API](5.5-Restful-api/)
6. [Build the Frontend](5.6-Build-Frontend/)
7. [Clean up Resources](5.7-Cleanup/)