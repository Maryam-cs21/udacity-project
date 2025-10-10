🧭 Project Overview

This project deploys a Coworking Analytics API on Amazon EKS, containerized with Docker and backed by a PostgreSQL database. It provides analytics endpoints for daily usage and user visits.

⚙️ Architecture and Deployment

The solution runs on EKS with a Deployment for the application and a StatefulSet for PostgreSQL.
Persistent storage is handled by EBS volumes, and application logs stream to CloudWatch.
The app is exposed externally through a LoadBalancer service.

🧩 Build and Deployment Workflow

Source code is hosted on GitHub and integrated with AWS CodeBuild.
On each GitHub push, CodeBuild automatically builds the Docker image and pushes it to Amazon ECR.
The new image is deployed to EKS via a rolling update using Kubernetes manifests.

🚀 Releasing a New Version

Push code changes to main to trigger a new build in CodeBuild.
Once the build completes, update the image tag in deployment/coworking.yaml and apply:

kubectl apply -f deployment/

Confirm rollout success using:

kubectl rollout status deployment/coworking