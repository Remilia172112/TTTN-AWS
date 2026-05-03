---
title : "Building a Serverless Backend"
date : 2025-05-03
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

## Overview

In this section, you will configure a serverless function using AWS Amplify and AWS Lambda. This function takes input parameters (ingredients) to generate a prompt. It then sends this prompt to Amazon Bedrock via an HTTP POST request to the Claude 3 Sonnet model.

The request body includes the prompt string inside a `messages` array.

---

## Objectives

In this tutorial, you will:

- Add Amazon Bedrock as a data source  
- Configure custom business logic  

---

## Implementation

### Step 1: Create a Lambda function to handle requests

#### Create the function file

On your local machine, navigate to: ai-recipe-generator/amplify/data and create a new file named: bedrock.js


![img 1](/images/5-Workshop/5.4-Serverless-backend/img1.png)

#### Add function code

Update the `bedrock.js` file with the provided code.

This code:
```
export function request(ctx) {
    const { ingredients = [] } = ctx.args;
  
    // Construct the prompt with the provided ingredients
    const prompt = `Suggest a recipe idea using these ingredients: ${ingredients.join(", ")}.`;
  
    // Return the request configuration
    return {
      resourcePath: `/model/anthropic.claude-3-sonnet-20240229-v1:0/invoke`,
      method: "POST",
      params: {
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          anthropic_version: "bedrock-2023-05-31",
          max_tokens: 1000,
          messages: [
            {
              role: "user",
              content: [
                {
                  type: "text",
                  text: `\n\nHuman: ${prompt}\n\nAssistant:`,
                },
              ],
            },
          ],
        }),
      },
    };
  }
  
  export function response(ctx) {
    // Parse the response body
    const parsedBody = JSON.parse(ctx.result.body);
    // Extract the text content from the response
    const res = {
      body: parsedBody.content[0].text,
    };
    // Return the response
    return res;
  }
```

- Defines a `request` function to construct an HTTP request to invoke the Claude 3 Sonnet model on Amazon Bedrock  
- Defines a `response` function to process the returned data and generate a recipe  

---

### Step 2: Add Amazon Bedrock as a data source

#### Update backend configuration

Open the file: amplify/backend.ts


Update it with the provided code and save the file.
```
import { defineBackend } from "@aws-amplify/backend";
import { data } from "./data/resource";
import { PolicyStatement } from "aws-cdk-lib/aws-iam";
import { auth } from "./auth/resource";

const backend = defineBackend({
  auth,
  data,
});

const bedrockDataSource = backend.data.resources.graphqlApi.addHttpDataSource(
  "bedrockDS",
  "https://bedrock-runtime.us-east-1.amazonaws.com",
  {
    authorizationConfig: {
      signingRegion: "us-east-1",
      signingServiceName: "bedrock",
    },
  }
);

bedrockDataSource.grantPrincipal.addToPrincipalPolicy(
  new PolicyStatement({
    resources: [
      "arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-3-sonnet-20240229-v1:0",
    ],
    actions: ["bedrock:InvokeModel"],
    
  })
);
```


![img 2](/images/5-Workshop/5.4-Serverless-backend/img2.png)

This configuration will:

- Add an HTTP data source for Amazon Bedrock  
- Grant permissions to invoke the Claude model  

---

## Conclusion

You have:

- Created a Lambda function using AWS Amplify  
- Implemented request/response handling logic  
- Integrated Amazon Bedrock as a data source  

Your serverless backend is now ready to process requests and interact with AI.

