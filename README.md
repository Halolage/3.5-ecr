# Creating and Deploying a Docker Image to AWS ECR

This guide outlines the steps to create a Docker image and deploy it to Amazon Elastic Container Registry (ECR).

## Prerequisites

Before proceeding, ensure you have the following prerequisites:

- Docker installed on your local machine.
- An AWS account with appropriate permissions to create and manage ECR repositories.

## Step 1: Build the Docker Image

1. Clone the repository to your local machine:
```git clone https://github.com/your-repo.git```


2. Navigate to the project directory:
```cd your-repo```


3. Build the Docker image using the Dockerfile:
```docker build -t your-image-name .```


## Step 2: Tag the Docker Image

1. Log in to your AWS account using the AWS CLI:
```aws configure```


2. Create an ECR repository (if not already created):
```aws ecr create-repository --repository-name your-repo-name```


3. Tag the Docker image with the ECR repository URI:
```docker tag your-image-name:latest aws_account_id.dkr.ecr.region.amazonaws.com/your-repo-name:latest```


## Step 3: Authenticate Docker with ECR

1. Get the ECR login command:
```aws ecr get-login-password --region region | docker login --username AWS --password-stdin aws_account_id.dkr.ecr.region.amazonaws.com```


2. Run the generated login command.

## Step 4: Push the Docker Image to ECR

1. Push the Docker image to the ECR repository:
```docker push aws_account_id.dkr.ecr.region.amazonaws.com/your-repo-name:latest```


## Step 5: Use the Docker Image from ECR

Now that your Docker image is pushed to ECR, you can use it for deployments or other purposes:

1. In your AWS account, navigate to the ECR service.

2. Locate your repository (`your-repo-name`) and click on it.

3. Choose the specific image tag (`latest`) you want to use.

4. Click on the "View push commands" button to get instructions on how to pull and use the image.

That's it! You have successfully created a Docker image and deployed it to AWS ECR. You can now utilize the image for running containers in your AWS environment.
