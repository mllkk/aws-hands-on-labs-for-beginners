# 🚀 Lab 01: To The Power of Math – Serverless Web Application

This lab demonstrates a beginner-friendly serverless web application architecture within the AWS environment.
All source code and scripts used in this exercise can be found in the Codes folder.

## 📐 Architecture
<img width="1363" height="784" alt="Gemini_Generated_Image_t73efqt73efqt73e" src="https://github.com/user-attachments/assets/6d3af37a-f97c-4abe-8b49-8c6a90b9c7fa" />
Reference: Tiny Technical Tutorials. (2026, October 20). AWS Project: Architect and Build an End-to-End AWS Web Application from Scratch, Step by Step [Video]. YouTube. [https://www.youtube.com/watch?v=7m_q1ldzw0U&t=969s]

## 📋 Execution Steps

1. **Deploy Frontend:** Deploy a basic web application on **AWS Amplify**.
2. **Create Business Logic:** Create an **AWS Lambda** function to handle the business logic.
3. **Configure API:** Configure **API Gateway** to enable communication between Amplify and Lambda.
4. **Provision Database:** Create a **DynamoDB** table for persistent data storage.
5. **Configure IAM:** Grant write permissions (IAM policy) to the Lambda function for DynamoDB access.
6. **Update Web App:** Update the frontend code to send requests to the new API Gateway endpoint and re-deploy.

### 1. Deploy Frontend (AWS Amplify)
* Open the AWS Amplify Console and select **Create new app**.
* Select **Deploy without Git provider** and click **Next**.
<img width="385" height="69" alt="image" src="https://github.com/user-attachments/assets/6423039a-48bc-4d27-9e98-05f1f9489f36" />

* Configure App Details: **App name:** `PowerOfMath`,**Branch name:** `dev`
* Rename the `index-ORIGINAL.html` file (located in the `Codes` folder) to `index.html`.
* Compress `index.html` into a `.zip` archive. 
   > ⚠️ **Note:** Ensure the HTML file inside the zip archive is strictly named `index.html`; otherwise, Amplify will fail to detect the entry point and deploy the site.
* Choose the **Drag and Drop** method and upload your `.zip` file. Click **Save and deploy**.
* Once the deployment completes, access your live application via the link provided under the **Domain** section.
<img width="739" height="160" alt="image" src="https://github.com/user-attachments/assets/392f4d11-6f06-4c5f-aa6e-14c900e3bd77" />


You should see a simple web page like this:
<img width="945" height="202" alt="image" src="https://github.com/user-attachments/assets/cbbcd2b1-8979-472a-8381-8ab6b205da37" />
