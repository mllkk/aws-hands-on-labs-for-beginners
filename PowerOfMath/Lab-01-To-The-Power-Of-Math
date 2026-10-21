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

### 2. Create Business Logic (AWS Lambda)

* Open the AWS Lambda Console and click **Create function**.
* Configure Settings:
   * Select **Author from scratch**.
   * **Function name:** `PowerOfMathFunction`
   * **Runtime:** `Python 3.14` (or latest Python version available)
   * Click **Create function**.
* Copy the code from the `PowerOfMathFunction-Lambda-ORIGINAL.txt` file (located in the `Codes` folder) and paste it into the **Code source** editor.
   > 💡 **Note:** This Python function accepts two variables, `base` and `exponent`, and performs the mathematical calculation.
   * Click **Save** and then click **Deploy** to publish the changes.
     <img width="945" height="482" alt="image" src="https://github.com/user-attachments/assets/6ac88d7b-3ca2-4e0a-af59-f68fa1a1414c" />

* Test the Function:
   * Click **Test** button in the Lambda console.
   * **Invocation type:** Synchronous
   * **Event name:** `powerOfMathTest`
   * **Event sharing settings:** Private
   * Paste your JSON test payload (containing `base` and `exponent` values) into the **Event JSON** area.
  ```json
     {
       "base": 3,
       "exponent": 2
     }
     ```
* Click the orange **Test** button. Upon successful execution, you should see a `200` status code along with the calculated math result.
  <img width="945" height="374" alt="image" src="https://github.com/user-attachments/assets/1f46551b-01f0-4e99-a52b-06fdc497602b" />

  
### 3. Configure API Gateway

To enable communication between the Amplify frontend and the Lambda function, an API Gateway is required.
1. **Create REST API:**
   * Open the **API Gateway** console and click **Create API**.
   * Locate **REST API** and click **Build**.
   * Enter an **API name** (e.g., `PowerOfMathAPI`) and click **Create API**.

2. **Create POST Method:**
   * In the newly created empty API, click **Create method**.
   * **Method type:** `POST`
   * **Integration type:** Lambda Function
   * **Lambda function:** Select your Lambda function (or enter the ARN for `PowerOfMathFunction`).
   * Click **Create method**.

3. **Enable CORS:**
   > 💡 **Note:** Since AWS Amplify and API Gateway run on different domains, Cross-Origin Resource Sharing (CORS) must be enabled to allow the frontend application to send requests to the API.
   * Select your resource or method and click **Enable CORS**.
   * Under **Access-Control-Allow-Methods**, ensure **POST** is selected.
   * Save the CORS configuration.
   * Deploy API after this operation.
     <img width="945" height="299" alt="image" src="https://github.com/user-attachments/assets/18291f02-d008-4f91-a720-447f7d7213c8" />


4. **Test the API Endpoint:**
   * Navigate to **Resources** > **POST** and click the **Test** tab.
   * In the **Request Body**, paste the JSON test payload (containing `base` and `exponent`).
   * Click **Test**.
   * Verify that the execution returns a `200` status code along with the expected response body:
    ```json
     {
       "statusCode": 200,
       "body": "\"Your result is 9.0\""
     }
     ```
    <img width="945" height="389" alt="image" src="https://github.com/user-attachments/assets/37d46771-2c0b-469a-897f-d21a0b73c700" />

### 4. Provision Database and Configure Permissions

1. **Create DynamoDB Table:**
   * Open the **DynamoDB** console and click **Create table**.
   * **Table name:** `PoMDatabase`
   * **Partition key:** `ID` (Type: `String` or `Number` based on your implementation)
   * Click **Create table**.
   * Note down the **Table ARN**.  
     > 💡 *If needed, you can retrieve it anytime via: DynamoDB > Tables > PoMDatabase > General Information > Amazon Resource Name (ARN).*

2. **Configure IAM Permissions for Lambda:**
   > 💡 **Note:** To allow the web application to save calculation history, the Lambda function requires write access to the DynamoDB table.
   * Go to your Lambda function (`PowerOfMathFunction`).
   * Navigate to **Configuration** > **Permissions** and click the role link under **Role name**.
   * In the IAM Management Console, click **Add permissions** > **Create inline policy**.
   <img width="945" height="393" alt="image" src="https://github.com/user-attachments/assets/cb8f72f5-2248-46ab-b0b9-8362e8c30b21" />

   * Switch to the **JSON** tab and paste the policy content from `Execution Role Policy JSON.txt` (located in the `Codes` folder).
   * Ensure your DynamoDB Table ARN is correctly referenced within the policy JSON.
   * Click **Next**, enter a policy name (e.g., `PowerOfMathDynamoDBWritePolicy`), and click **Create policy**.
   <img width="945" height="308" alt="image" src="https://github.com/user-attachments/assets/1baa98ae-40fe-4df7-819a-8ba2aae229ac" />


3. **Update Lambda Function to Final Version:**
   * Return to the Lambda function editor.
   * Copy the code from `PowerOfMathFunction-Lambda-FINAL.txt` and paste it into the code area.
   * Verify that the table name in the code matches your DynamoDB table:
     ```python
     # Use the DynamoDB resource to select your table
     table = dynamodb.Table('PoMDatabase')
     ```
   * Click **Save** and then **Deploy**.

4. **Verify Database Insertion:**
   * Execute a test invocation using the previously configured `powerOfMathTest` payload.
   * Confirm that the test returns a `200` status code.
   * Navigate to the **DynamoDB** console, select **Explore items** from the left menu, and click on `PoMDatabase`.
   * Verify that a new record containing the calculation result has been successfully written to the table.
   <img width="945" height="239" alt="image" src="https://github.com/user-attachments/assets/0af6e1da-c97e-41aa-a844-fec0a2acf55f" />

### 5. Update the Web Application

In the first step, a basic static web page was deployed for testing. Now, the frontend application will be updated to collect user input (base and exponent) and send calculation requests to the backend via the API Gateway endpoint.

1. **Configure API Endpoint in Frontend Code:**
   * Open the `index-FINAL.html` file (located in the `Codes` folder).
   * Navigate to the **API Gateway** console, go to **Stages**, and copy the **Invoke URL**.
   * Replace the placeholder API URL in `index-FINAL.html` with your actual API Gateway Invoke URL.
   * Rename `index-FINAL.html` to `index.html` and compress it into a `.zip` archive.
   <img width="945" height="254" alt="image" src="https://github.com/user-attachments/assets/0334508a-b7ed-440e-9deb-d8ee443e75fd" />


2. **Deploy Updated Frontend:**
   * Open the **AWS Amplify** console and select your `PowerOfMath` application.
   * Click **Deploy updates** (or **Upload deployment**).
   * Drag and drop the updated `.zip` file containing `index.html`.
   * Click **Save and deploy**.

3. **Verify End-to-End Application:**
   * Access your application via the Amplify domain link.
   * Enter two numbers (base and exponent) and click the calculate button.
   * Confirm that the result is calculated via Lambda, displayed on the web interface, and stored in the DynamoDB table.
   <img width="945" height="313" alt="image" src="https://github.com/user-attachments/assets/5a60ee8d-f60e-4daa-9fa1-7bf7821a2441" />


🎉 **Congratulations! You have successfully built and deployed an end-to-end serverless web application on AWS!**

### 🧹 Resource Cleanup
<img width="945" height="348" alt="image" src="https://github.com/user-attachments/assets/bbcdca7d-9b36-4a02-a4a1-00795b21718f" />
<img width="945" height="152" alt="image" src="https://github.com/user-attachments/assets/79229b36-89d4-46cf-8402-d7bd15914e49" />
<img width="945" height="168" alt="image" src="https://github.com/user-attachments/assets/c04c775e-53f9-4b73-ba40-9eaa22d4e919" />
<img width="945" height="222" alt="image" src="https://github.com/user-attachments/assets/a2f2b047-cb24-44d0-aca5-ce0355554215" />





