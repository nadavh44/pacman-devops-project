# 🎮 Pac-Man DevOps Project

A production-oriented DevOps implementation of the classic **Pac-Man** application using **Amazon EKS Auto Mode**, **GitHub Actions**, **Docker**, **Amazon ECR**, and **Kubernetes**.

This project demonstrates modern DevOps practices including Infrastructure as Code, Kubernetes orchestration, secure CI/CD with GitHub OIDC authentication, containerized deployments, and automated delivery to Amazon EKS.

---

## 📌 Project Overview

The goal of this project was to deploy the Pac-Man application on Amazon Elastic Kubernetes Service (EKS) while implementing a secure and automated CI/CD pipeline following modern cloud engineering best practices.

The solution provisions an Amazon EKS Auto Mode cluster, builds Docker images, stores them in Amazon Elastic Container Registry (ECR), and automatically deploys application updates to Kubernetes using GitHub Actions.

To improve the project's production readiness, static AWS credentials were replaced with GitHub OpenID Connect (OIDC), allowing the CI/CD pipeline to assume temporary IAM roles without storing long-lived secrets.

This repository was developed as part of a DevOps Engineering course while following professional engineering standards, emphasizing automation, security, maintainability, reproducibility, and clear technical documentation.

## 🚀 Technologies

![AWS](https://img.shields.io/badge/AWS-EKS%20Auto%20Mode-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.34-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI%2FCD-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Amazon ECR](https://img.shields.io/badge/Amazon-ECR-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![OIDC](https://img.shields.io/badge/Security-GitHub_OIDC-success?style=for-the-badge)
![MongoDB](https://img.shields.io/badge/MongoDB-StatefulSet-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![eksctl](https://img.shields.io/badge/eksctl-Auto%20Mode-blueviolet?style=for-the-badge)
![EKS Auto Mode](https://img.shields.io/badge/EKS-Auto%20Mode-success?style=for-the-badge)

---

# 🏗️ Solution Architecture

The following diagram illustrates the complete production architecture of the project.

It includes GitHub Actions, Amazon ECR, Amazon EKS Auto Mode, the Kubernetes workloads, MongoDB StatefulSet with persistent storage, and the external Network Load Balancer used to expose the application.

<p align="center">
  <img src="docs/diagrams/runtime-architecture.png" alt="Runtime Architecture" width="900">
</p>

---

# 🔄 CI/CD Pipeline

The following diagram illustrates the complete CI/CD workflow implemented for this project.

Every code change pushed to the **master** branch automatically triggers GitHub Actions to:

- Build the Docker image
- Tag the image using the Git commit SHA
- Push the image to Amazon ECR
- Authenticate to AWS using GitHub OIDC
- Update the running workload on Amazon EKS

<p align="center">
  <img src="docs/diagrams/cicd-pipeline.png" alt="CI/CD Pipeline" width="900">
</p>

---

# ⭐ Project Highlights

- 🔐 Implemented passwordless AWS authentication using **GitHub OIDC**, eliminating the need for long-lived AWS access keys.
- ☸️ Deployed the application on **Amazon EKS Auto Mode**, leveraging managed Kubernetes infrastructure.
- 🚀 Built a fully automated **CI/CD pipeline** using GitHub Actions.
- 📦 Built, tagged, and pushed Docker images automatically to **Amazon Elastic Container Registry (ECR)**.
- 🏷️ Implemented automatic Docker image versioning using the **Git commit SHA**.
- 💾 Deployed **MongoDB as a StatefulSet** with persistent storage backed by Amazon EBS volumes.
- 🌐 Exposed the application through an **AWS Network Load Balancer (NLB)**.
- ⚙️ Managed the Kubernetes infrastructure using declarative YAML manifests and **eksctl**.
- 🧹 Performed complete AWS resource cleanup after project validation to avoid unnecessary cloud costs.

# 🛠️ Technology Stack

| Category | Technology |
|----------|------------|
| Cloud Platform | Amazon Web Services (AWS) |
| Container Orchestration | Amazon EKS Auto Mode |
| Containerization | Docker |
| Container Registry | Amazon Elastic Container Registry (ECR) |
| CI/CD | GitHub Actions |
| Authentication | GitHub OIDC |
| Kubernetes Resources | Deployment, StatefulSet, Service, PersistentVolumeClaim |
| Database | MongoDB |
| Infrastructure Provisioning | eksctl |
| Load Balancer | AWS Network Load Balancer (NLB) |
| Storage | Amazon EBS Persistent Volumes |
| Version Control | Git & GitHub |

# 📁 Repository Structure

```text
.
├── .github/
│   └── workflows/          # GitHub Actions CI/CD pipeline
├── docker/                 # Docker build files
├── docs/
│   ├── diagrams/           # Architecture and CI/CD diagrams
│   ├── screenshots/        # Project screenshots
│   └── prompts/            # AI prompts used to generate diagrams
├── ekscluster/             # EKS Auto Mode cluster configuration
├── k8s/                    # Kubernetes manifests
├── lib/                    # Application source files
├── public/                 # Static application assets
├── app.js                  # Application entry point
├── package.json
└── README.md
```

# 🔐 Security Implementation

Security was a key design consideration throughout this project.

The following practices were implemented:

- **GitHub OIDC Authentication** instead of long-lived AWS access keys.
- **IAM Role assumption** with temporary credentials for GitHub Actions.
- **Least Privilege IAM permissions** for deployment operations.
- **Amazon ECR authentication** using temporary AWS credentials.
- **Git SHA image tagging** to ensure immutable deployments.
- No AWS credentials or sensitive information are stored in the repository.
- All cloud resources were removed after validation to minimize security exposure and cloud costs.

# ⚙️ Deployment Workflow

The deployment process is fully automated using GitHub Actions and GitHub OIDC authentication.

The workflow follows these steps:

```text
Developer
    │
    ▼
Push to GitHub (master)
    │
    ▼
GitHub Actions
    │
    ├── Checkout Repository
    ├── Build Docker Image
    ├── Tag Image with Git Commit SHA
    ├── Authenticate to AWS using GitHub OIDC
    ├── Push Image to Amazon ECR
    ├── Configure kubectl
    └── Deploy Kubernetes Manifests
    │
    ▼
Amazon EKS Auto Mode
    │
    ▼
Pac-Man Application
```

Each deployment is versioned using the Git commit SHA, ensuring traceability and immutable image versions. GitHub OIDC enables secure authentication to AWS without storing long-lived credentials inside the repository.

# ☸️ Kubernetes Architecture

The application is deployed on Amazon EKS Auto Mode using Kubernetes native resources.

| Resource | Purpose |
|----------|---------|
| Deployment | Runs multiple replicas of the Pac-Man application for high availability |
| StatefulSet | Hosts the MongoDB database with stable identities |
| PersistentVolumeClaim | Provides persistent storage for MongoDB |
| Service (ClusterIP) | Internal communication between Pac-Man and MongoDB |
| Service (LoadBalancer) | Exposes the application externally using AWS Network Load Balancer |

The application consists of stateless and stateful workloads, following Kubernetes best practices by separating the application layer from the database layer.

# ☁️ Infrastructure

The infrastructure was provisioned using **eksctl** with **Amazon EKS Auto Mode**, reducing operational overhead while maintaining a production-oriented Kubernetes environment.

Main infrastructure components:

- Amazon EKS Auto Mode Cluster
- Amazon Elastic Container Registry (ECR)
- AWS IAM Roles
- GitHub OIDC Identity Provider
- AWS Network Load Balancer
- Amazon EBS Persistent Volumes
- Kubernetes Deployments and StatefulSets

Infrastructure configuration files are located under the `ekscluster/` directory, while Kubernetes manifests are stored in the `k8s/` directory.

# 🚀 Deployment Guide

## Prerequisites

- AWS Account
- AWS CLI
- kubectl
- eksctl
- Docker
- GitHub Repository
- GitHub Actions
- GitHub OIDC configured
- Amazon EKS Auto Mode Cluster

## Deployment Steps

1. Clone the repository.
2. Build the Docker image.
3. Push the image to Amazon ECR.
4. Configure access to the EKS cluster.
5. Apply the Kubernetes manifests.
6. Verify the deployment using kubectl.

# ✅ Validation

The deployment was successfully validated by verifying the following:

- Docker image successfully built and pushed to Amazon ECR.
- GitHub Actions workflow completed successfully.
- GitHub OIDC authentication successfully assumed the IAM deployment role.
- Amazon EKS cluster was reachable using kubectl.
- Kubernetes resources were successfully deployed.
- MongoDB StatefulSet initialized correctly.
- Persistent storage was successfully attached.
- Pac-Man application became accessible through the AWS Network Load Balancer.
- Application functionality was verified through browser testing.

# 📸 Project Screenshots

Project screenshots documenting the implementation process are available under:

```text
docs/screenshots/
```

The screenshots cover the complete project lifecycle, including:

- AWS infrastructure provisioning
- Amazon EKS cluster creation
- GitHub Actions workflow execution
- Amazon ECR image publishing
- Kubernetes deployment
- Running application
- Project validation
```

# ⚖️ Engineering Decisions

Several engineering decisions were made throughout the project to improve security, maintainability, and operational simplicity.

| Decision | Reason |
|----------|--------|
| Amazon EKS Auto Mode | Reduced infrastructure management overhead |
| GitHub OIDC | Eliminated long-lived AWS credentials |
| Git SHA Image Tags | Improved deployment traceability |
| MongoDB StatefulSet | Enabled persistent database storage |
| Amazon ECR | Native integration with AWS and Kubernetes |
| eksctl | Simple and declarative cluster provisioning |
| Network Load Balancer | Native Kubernetes LoadBalancer integration |

# 📚 Lessons Learned

This project provided hands-on experience with:

- Amazon EKS Auto Mode
- Kubernetes workload management
- GitHub Actions CI/CD
- GitHub OIDC authentication
- Amazon ECR image management
- Kubernetes StatefulSets
- Persistent Volumes
- Kubernetes Services
- Infrastructure automation
- Cloud security best practices

Beyond the technical implementation, the project reinforced the importance of automation, documentation, reproducibility, and engineering decision-making when designing cloud-native applications.

# 🚀 Future Improvements

Possible production enhancements include:

- Helm chart packaging
- GitOps deployment using ArgoCD
- Monitoring with Prometheus and Grafana
- Centralized logging
- Horizontal Pod Autoscaler
- AWS Secrets Manager integration
- TLS termination and custom domain
- Multi-environment deployment strategy

# 🧹 Cleanup

After validating the project, all AWS resources were removed to avoid unnecessary cloud costs.

The cleanup included:

- Amazon EKS Cluster
- Amazon ECR resources
- IAM temporary resources created specifically for the project
- Kubernetes workloads
- Persistent storage

# 👨‍💻 Author

**Nadav Harari**

DevOps Portfolio Project

GitHub: https://github.com/nadavh44