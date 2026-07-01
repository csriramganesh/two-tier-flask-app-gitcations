# 🚀 Two-Tier Flask Application CI/CD with GitHub Actions

A complete **CI/CD pipeline** for a **Two-Tier Flask Application** using **GitHub Actions**, **Docker**, **Docker Hub**, **Composite Actions**, **Reusable Workflows**, and a **Self-Hosted Runner on AWS EC2**.

The project demonstrates how to automate Docker image builds, publish images to Docker Hub, and deploy the latest version of the application to an EC2 instance whenever code is pushed to the repository.

---

# 📌 Project Overview

This project automates the complete software delivery process.

* Build Docker image
* Tag image with `latest` and Git commit SHA
* Push image to Docker Hub
* Trigger deployment automatically
* Deploy on AWS EC2 using a GitHub Self-Hosted Runner
* Run the application using Docker Compose

---

# 🏗️ CI/CD Architecture

```text
Developer Push
       │
       ▼
GitHub Actions (Caller Workflow)
       │
       ▼
Reusable Workflow
       │
       ▼
Composite Action
       │
       ▼
Docker Build
       │
       ▼
DockerHub
       │
       ▼
Deploy Workflow
       │
       ▼
Self-Hosted Runner (EC2)
       │
       ▼
docker compose pull
       │
       ▼
docker compose up -d
       │
       ▼
Flask + MySQL Application Live
```

---

# 🛠️ Tech Stack

* Python
* Flask
* MySQL
* Docker
* Docker Compose
* GitHub Actions
* Composite Actions
* Reusable Workflows
* Docker Hub
* AWS EC2
* Self-Hosted Runner
* Ubuntu Linux

---

# ✨ Features

* Automated CI/CD Pipeline
* Docker Image Build
* Docker Image Versioning
* Docker Hub Integration
* GitHub Secrets
* Composite Actions
* Reusable Workflows
* Self-Hosted Runner Deployment
* Docker Compose Deployment
* Automatic Deployment after Successful CI

---

# 📂 Project Structure

```text
.
├── .github
│   ├── actions
│   │   └── docker-build-push
│   │       └── action.yml
│   └── workflows
│       ├── docker-build.yml
│       ├── reusable-docker-build.yml
│       └── deploy.yml
├── templates
├── Dockerfile
├── Dockerfile.multi
├── docker-compose.yml
├── app.py
├── message.sql
├── requirements.txt
├── README.md
└── screenshots
```

---

# ⚙️ CI Pipeline

The CI pipeline performs the following tasks automatically:

* Checkout Repository
* Build Docker Image
* Tag Image
* Login to Docker Hub
* Push Image to Docker Hub

---

# ♻️ Image Tagging

Each build creates two Docker image tags:

* `latest`
* Git Commit SHA

Example:

```text
csriramganesh/two-tier-flask-app-gitactions:latest
csriramganesh/two-tier-flask-app-gitactions:f7b12ac...
```

This enables version tracking and rollback to previous builds.

---

# 🧩 Composite Action

A Composite Action was created to avoid repeating Docker build and push logic across multiple workflows.

It performs:

* Docker Build
* Docker Login
* Push latest tag
* Push Git SHA tag

---

# 🔄 Reusable Workflow

A reusable workflow was implemented using `workflow_call`.

The caller workflow simply passes:

* Docker username
* Docker password
* Image name

This keeps repositories clean and reusable.

---

# 🚀 CD Pipeline

The deployment workflow runs after the CI workflow completes successfully.

Deployment steps:

1. Checkout Repository
2. Pull Latest Docker Image
3. Stop Existing Containers
4. Start Updated Containers
5. Verify Running Containers

---

# 🖥️ Self-Hosted Runner

The deployment is executed on an AWS EC2 Ubuntu instance configured as a GitHub Self-Hosted Runner.

Benefits:

* Full control over deployment environment
* Faster deployments
* Real production-like CI/CD experience

---

# 📸 Project Screenshots

## 1. Project Structure

![Project Structure](screenshots/01_project_structure_created.png)

---

## 2. Docker Build Workflow

![Docker Build Workflow](screenshots/02_docker_build_workflow_created.png)

---

## 3. Docker Build Successful

![Docker Build Success](screenshots/06_docker_build_workflow_success.png)

---

## 4. Docker Hub Push Successful

![DockerHub Push](screenshots/07_dockerhub_push_success.png)

---

## 5. Docker Image Uploaded

![DockerHub Image](screenshots/08_dockerhub_image_uploaded.png)

---

## 6. Git SHA Tag Added

![SHA Tag](screenshots/09_workflow_updated_with_sha_tag.png)

---

## 7. Docker Hub Image Tags

![Docker Tags](screenshots/10_dockerhub_latest_and_sha_tags.png)

---

## 8. Composite Action

![Composite Action](screenshots/11_composite_action_created.png)

---

## 9. Workflow Using Composite Action

![Composite Workflow](screenshots/12_workflow_using_composite_action.png)

---

## 10. Composite Action Workflow Success

![Composite Success](screenshots/13_composite_action_workflow_success.png)

---

## 11. Reusable Workflow

![Reusable Workflow](screenshots/14_reusable_workflow_created.png)

---

## 12. Caller Workflow

![Caller Workflow](screenshots/15_caller_workflow_created.png)

---

## 13. Reusable Workflow Success

![Reusable Success](screenshots/16_reusable_workflow_success.png)

---

## 14. EC2 Connected

![EC2 SSH](screenshots/17_ec2_ssh_connected.png)

---

## 15. Docker Installed on EC2

![Docker EC2](screenshots/19_docker_installed_on_ec2.png)

---

## 16. Self Hosted Runner Configuration

![Runner Config](screenshots/20_self_hosted_runner_configured.png)

---

## 17. Runner Ready

![Runner Idle](screenshots/21_runner_status_idle.png)

---

## 18. Docker Compose Updated

![Compose](screenshots/22_compose_updated_for_dockerhub_image.png)

---

## 19. Deployment Workflow

![Deploy Workflow](screenshots/23_deploy_workflow_created.png)

---

## 20. Deployment Success

![Deployment Success](screenshots/24_deployment_workflow_success.png)

---

## 21. Containers Running on EC2

![Containers Running](screenshots/25_containers_running_on_ec2.png)

---

## 22. Application Live

![Application Live](screenshots/26_application_live_on_ec2.png)

---

## 23. Complete CI/CD Pipeline

![Complete Pipeline](screenshots/27_complete_ci_cd_pipeline.png)

---

# 🎯 Learning Outcomes

Through this project, I gained practical experience with:

* GitHub Actions
* Docker Image Automation
* Docker Hub Integration
* GitHub Repository Secrets
* Docker Image Versioning
* Composite Actions
* Reusable Workflows
* Self-Hosted Runners
* Docker Compose Deployment
* End-to-End CI/CD Pipeline Design
* AWS EC2 Deployment Automation

---

# 🚀 Future Improvements

* Kubernetes Deployment
* Helm Charts
* GitOps using Argo CD
* Terraform Infrastructure Automation
* Prometheus & Grafana Monitoring
* Blue/Green Deployment Strategy
* Automated Security Scanning
* Slack Notifications

---

# ⭐ If you found this project helpful

If you found this project useful, consider giving the repository a ⭐ 

