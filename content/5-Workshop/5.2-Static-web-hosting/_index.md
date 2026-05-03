---
title: "Deploying Application with AWS Amplify"
date: 2026-05-03
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

AWS Amplify provides a Git-based CI/CD workflow for building, deploying, and hosting single-page web applications or static sites with a backend. When connected to a Git repository, Amplify automatically identifies the build settings for both the frontend framework and configured backend resources, then automatically deploys updates after every code commit.

In this practice, you will start by creating a new React application and pushing the source code to a GitHub repository. Then, you will connect this repository to the AWS Amplify web hosting service and deploy the application to a globally available Content Delivery Network (CDN), hosted on the `amplifyapp.com` domain.

### What you will accomplish
In this tutorial, you will:
* Create a new web application.
* Set up Amplify for your project.

### Deployment

#### Step 1: Create a new React application

#### Create the application
Open a new terminal or command line window and run the following command to use Vite to create a React application:
```bash
npm create vite@latest ai-recipe-generator -- --template react-ts -y
cd ai-recipe-generator
npm install
npm run dev
```
![img](/images/5-Workshop/5.2-Static-web-hosting/img1.png)

#### Open the application
In the terminal window, select and open the **Local** link to view the Vite + React application.

![img](/images/5-Workshop/5.2-Static-web-hosting/img2.png)

#### Step 2: Initialize the GitHub repository
In this step, you will create a GitHub repository and commit your source code to it. You will need a GitHub account to complete this step; if you do not have one, please sign up here.

**Note:**
If you have never used GitHub on your computer, follow the setup steps before continuing to allow a connection to your account.

#### Log in to GitHub
Log in to GitHub at [https://github.com/](https://github.com/).

![img](/images/5-Workshop/5.2-Static-web-hosting/img3.png)

#### Start a new repository
In the **Start a new repository** section, make the following selections:
- For **Repository name**, enter `ai-recipe-generator` and select the **Public** radio button.
- Then select **Create a new repository**.

![img](/images/5-Workshop/5.2-Static-web-hosting/img4.png)

#### Initialize Git
Open a new terminal window, navigate to the root directory of your project (`ai-recipe-generator`), and run the following commands to initialize git and push the application to the new GitHub repository:

**Note:**
Replace the GitHub SSH URL in the command with your own GitHub URL.
```bash
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:<your-username>/ai-recipe-generator.git
git branch -M main
git push -u origin main
```
![img](/images/5-Workshop/5.2-Static-web-hosting/img5.png)

#### Step 3: Install Amplify packages

#### Install Amplify
Open a new terminal window, navigate to the root directory of the application (`ai-recipe-generator`), and run the following command:
```bash
npm create amplify@latest -y
```
![img](/images/5-Workshop/5.2-Static-web-hosting/img6.png)

#### View directory
Running the previous command will create a lightweight Amplify project skeleton right inside your application directory.

![img](/images/5-Workshop/5.2-Static-web-hosting/img7.png)

#### Step 4: Deploy your application with AWS Amplify
Log in to the **AWS Management Console** in a new browser window, and open the AWS Amplify console at [https://console.aws.amazon.com/amplify/apps](https://console.aws.amazon.com/amplify/apps).

Select **Create new app**.

![img](/images/5-Workshop/5.2-Static-web-hosting/img8.png)

#### Choose GitHub to deploy the application
On the **Start building with Amplify** page, under the **Deploy your app** section, select **GitHub** and then select **Next**.

![img](/images/5-Workshop/5.2-Static-web-hosting/img9.png)

#### Authenticate with GitHub
When prompted, authenticate with GitHub. You will be automatically redirected back to the Amplify console.
Select the repository and the `main` branch you created earlier. Then select **Next**.

![img](/images/5-Workshop/5.2-Static-web-hosting/img10.png)

#### Select Next
Keep the default build settings and select **Next**.

![img](/images/5-Workshop/5.2-Static-web-hosting/img11.png)

#### Review configuration
Review the selected input information and select **Save and deploy**.

![img](/images/5-Workshop/5.2-Static-web-hosting/img12.png)

#### View your application
AWS Amplify will now build your source code and deploy the application at `https://...amplifyapp.com`. With every `git push`, your deployed version will be updated. It may take up to 5 minutes to deploy your application.

After the build process is complete, select the **Visit deployed URL** button to see your web application live.

![img](/images/5-Workshop/5.2-Static-web-hosting/img13.png)

## Conclusion
You have successfully deployed a React application to AWS by integrating with GitHub and using AWS Amplify. With AWS Amplify, you can continuously deploy your application on the Cloud and host it on a globally available CDN network.