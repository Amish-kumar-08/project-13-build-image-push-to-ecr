# Project 13: Build Docker Image and Push to Amazon ECR

## Overview

Built a Docker image for a sample web application and published it to Amazon Elastic Container Registry (ECR). Used Docker to containerize the application and AWS CLI to authenticate and push the image to a private ECR repository.

## Objectives

- Create a Dockerfile for the application.
- Build a Docker image locally.
- Verify the Docker image.
- Create a private Amazon ECR repository.
- Authenticate Docker with Amazon ECR.
- Tag and push the Docker image to ECR.
- Verify that the image is successfully stored in ECR.

## Architecture

Application → Dockerfile → Docker Image → Amazon ECR

## Technologies Used

- AWS
- Amazon Elastic Container Registry (ECR)
- Docker
- AWS CLI
- Linux (Ubuntu)
- Git and GitHub

## AWS Configuration

| Configuration | Value |
|---|---|
| AWS Region | ap-south-1 |
| AWS Service | Amazon ECR |
| Repository Type | Private |
| Container Tool | Docker |

## Project Structure

```text
project-13-build-image-push-to-ecr/
│
├── Dockerfile
├── index.html
└── README.md
```

## Implementation Steps

1. Created a GitHub repository for Project 13.
2. Prepared a sample web application.
3. Created a Dockerfile to containerize the application.
4. Built a Docker image locally.
5. Created a private repository in Amazon ECR.
6. Authenticated Docker with Amazon ECR using AWS CLI.
7. Tagged the Docker image with the ECR repository URI.
8. Pushed the Docker image to Amazon ECR.
9. Verified the uploaded image in the AWS Console.

## Docker Commands

### Build Docker Image

```bash
docker build -t project-13-app .
```

### Verify Docker Image

```bash
docker images
```

### Run Docker Container

```bash
docker run -d -p 8080:80 --name project-13-container project-13-app
```

### AWS ECR Authentication

```bash
aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin <AWS_ACCOUNT_ID>.dkr.ecr.ap-south-1.amazonaws.com
```

### Tag Docker Image

```bash
docker tag project-13-app:latest <AWS_ACCOUNT_ID>.dkr.ecr.ap-south-1.amazonaws.com/project-13-app:latest
```

### Push Docker Image to ECR

```bash
docker push <AWS_ACCOUNT_ID>.dkr.ecr.ap-south-1.amazonaws.com/project-13-app:latest
```

## Deliverables

- Dockerfile
- Successfully built Docker image
- Amazon ECR repository
- Docker image successfully pushed to ECR
- Screenshot of the uploaded image in Amazon ECR

## Outcome

Successfully containerized a web application using Docker and published the Docker image to Amazon ECR. Gained practical experience with Docker image creation, AWS ECR configuration, container registry authentication, and image publishing.

## Author

Amish Kumar

## GitHub Repository

[Project 13 - Build Image and Push to ECR](https://github.com/Amish-kumar-08/project-13-build-image-push-to-ecr)
