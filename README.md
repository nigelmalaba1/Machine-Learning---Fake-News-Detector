# Fake News Detection API

This repository contains a Fake News Detection API using Databricks AutoML, FastAPI, and AWS ECR. The API receives text as input and returns a prediction from the Databricks AutoML model that classifies the text as fake news or not.

# Requirements

* Python 3.9
* FastAPI
* Uvicorn
* Requests
* Docker
* AWS CLI

# Getting Started

1. Clone the repository

  `git clone https://github.com/yourusername/fake-news-detection-api.git`
  `cd fake-news-detection-api`

2. Install Python libraries

  `pip install fastapi uvicorn requests`

3. Update Databricks AutoML configuration

  Open main.py and replace the serving_endpoint_url and api_token variables with your actual Databricks AutoML serving endpoint URL and API token.

4. Run FastAPI server locally

  `uvicorn main:app --reload`

  The FastAPI server should now be running at http://127.0.0.1:8000. Visit http://127.0.0.1:8000/docs to see the API documentation and interact with the API.

# Deploying to AWS using Docker and Amazon ECR

1. Build Docker image

  `docker build -t my-fastapi-app .`

2. Run Docker container

  `docker run -p 4000:80 my-fastapi-app`

  Your FastAPI service should now be running at http://127.0.0.1:4000.

3. Push Docker image to Amazon ECR

3.1. Install and configure the AWS CLI

  `aws configure`
  
3.2. Create an ECR repository

  `aws ecr create-repository --repository-name my-fastapi-app`
  
3.3. Authenticate Docker to your Amazon ECR registry
  Replace aws_account_id with your actual AWS account ID:

  `aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin aws_account_id.dkr.ecr.us-west-2.amazonaws.com`
  
3.4. Tag your Docker image
Replace aws_account_id with your actual AWS account ID:

  `docker tag my-fastapi-app:latest aws_account_id.dkr.ecr.us-west-2.amazonaws.com/my-fastapi-app:latest`
  
3.5. Push the Docker image to Amazon ECR
  Replace aws_account_id with your actual AWS account ID:

  `docker push aws_account_id.dkr.ecr.us-west-2.amazonaws.com/my-fastapi-app:latest`
  
  You can now deploy the Docker image from Amazon ECR to your desired AWS service, such as Amazon ECS or AWS Fargate.


  # Architecture Diagram
  
  ![databricks](https://user-images.githubusercontent.com/123284219/226489807-57021815-a84a-4834-9e0a-b53b08476e2d.png)
  
  
