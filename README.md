# AWS-REST-API
## Building a Serverless CRUD API with AWS: A Step-by-Step Guide

This guide walks you through building a serverless CRUD API using AWS DynamoDB, Lambda, and API Gateway.
![image](https://github.com/njange/AWS-REST-API/assets/128843179/4ad94735-a504-4f72-a20a-3a787ee65ca6)


# What You'll Build

A DynamoDB table to store employee data (ID, job title, name, salary).

A Lambda function to process API requests and interact with DynamoDB.

An API Gateway to expose endpoints for CRUD operations on employee data.

## Prerequisites

An AWS account (You can sign up for a free tier account).

Basic understanding of AWS services and concepts like Lambda, DynamoDB, and API Gateway

## Steps

## Setting Up DynamoDB Table

Sign in to the AWS Management Console and search for DynamoDB.

Click "Create Table" and name your table "employee_info".

Set "EmployeeID" as the Partition Key (primary key). Leave the Sort Key blank.

Click "Create table".

Creating a Lambda Function.

Go to the Lambda service in the console and click "Create function".

Choose "Author from scratch" and name your function "serverless_api_demo".

Select "Python 3.11" as the Runtime.

For "Execution role", choose "Create a new role with basic Lambda permissions".

Click "Create function".

## Configuring Lambda Permissions

In the function details page, navigate to "Configuration" -> "Permissions".

Click on the role name displayed.

Click "Attach policies" and search for "AmazonDynamoDBFullAccess" policy. Attach it.

Search for "CloudWatchLogsFullAccess" and attach it.

Click "Add permissions".

## Building the Lambda Function

In the function code editor, paste the code provided in the video tutorial. The code will handle different HTTP methods (GET, POST, PUT, DELETE) and interact with DynamoDB based on the path and request body.
![Screenshot at 2024-05-30 23-29-16](https://github.com/njange/AWS-REST-API/assets/128843179/e3ed1a5c-4488-4895-948e-39a7bb0d1202)

## Creating the API in API Gateway

Go to the API Gateway service and click "Create API".

Choose "Build" and then "REST API".

Name your API "serverless_api_demo" and leave the description blank.

Choose "Create API".

## Defining Resources and Methods

Create a resource named "status". Enable CORS for this resource.
![Screenshot at 2024-05-30 17-06-20](https://github.com/njange/AWS-REST-API/assets/128843179/2c8116df-1db8-446b-91f5-d3de3b3371c2)

Under the "status" resource, create a GET method and integrate it with your Lambda function "serverless_api_demo".

Create another resource named "employee" and enable CORS.

Under the "employee" resource, create GET, POST, PUT, and DELETE methods, each integrating with your Lambda function.
![Screenshot at 2024-05-30 18-47-29](https://github.com/njange/AWS-REST-API/assets/128843179/3480f85d-f6fb-40b1-8052-38938a9ed02a)

## Deploying the API

Click "Actions" -> "Deploy API" in the API Gateway console.

Choose a new stage name (e.g., "prod") and click "Deploy".

This will generate a URL for your API. Copy this URL for later use.
![Screenshot at 2024-05-30 18-51-35](https://github.com/njange/AWS-REST-API/assets/128843179/5563c800-62b1-498e-bfec-307683f35a9e)

## Testing the API

Use a tool like Postman to send requests to your API endpoints.

Send a GET request to the "/status" endpoint to verify the API is running.

Send a POST request to the "/employee" endpoint with employee data in the JSON body to create a new employee.

Send a GET request to the "/employee/{id}" endpoint to retrieve employee details by ID.

Send a PUT request to the "/employee/{id}" endpoint with updated employee data to modify an existing employee.

Send a DELETE request to the "/employee/{id}" endpoint to delete an employee.

![Screenshot at 2024-05-31 23-01-11](https://github.com/njange/AWS-REST-API/assets/128843179/ea6d2fb8-07d9-4cbb-9bb3-73909ae341e0)

## Verifying Data in DynamoDB

Go back to the DynamoDB console and navigate to your "employee_info" table.

You should see the newly created employee entries with their corresponding data.

## Conclusion

By following these steps, you've successfully built a serverless CRUD API on AWS using Lambda, DynamoDB, and API Gateway. Refer to the video tutorial (link to be provided) for a more detailed explanation and troubleshooting tips.

## Additional Notes


Consider implementing error handling and validation logic in your Lambda function
