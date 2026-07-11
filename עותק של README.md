# Pacman DevOps Project

![GitHub last commit](https://img.shields.io/github/last-commit/nadavh44/pacman-devops-project)
![GitHub repo size](https://img.shields.io/github/repo-size/nadavh44/pacman-devops-project)
![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/nadavh44/pacman-devops-project/main_secure.yml)
![AWS](https://img.shields.io/badge/AWS-EKS%20Auto%20Mode-orange)
![Docker](https://img.shields.io/badge/Docker-Containerized-blue)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestration-326CE5)
![Terraform](https://img.shields.io/badge/IaC-Ready-623CE4)
![License](https://img.shields.io/badge/License-MIT-green)

---

## Project Overview

This project demonstrates a complete end-to-end DevOps implementation for deploying the classic **Pacman** application on **Amazon Elastic Kubernetes Service (Amazon EKS Auto Mode)** using modern cloud-native technologies and DevOps best practices.

The objective was not only to deploy a containerized application, but also to design and implement a secure, automated, and reproducible deployment pipeline that reflects real-world engineering practices.

The project covers the entire software delivery lifecycle—from infrastructure provisioning and containerization to Continuous Integration, Continuous Deployment, Kubernetes orchestration, and cloud-native security.

Unlike a simple deployment exercise, this repository emphasizes infrastructure automation, secure authentication, Kubernetes architecture, and production-oriented engineering decisions suitable for a professional DevOps portfolio.

---

## Project Objectives

- Deploy the Pacman application on Amazon EKS Auto Mode.
- Build a secure CI/CD pipeline using GitHub Actions.
- Authenticate to AWS using GitHub OIDC (without long-lived AWS access keys).
- Store Docker images securely in Amazon ECR.
- Deploy the application automatically to Kubernetes.
- Run MongoDB as a StatefulSet with persistent storage.
- Expose the application through an AWS Network Load Balancer.
- Follow Infrastructure as Code and cloud-native engineering principles.
- Produce a clean, documented, and reproducible DevOps project.

---

# Architecture Overview

The solution consists of four major layers:

1. **Source Control**
   - GitHub Repository
   - GitHub Actions Workflow

2. **Container Platform**
   - Docker
   - Amazon Elastic Container Registry (ECR)

3. **Kubernetes Platform**
   - Amazon EKS Auto Mode
   - Pacman Deployment
   - MongoDB StatefulSet
   - Persistent Volumes
   - Kubernetes Services

4. **AWS Infrastructure**
   - IAM
   - GitHub OIDC Authentication
   - Network Load Balancer
   - Amazon EBS
   - Amazon VPC

---

# Technology Stack

| Category | Technologies |
|-----------|--------------|
| Cloud | AWS |
| Container Platform | Docker |
| Container Registry | Amazon ECR |
| Orchestration | Kubernetes |
| Managed Kubernetes | Amazon EKS Auto Mode |
| Infrastructure Provisioning | eksctl |
| CI/CD | GitHub Actions |
| Authentication | GitHub OIDC |
| Database | MongoDB |
| Storage | Amazon EBS Persistent Volumes |
| Networking | AWS Network Load Balancer |
| Version Control | Git & GitHub |

---

# Key DevOps Features

- Secure GitHub OIDC authentication
- Fully automated CI/CD pipeline
- Docker image build automation
- Automatic image push to Amazon ECR
- Kubernetes automatic deployment
- Git SHA image versioning
- Infrastructure as Code
- Kubernetes StatefulSet deployment
- Persistent storage using Amazon EBS
- Network Load Balancer exposure
- Secure IAM least-privilege permissions
- Production-style repository organization
- Architecture documentation
- CI/CD documentation
- Validation screenshots
- Complete deployment documentation

---

# Project Highlights

This repository demonstrates practical experience with:

- Amazon EKS Auto Mode
- Kubernetes Deployments
- Kubernetes StatefulSets
- Persistent Volumes
- GitHub Actions
- GitHub OIDC
- Amazon ECR
- Docker
- IAM Roles
- Infrastructure as Code
- DevOps Automation
- Cloud Security Best Practices
- Kubernetes Networking
- Production-oriented repository documentation

---

> **Academic Project:** DevOps CI/CD Pipeline for Amazon EKS  
> **Focus:** Cloud Infrastructure, Kubernetes, Automation, Security, and DevOps Engineering

# Repository Structure

```text
pacman-devops-project/
│
├── .github/
│   └── workflows/
│       └── main_secure.yml
│
├── docker/
│   ├── Dockerfile
│   └── ...
│
├── ekscluster/
│   └── cluster.yaml
│
├── k8s/
│   ├── deployment.yaml
│   ├── mongodb-statefulset.yaml
│   ├── service.yaml
│   ├── storageclass.yaml
│   ├── pvc.yaml
│   └── ...
│
├── docs/
│   ├── diagrams/
│   │   ├── architecture-diagram.png
│   │   └── cicd-diagram.png
│   │
│   └── screenshots/
│       ├── phase-1/
│       ├── phase-2/
│       ├── phase-3/
│       ├── phase-4/
│       └── phase-5/
│
├── app.js
├── package.json
├── README.md
└── LICENSE
```

---

# Solution Architecture

The project architecture follows a modern cloud-native deployment model built on Amazon EKS Auto Mode.

The complete deployment flow consists of:

- Developer pushes code to GitHub.
- GitHub Actions automatically starts the CI/CD pipeline.
- GitHub authenticates to AWS using OpenID Connect (OIDC).
- A temporary IAM role is assumed without using long-lived AWS credentials.
- Docker builds the application image.
- The image is pushed to Amazon Elastic Container Registry (ECR).
- GitHub Actions connects securely to Amazon EKS.
- Kubernetes updates the running workload.
- Users access the application through an AWS Network Load Balancer.

---

## Architecture Diagram

> Replace the image below with your exported Architecture Diagram.

<p align="center">

![Architecture](docs/diagrams/architecture-diagram.png)

</p>

---

# CI/CD Pipeline

The deployment pipeline is fully automated using GitHub Actions.

Every deployment follows the same secure workflow:

1. Developer pushes new code.
2. GitHub Actions starts automatically.
3. GitHub authenticates to AWS using OIDC.
4. Temporary AWS credentials are generated.
5. Docker builds the application image.
6. Docker image is pushed to Amazon ECR.
7. kubectl connects to Amazon EKS.
8. Kubernetes updates the running Deployment.
9. Kubernetes pulls the new image from Amazon ECR.
10. The updated application becomes available through the Network Load Balancer.

---

## CI/CD Diagram

> Replace the image below with your exported CI/CD Diagram.

<p align="center">

![CI/CD Pipeline](docs/diagrams/cicd-diagram.png)

</p>

---

# Deployment Workflow

```text
Developer
     │
     ▼
Git Push
     │
     ▼
GitHub Repository
     │
     ▼
GitHub Actions
     │
     ▼
GitHub OIDC Authentication
     │
     ▼
AWS IAM Role
     │
     ▼
Docker Build
     │
     ▼
Amazon ECR
     │
     ▼
Amazon EKS Auto Mode
     │
     ▼
Kubernetes Deployment
     │
     ▼
Network Load Balancer
     │
     ▼
Users
```

---

# Kubernetes Runtime Architecture

Inside the EKS cluster the application consists of two primary workloads.

## Pacman Application

- Kubernetes Deployment
- Multiple replicas
- Stateless application
- Automatically managed by Kubernetes
- Rolling updates enabled

---

## MongoDB Database

- Kubernetes StatefulSet
- Persistent Volume Claims
- Amazon EBS persistent storage
- Stable network identity
- Data persistence across Pod restarts

---

# High-Level Request Flow

```text
User
   │
   ▼
AWS Network Load Balancer
   │
   ▼
Pacman Service
   │
   ▼
Pacman Pods
   │
   ▼
MongoDB Service
   │
   ▼
MongoDB StatefulSet
   │
   ▼
Amazon EBS Persistent Volume
```

# Infrastructure

The infrastructure was provisioned using **Amazon EKS Auto Mode**, which automatically manages the Kubernetes data plane while allowing developers to focus on application deployment rather than cluster administration.

The EKS cluster was created declaratively using **eksctl** and version-controlled as Infrastructure as Code.

## Infrastructure Components

| Component | Purpose |
|-----------|---------|
| Amazon EKS Auto Mode | Managed Kubernetes platform |
| Amazon VPC | Cluster networking |
| IAM | Identity and access management |
| GitHub OIDC | Secure authentication without static credentials |
| Amazon ECR | Docker image registry |
| Amazon EBS | Persistent storage for MongoDB |
| Network Load Balancer | External application access |

---

# Kubernetes Resources

The application is deployed using native Kubernetes resources following cloud-native best practices.

| Resource | Purpose |
|----------|---------|
| Deployment | Runs the Pacman application |
| StatefulSet | Runs MongoDB with persistent identity |
| Service | Internal communication between components |
| LoadBalancer Service | Exposes the application externally |
| PersistentVolumeClaim | Database storage |
| StorageClass | Dynamic Amazon EBS provisioning |

---

# CI/CD Pipeline

The project uses a fully automated GitHub Actions workflow.

Every push triggers a complete deployment pipeline that builds, publishes, and deploys the latest application version.

## Pipeline Stages

### 1. Source Checkout

The workflow retrieves the latest repository version.

---

### 2. AWS Authentication

GitHub authenticates using **OpenID Connect (OIDC)**.

Instead of storing AWS Access Keys inside GitHub Secrets, the workflow assumes an IAM Role and receives temporary AWS credentials during execution.

Benefits:

- No long-lived credentials
- Short-lived security tokens
- Least-privilege access
- AWS recommended authentication method

---

### 3. Docker Build

The application image is built directly from the Dockerfile.

```bash
docker build
```

---

### 4. Amazon ECR Push

After a successful build, the Docker image is pushed to Amazon Elastic Container Registry.

Each image is tagged using the Git commit SHA.

Example:

```text
380648615517.dkr.ecr.us-west-2.amazonaws.com/pacman:9ab13f2
```

Benefits:

- Immutable deployments
- Easy rollback
- Full deployment traceability

---

### 5. Kubernetes Deployment

GitHub Actions updates the Kubernetes Deployment running inside Amazon EKS.

The cluster automatically pulls the new image from Amazon ECR.

Rolling Updates ensure zero downtime during deployment.

---

# Security

Security was incorporated throughout the project rather than added as a final step.

## GitHub OIDC Authentication

Instead of storing permanent AWS credentials in GitHub Secrets, the workflow authenticates using OpenID Connect (OIDC).

Advantages include:

- No AWS Access Keys stored in GitHub
- Temporary STS credentials
- IAM Role assumption
- Reduced credential exposure
- AWS security best practice

---

## IAM Least Privilege

Permissions were granted following the Principle of Least Privilege.

The GitHub deployment role only received the permissions required to:

- Push Docker images to Amazon ECR
- Describe the Amazon EKS cluster
- Deploy Kubernetes manifests

No AdministratorAccess permissions were used by the CI/CD pipeline.

---

## Image Versioning

Every deployment uses the Git commit SHA as the Docker image tag.

Benefits include:

- Immutable artifacts
- Version traceability
- Reliable rollbacks
- Deployment auditing

---

# Storage

MongoDB requires persistent storage.

To ensure data survives Pod recreation, Kubernetes dynamically provisions Amazon EBS volumes using PersistentVolumeClaims.

Benefits include:

- Persistent database storage
- Automatic volume provisioning
- Automatic volume attachment
- Native AWS integration

---

# Networking

Application traffic follows this path:

```text
Internet
     │
     ▼
AWS Network Load Balancer
     │
     ▼
Kubernetes Service
     │
     ▼
Pacman Deployment
     │
     ▼
MongoDB Service
     │
     ▼
MongoDB StatefulSet
```

The Network Load Balancer exposes the application publicly while Kubernetes Services provide reliable internal communication between the application and MongoDB.

---

# Engineering Decisions

Several implementation choices were intentionally made to follow current DevOps best practices.

| Decision | Reason |
|----------|--------|
| Amazon EKS Auto Mode | Simplifies cluster management |
| GitHub OIDC | Eliminates static AWS credentials |
| Git SHA image tags | Immutable deployments |
| MongoDB StatefulSet | Stable identity and persistent storage |
| Amazon ECR | Native AWS container registry |
| eksctl | Simple and reproducible cluster provisioning |
| GitHub Actions | Native GitHub CI/CD integration |
| Network Load Balancer | Kubernetes service exposure on AWS |

---

# Project Phases

The project was completed in multiple engineering phases.

| Phase | Description |
|--------|-------------|
| Phase 1 | AWS IAM configuration |
| Phase 2 | Amazon EKS Auto Mode cluster provisioning |
| Phase 3 | GitHub OIDC authentication |
| Phase 4 | Docker image build and Amazon ECR integration |
| Phase 5 | Kubernetes deployment and MongoDB StatefulSet |
| Phase 6 | CI/CD automation using GitHub Actions |
| Phase 7 | Documentation, diagrams, validation, and cleanup |

# Project Validation

The project was validated end-to-end to ensure that every infrastructure component, Kubernetes resource, and CI/CD process operated as expected.

## Validation Checklist

| Validation | Status |
|------------|:------:|
| Amazon EKS Cluster Created | ✅ |
| GitHub OIDC Authentication | ✅ |
| IAM Least Privilege Configuration | ✅ |
| Docker Image Successfully Built | ✅ |
| Docker Image Pushed to Amazon ECR | ✅ |
| GitHub Actions Pipeline Completed | ✅ |
| Kubernetes Deployment Running | ✅ |
| MongoDB StatefulSet Running | ✅ |
| Persistent Storage Provisioned | ✅ |
| Network Load Balancer Created | ✅ |
| Application Accessible from Browser | ✅ |
| Automatic Redeployment Verified | ✅ |

---

# Screenshots

The complete implementation process is documented with screenshots organized by project phase.

## Phase 1 — AWS & IAM

- IAM User
- IAM Policies
- IAM Role
- GitHub OIDC Provider

📁 `docs/screenshots/phase-1/`

---

## Phase 2 — Amazon EKS

- EKS Auto Mode Cluster
- Cluster Creation
- Node Status
- Kubernetes System Pods

📁 `docs/screenshots/phase-2/`

---

## Phase 3 — CI/CD & Security

- GitHub OIDC Configuration
- GitHub Repository Variables
- GitHub Actions Workflow
- Successful Workflow Execution

📁 `docs/screenshots/phase-3/`

---

## Phase 4 — Kubernetes Deployment

- Running Pods
- Services
- StatefulSet
- PersistentVolumeClaims
- LoadBalancer Service

📁 `docs/screenshots/phase-4/`

---

## Phase 5 — Running Application

- Pacman Application
- Browser Access
- Successful Deployment

📁 `docs/screenshots/phase-5/`

---

# Troubleshooting

During the project several real-world issues were encountered and resolved.

| Issue | Resolution |
|------|------------|
| IAM permission errors | Updated IAM policies following least-privilege principles |
| ECR authentication failures | Added required ECR permissions |
| GitHub authentication | Replaced static credentials with GitHub OIDC |
| Kubernetes deployment failures | Verified manifests and image references |
| LoadBalancer provisioning | Validated Kubernetes Service configuration |
| Cluster access issues | Configured EKS Access Entries and IAM Role permissions |

These troubleshooting steps reflect common operational challenges encountered when deploying Kubernetes workloads on AWS.

---

# Cleanup

To avoid unnecessary AWS charges, all cloud resources were removed after successful validation.

Cleanup included:

- Amazon EKS Cluster
- Worker Nodes
- Network Load Balancer
- Amazon EBS Volumes
- Kubernetes Resources
- Amazon ECR Images (optional)
- Temporary Infrastructure

Following cleanup best practices helps maintain a cost-efficient cloud environment while keeping the project fully reproducible.

---

# Future Improvements

Possible enhancements for a production-grade implementation include:

- Helm Charts
- Argo CD (GitOps)
- Horizontal Pod Autoscaler (HPA)
- Kubernetes Ingress Controller
- External DNS
- AWS Secrets Manager integration
- Monitoring with Prometheus and Grafana
- Centralized logging with Fluent Bit
- Container image vulnerability scanning
- Multi-environment deployment (Dev / Stage / Production)
- Terraform-based infrastructure provisioning
- Blue/Green deployments
- Canary deployments

---

# Lessons Learned

Throughout this project I strengthened practical experience with:

- Amazon EKS Auto Mode
- Kubernetes Deployments
- Kubernetes StatefulSets
- Persistent Volumes
- GitHub Actions
- GitHub OIDC Authentication
- Amazon ECR
- Docker
- IAM Roles and Policies
- Kubernetes Networking
- Infrastructure as Code
- Cloud Security Best Practices
- CI/CD Pipeline Design
- Production-oriented repository organization
- End-to-end Kubernetes application deployment

The project also reinforced the importance of automation, security, reproducibility, and documentation when designing modern cloud-native solutions.

---

# References

- AWS Documentation
- Amazon EKS Documentation
- Kubernetes Documentation
- Docker Documentation
- GitHub Actions Documentation
- GitHub OIDC Documentation
- eksctl Documentation
- MongoDB Documentation

---

# Author

**Nadav Harari**

DevOps Engineer Portfolio Project

GitHub:

https://github.com/nadavh44

LinkedIn:

> *(Add your LinkedIn profile here)*

---

# License

This project is intended for educational and portfolio purposes.

The original Pacman application belongs to its respective authors.

The DevOps implementation, infrastructure, automation, documentation, and CI/CD pipeline were created as part of a hands-on DevOps engineering project.

---

# Acknowledgements

This project was developed as part of a DevOps engineering training program focused on cloud-native infrastructure, Kubernetes, automation, and CI/CD practices.

Special thanks to the course instructors and the open-source community for providing the tools and documentation that made this project possible.