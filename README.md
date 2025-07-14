# CI/CD Pipeline for Node.js Application

This project outlines a CI/CD pipeline setup for automating the deployment of a Node.js application using Jenkins, SonarQube for SAST, Docker, Docker Hub, and a Kubernetes cluster on AWS.

# Prerequisites
#helloooooooo
## Ensure the following are installed and configured:
 * Jenkins: Installed and configured with plugins for GitHub, SonarQube, Docker, and Kubernetes.
 * GitHub Repository: A repository containing the Node.js application.
 * Docker: Installed on the Jenkins server to build Docker images.
 * Kubernetes Cluster: A functional Kubernetes cluster with at least one master and one worker node.
 * SonarQube: Set up for Static Application Security Testing (SAST).
 * Docker Hub Account: For storing Docker images.

# Architecture Diagram

 * you can view the full architecture diagram [here](you can view the full architecture diagram [here](link-to-your-architecture-diagram))

# Pipeline Steps

## 1.SCM Checkout (GitHub Integration)

* Ensure the Git Plugin is installed in Jenkins.
* Create a new Pipeline job in Jenkins, providing the GitHub repository URL and authentication credentials.
  
## 2.SonarQube Analysis (SAST)

* Install Docker Compose to set up a SonarQube instance
  
  sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  
  sudo chmod +x /usr/local/bin/docker-compose

* Configure a docker-compose.yml file for SonarQube and PostgreSQL.
* Install and configure the SonarQube Scanner plugin in Jenkins to enable code analysis.

  ## 3.npm Build

* Install and configure the Node.js plugin in Jenkins.
* Install Node.js on the Jenkins server:
   * sudo apt update
   * sudo apt install nodejs npm
 
## 4.Build Docker Image

* Ensure a Dockerfile exists in the root of your repository.
* Add a Docker build step in the Jenkins pipeline script to build the Docker image.
  
## 5.Push Docker Image to Docker Hub

* Add Docker Hub credentials in Jenkins.
* In the pipeline script, log in to Docker Hub and push the Docker image.

## 6.Deploy to Kubernetes

* Install the kubectl and kops binaries on the Jenkins server.
* Create and configure an S3 bucket for Kubernetes state storage in AWS.
* Use kops to create a Kubernetes cluster and configure the Kubernetes plugin in Jenkins.
* Deploy the Docker image to Kubernetes, referencing a deployment.yaml file.

## Notes
* Use kops and kubectl to manage the Kubernetes cluster on AWS.
* Ensure Jenkins is updated with necessary credentials for GitHub, Docker Hub, and Kubernetes access.



