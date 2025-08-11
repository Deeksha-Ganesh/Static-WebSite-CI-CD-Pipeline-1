Static Website CI/CD Pipeline

This project demonstrates a CI/CD pipeline that automates the deployment of a static website. Whenever changes are pushed to GitHub, Jenkins builds a Docker image, pushes it to Docker Hub, and deploys the container on an AWS EC2 instance.

Architecture

Developer → GitHub → Jenkins (CI) → Docker Hub → AWS EC2 (CD)


Tools Used
AWS EC2 (Ubuntu instance for Jenkins & Amazon Linux for deployment)

GitHub (to store website code)

Jenkins (pipeline automation)

Docker (containerization)

Docker Hub (image registry)

Project Overview

A static website built with HTML/CSS stored in GitHub.

A Dockerfile that packages the website using an Apache HTTP server container.

Jenkins pipeline automates building, pushing Docker images, and deploying to AWS EC2.

The deployed app is accessible via the public IP of the EC2 instance.

Prerequisites

AWS account with EC2 instances launched (Ubuntu for Jenkins, Amazon Linux for deployment)

Docker Hub account

Jenkins installed on EC2 with Docker configured

GitHub repository containing the static website and Jenkinsfile

Setup Instructions
1. Prepare Jenkins Server (Ubuntu EC2)
2. Install Docker on Jenkins Server
3. Create GitHub Repository and upload your code
4. Create Dockerfile
5. Create Docker Hub Repository
6. Setup Jenkins Pipeline
Install “Pipeline” plugin in Jenkins.
Create a new Pipeline job using “Pipeline script from SCM”.
Provide your GitHub repo URL.
7. Setup Deployment EC2 (Amazon Linux)

8. Run the Pipeline(if any changes occurred)
Jenkins will automatically:
Build the Docker image.
Push it to Docker Hub.
SSH into EC2 and deploy the updated container.
Access your website at Deployment Instance.
