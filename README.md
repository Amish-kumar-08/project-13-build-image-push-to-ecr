# Project 13: Build Docker Image and Push to Amazon ECR

## Overview

Built a Docker image for a sample Nginx web application and published it to Amazon Elastic Container Registry (ECR). Used Docker to containerize the application and AWS CLI to authenticate, tag, and push the image to a private ECR repository.

## Objectives

- Create a Dockerfile for the web application.
- Build a Docker image locally.
- Run and test the Docker container.
- Create a private Amazon ECR repository.
- Authenticate Docker with Amazon ECR using AWS CLI.
- Tag and push the Docker image to ECR.
- Verify the uploaded image using AWS CLI.

## Technologies Used

- AWS
- Amazon Elastic Container Registry (ECR)
- Docker
- AWS CLI
- Linux (Ubuntu)
- Nginx
- Git and GitHub

## AWS Configuration

| Configuration | Value |
|---|---|
| AWS Region | ap-south-1 (Mumbai) |
| AWS Account ID | 590507089733 |
| ECR Repository | project-13-app-amish |
| Repository Type | Private |
| Image Tag | latest |
| Image Status | ACTIVE |

## Project Structure

```text
project-13-build-image-push-to-ecr/
│
├── Dockerfile
├── index.html
└── README.md
```

## Implementation Steps

### 1. Create Docker Image

Built the Docker image using:

```bash
docker build -t project-13-app .
```

### 2. Run Docker Container

```bash
docker run -d -p 8080:80 --name project-13-container project-13-app
```

### 3. Test Application

```bash
curl http://localhost:8080
```

Verified that the Nginx container successfully served the sample HTML application.

### 4. Create Amazon ECR Repository

```bash
aws ecr create-repository \
  --repository-name project-13-app-amish \
  --image-tag-mutability MUTABLE \
  --region ap-south-1
```

### 5. Authenticate Docker with ECR

```bash
aws ecr get-login-password --region ap-south-1 | \
docker login --username AWS --password-stdin \
590507089733.dkr.ecr.ap-south-1.amazonaws.com/project-13-app-amish
```

### 6. Tag Docker Image

```bash
docker tag project-13-app:latest \
590507089733.dkr.ecr.ap-south-1.amazonaws.com/project-13-app-amish:latest
```

### 7. Push Image to Amazon ECR

```bash
docker push \
590507089733.dkr.ecr.ap-south-1.amazonaws.com/project-13-app-amish:latest
```

### 8. Verify Uploaded Image

```bash
aws ecr describe-images \
  --repository-name project-13-app-amish \
  --region ap-south-1
```

Verified that the image was successfully uploaded and its status was ACTIVE.

## Amazon ECR Image Details

**Repository URI:**

```text
590507089733.dkr.ecr.ap-south-1.amazonaws.com/project-13-app-amish
```

**Image Tag:** `latest`

**Image Digest:**

```text
sha256:032b6e384350ce1cf2a4e82e32835808e1a2a3914859f9943752c7c76e68ba28
```

**Image Status:** ACTIVE

## Deliverables

- Dockerfile
- Sample HTML web application
- Successfully built Docker image
- Private Amazon ECR repository
- Docker image successfully pushed to ECR
- AWS CLI verification output

## Outcome

Successfully containerized a web application using Docker and published the Docker image to Amazon ECR. Gained practical experience with Docker image creation, container execution, AWS ECR configuration, registry authentication, image tagging, and image publishing using AWS CLI.

## Author

Amish Kumar

## GitHub Repository

[Project 13 - Build Image and Push to ECR](https://github.com/Amish-kumar-08/project-13-build-image-push-to-ecr)
