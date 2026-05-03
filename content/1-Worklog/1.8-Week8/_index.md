---
title: "Week 8 Worklog"
date: 2026-04-27
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Finalize the architecture and deploy the "Building a Serverless Web Application on AWS" project.
* Successfully integrate Generative AI capabilities into a production-ready application.
* Perform comprehensive testing and package the deployment documentation.

### Tasks for the week:
| Day | Task                                                                                                                                                                                        | Start Date   | End Date        | Resources                                 |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| Mon | - Set up Frontend environment with AWS Amplify <br> - Connect GitHub repository and configure automated CI/CD                                                                               | 04/27/2026   | 04/27/2026      | [AWS Workshop](https://docs.aws.amazon.com) |
| Tue | - Configure user authentication via Amazon Cognito <br> - Set up Model Access for Claude 3 Sonnet on Amazon Bedrock                                                                         | 04/28/2026   | 04/28/2026      | [AWS Workshop](https://docs.aws.amazon.com) |
| Wed | - Build Serverless Backend with AWS Lambda <br> - Design Amazon DynamoDB tables for data storage <br> - Deploy GraphQL API via AWS AppSync                                                  | 04/29/2026   | 04/29/2026      | [AWS Workshop](https://docs.aws.amazon.com) |
| Thu | - Generative AI Integration: Write Lambda logic to invoke Amazon Bedrock <br> - Process input data and format responses from the Large Language Model (LLM)                                 | 04/30/2026   | 04/30/2026      | [AWS Workshop](https://docs.aws.amazon.com) |
| Fri | - **Testing & Optimization:** <br>&emsp; + Verify data flow from UI to AI Backend <br>&emsp; + Optimize performance and costs <br>&emsp; + Clean up redundant resources after completion    | 05/01/2026   | 05/01/2026      | [AWS Workshop](https://docs.aws.amazon.com) |

### Week 8 Outcomes:

* Successfully deployed a complete Web application based on the Serverless model.
* Mastered the CI/CD workflow on AWS Amplify to automate source code updates from GitHub.
* Effectively integrated Amazon Bedrock to generate intelligent content (recipes) from user input.
* Gained a deep understanding of the coordination between AppSync (GraphQL), Lambda, and DynamoDB in a real-world system.
* Ensured application security by implementing IAM Least Privilege for Lambda functions accessing Bedrock.