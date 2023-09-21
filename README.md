# go-serverless-yt

## Overview

`go-serverless-yt` is a serverless backend project written in Golang. It leverages AWS Lambda, DynamoDB, and API Gateway to provide RESTful APIs for managing user data.

## Project Structure

The project consists of several key components:

- **main.go**: The entry point of the application, responsible for setting up the AWS session, handling Lambda function execution, and defining the main request handler based on HTTP methods.

- **api_response.go**: Contains a utility function for constructing API Gateway responses with proper headers and status codes.

- **handlers.go**: Implements functions for handling different HTTP methods (GET, POST, PUT, DELETE) for user data. These functions interact with DynamoDB to perform CRUD operations on user records.

- **user.go**: Defines the User struct and functions for fetching, creating, updating, and deleting user records. It also includes error messages used throughout the application.

- **is_email_valid.go**: Provides a simple email validation utility function to check the validity of email addresses.

## How to Build and Deploy

Follow these steps to build and deploy the project:

1. Run `go mod tidy` to tidy up the Go modules.

2. Set environment variables for the target platform:

   ```bash
   $env:GOOS = "linux"
   $env:GOARCH = "amd64"
   $env:CGO_ENABLED = "0"
   ```

3. Build the Go binary:

   ```bash
   go build -o main.go
   ```

4. Create a deployment package (ZIP file) for AWS Lambda:

   ```bash
   ~\Go\Bin\build-lambda-zip.exe -o main.zip main
   ```

5. Deploy the project on AWS using the following services:

- AWS Lambda: Create a Lambda function and upload the ZIP file as the deployment package. Set the appropriate environment variables, such as `AWS_REGION`, and configure the Lambda function handler to `main`.

- DynamoDB: Create a DynamoDB table with the name `go-serverless-yt` to store user data.

- API Gateway: Configure an API Gateway to trigger the Lambda function. Set up the necessary API routes and methods to correspond with your HTTP endpoints.

## Testing

You can test the APIs using tools like Postman by making HTTP requests to the API Gateway endpoints created during deployment.

## AWS Services Used

This project makes use of the following AWS services:

1. AWS Lambda: For serverless function execution.

2. DynamoDB: As the NoSQL database for storing user data.

3. API Gateway: To create HTTP APIs for accessing Lambda functions.

Feel free to explore and extend this project for your serverless backend needs.
