---
title : "User Management"
date : 2025-05-03
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

## Overview

After having a React web application, you will configure an authentication resource for the app using AWS Amplify Auth, which is powered by Amazon Cognito. Cognito is a powerful user management service that supports user registration, authentication, account recovery, and more.

You will also use the AWS Management Console to enable access to Amazon Bedrock and the Claude 3 Sonnet model, allowing the application to generate recipes using AI.

---

## Objectives

In this tutorial, you will:

- Set up Amplify Authentication  
- Configure access to Claude 3 Sonnet from Anthropic  

---

## Implementation

### Step 1: Set up Amplify Auth

The application uses email as the default login method. When users sign up, they will receive a verification email. In this step, you will customize the verification email content.

#### Modify the resource file

On your local machine, navigate to: `ai-recipe-generator/amplify/auth/resource.ts`, update the file as required, and save it.
```
import { defineAuth } from "@aws-amplify/backend";

export const auth = defineAuth({
  loginWith: {
    email: {
      verificationEmailStyle: "CODE",
      verificationEmailSubject: "Welcome to the AI-Powered Recipe Generator!",
      verificationEmailBody: (createCode) =>
        `Use this code to confirm your account: ${createCode()}`,
    },
  },
});
```

![img 1](/images/5-Workshop/5.3-User-management/img1.png)

#### View the customized email

The image below shows an example of the customized verification email:

![img 2](/images/5-Workshop/5.3-User-management/img2.png)

---

### Step 2: Set up Amazon Bedrock access

Amazon Bedrock allows you to request access to various generative AI models. In this tutorial, you will need access to Claude 3 Sonnet from Anthropic.

#### Open the Bedrock Console

Sign in to the AWS Management Console and navigate to:

https://console.aws.amazon.com/bedrock/

- Make sure you are in the **N. Virginia (us-east-1)** region  
- Click **Get started**

![img 3](/images/5-Workshop/5.3-User-management/img3.png)

#### Select the Claude model

In the **Foundation models** section, select Claude.

![img 4](/images/5-Workshop/5.3-User-management/img4.png)

#### Request access to Claude 3 Sonnet

- Scroll down to the Claude models section  
- Select the **Claude 3 Sonnet** tab  
- Click **Request model access**

> If you already have access, the button will display **Manage model access**

![img 5](/images/5-Workshop/5.3-User-management/img5.png)

#### Request model access

In the **Base models** section:

- Choose **Available to request** for Claude 3 Sonnet  
- Click **Request model access**

![img 6](/images/5-Workshop/5.3-User-management/img6.png)

#### Click Next

On the **Edit model access** screen, click **Next**

![img 7](/images/5-Workshop/5.3-User-management/img7.png)

#### Submit request

On the **Review and Submit** page, click **Submit**

![img 8](/images/5-Workshop/5.3-User-management/img8.png)

---

## Conclusion

You have:

- Configured Amplify Authentication  
- Customized the verification email  
- Enabled access to Amazon Bedrock  
- Activated the Claude 3 Sonnet model  

Your application is now ready to use AI for content generation.