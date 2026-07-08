# CI/CD Pipeline Design



Create an architecture diagram:
Create an Architecture Diagram.

You are a Principal DevOps Engineer and AWS Solutions Architect preparing a production-grade CI/CD pipeline diagram for a public GitHub portfolio.

The audience includes:

• Senior DevOps Engineers
• Cloud Architects
• Technical Interviewers
• Hiring Managers

This is NOT a generic CI/CD diagram.

It should resemble an internal engineering design review document used by a mature DevOps team.

=========================================================
GOAL
=========================================================

Explain how source code is automatically built, authenticated, published and deployed to Amazon EKS.

The complete pipeline should be understandable within 10–15 seconds.

Prioritize engineering communication over artistic appearance.

=========================================================
PROJECT CONTEXT
=========================================================

The project uses:

GitHub Repository

GitHub Actions

GitHub OIDC

AWS IAM Role

Temporary AWS Credentials

Docker Build

Git SHA Image Tagging

Amazon ECR

kubectl apply

Amazon EKS Auto Mode

The deployment is manually triggered using workflow_dispatch.

=========================================================
LAYOUT
=========================================================

Landscape (16:9)

Reading direction:

LEFT

→

RIGHT

The pipeline should read naturally from source code to production.

Avoid diagonal arrows.

Avoid unnecessary edge crossings.

Use orthogonal connectors.

Keep equal spacing between components.

=========================================================
VISUAL GROUPS
=========================================================

Create FOUR clearly separated sections.

Section 1

Source Control

Section 2

CI/CD Pipeline

Section 3

Secure AWS Authentication

Section 4

AWS Deployment

=========================================================
SECTION 1
=========================================================

Developer

↓

GitHub Repository

Arrow label:

Push Code

=========================================================
SECTION 2
=========================================================

GitHub Repository

↓

workflow_dispatch

↓

GitHub Actions

GitHub Actions performs:

Docker Build

↓

Generate Image Tag

Git SHA

↓

Push Image

↓

Amazon ECR

Git SHA should be visually highlighted as an engineering decision.

Do NOT use "latest".

=========================================================
SECTION 3
=========================================================

GitHub Actions requests

GitHub OIDC Token

↓

AWS IAM Role

↓

Temporary AWS Credentials

Arrow label:

AssumeRoleWithWebIdentity

This section should visually communicate:

No Long-Lived AWS Access Keys

Highlight this section in green.

=========================================================
SECTION 4
=========================================================

GitHub Actions

↓

kubectl apply

↓

Amazon EKS Auto Mode

↓

Pacman Deployment Updated

Amazon EKS pulls the new container image from Amazon ECR.

Show the image flow:

Amazon ECR

↓

Amazon EKS Auto Mode

Arrow label:

Pull Image

=========================================================
ENGINEERING DECISIONS
=========================================================

Create a small callout panel.

Title:

Engineering Decisions

Include:

GitHub OIDC
Temporary AWS credentials instead of static access keys.

Git SHA Image Tags
Immutable deployments and full traceability.

Amazon EKS Auto Mode
Reduced operational overhead.

These callouts should not interrupt the pipeline.

=========================================================
VISUAL STYLE
=========================================================

Use official icons whenever possible.

GitHub

GitHub Actions

Docker

Amazon ECR

Amazon EKS

AWS IAM

Kubernetes

White background.

Rounded containers.

Soft pastel colors.

Professional typography.

Minimal visual clutter.

Large whitespace.

=========================================================
COLORS
=========================================================

GitHub

Purple

Security

Green

AWS Services

Orange

Kubernetes

Blue

Docker Build

Blue

Engineering Decisions

Light Gray

=========================================================
DO NOT INCLUDE
=========================================================

MongoDB

StatefulSet

PersistentVolume

PersistentVolumeClaim

Runtime Architecture

Application Traffic

Network Load Balancer

VPC

CloudFormation

Terraform

Those belong in another architecture diagram.

=========================================================
SUCCESS CRITERIA
=========================================================

When someone opens the repository they should immediately understand:

Developer

↓

GitHub Repository

↓

GitHub Actions

↓

Docker Build

↓

Git SHA

↓

Amazon ECR

↓

Amazon EKS Auto Mode

With a clearly visible secure authentication flow using:

GitHub OIDC

↓

AWS IAM Role

↓

Temporary Credentials

The diagram should look polished enough to be presented during a Senior DevOps technical interview and suitable for a professional GitHub portfolio.
The CI/CD pipeline is the primary focus of the diagram.
The OIDC authentication flow should be displayed as a secondary side branch, not as part of the main deployment flow.