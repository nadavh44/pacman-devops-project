# Runtime Architecture Design Specification

This design specification was used to generate the Runtime Architecture Diagram using Eraser AI.

The document defines the architecture, layout, visual hierarchy, engineering constraints, and presentation requirements for the diagram.
Create an architecture diagram:
You are a Principal AWS Solutions Architect preparing a production-ready architecture diagram for a public GitHub DevOps portfolio.

The audience includes Senior DevOps Engineers, Cloud Architects, Technical Interviewers, and Hiring Managers.

This is NOT a generic cloud diagram.

It should look like an architecture review diagram presented during an AWS Design Review meeting.

=========================================================
GOAL
=========================================================

Explain ONLY the runtime architecture of the Pacman application running on Amazon EKS Auto Mode.

The entire architecture should be understandable within 10–15 seconds.

Prioritize engineering communication over artistic appearance.

=========================================================
DO NOT INCLUDE
=========================================================

Do NOT include:

• GitHub
• GitHub Actions
• Docker
• CI/CD
• Terraform
• IAM
• OIDC
• CloudFormation
• VPC
• EC2
• Worker Nodes
• Security Groups
• Subnets
• Route Tables

Those belong in a separate CI/CD diagram.

=========================================================
THE DIAGRAM SHOULD ANSWER
=========================================================

1. How users reach the application.
2. How traffic enters Kubernetes.
3. How Kubernetes routes requests.
4. How the application reaches MongoDB.
5. How MongoDB persists data.

Nothing more.

=========================================================
LAYOUT
=========================================================

Landscape orientation (16:9)

Reading direction:

TOP

↓

BOTTOM

NOT left-to-right.

Avoid long horizontal chains.

Avoid diagonal arrows.

Avoid edge crossings.

Use clean orthogonal connectors.

=========================================================
VISUAL STRUCTURE
=========================================================

Top section

Internet User

↓

AWS Network Load Balancer

↓

Amazon EKS Auto Mode

Inside the EKS container create TWO independent vertical columns.

LEFT COLUMN

Title:

Application Runtime

Components:

Pacman Service (LoadBalancer)

↓

Pacman Deployment

↓

Pacman Pod

(Node.js Application)

RIGHT COLUMN

Title:

MongoDB Persistence

Components:

MongoDB Service

↓

MongoDB StatefulSet

↓

PersistentVolumeClaim

↓

PersistentVolume

=========================================================
CONNECTIONS
=========================================================

Internet User

↓

AWS Network Load Balancer

↓

Pacman Service

↓

Pacman Deployment

↓

Pacman Pod

The Pacman Pod communicates horizontally to MongoDB Service.

Connection label:

mongodb://mongo:27017/pacman

MongoDB Service

↓

MongoDB StatefulSet

↓

PersistentVolumeClaim

↓

PersistentVolume

MongoDB MUST NOT appear as the next step in the application flow.

MongoDB is a dependency, not another application stage.

=========================================================
VISUAL STYLE
=========================================================

Use official AWS architecture icons.

Use official Kubernetes icons.

Use MongoDB logo.

White background.

Rounded containers.

Consistent spacing.

Equal component sizes.

Professional typography.

Soft pastel colors.

Minimal visual noise.

Large whitespace.

The result should resemble an AWS re:Invent architecture slide.

=========================================================
COLORS
=========================================================

AWS Edge Services

Orange

Kubernetes Runtime

Blue

MongoDB

Red

Persistent Storage

Gray

External User

Dark Gray

=========================================================
GROUPING
=========================================================

Create clear nested containers.

AWS Cloud

└── Amazon EKS Auto Mode

      ├── Application Runtime

      └── MongoDB Persistence

Do NOT create unnecessary containers.

=========================================================
SUCCESS CRITERIA
=========================================================

When someone opens the GitHub repository, they should immediately understand:

Internet User

↓

AWS Network Load Balancer

↓

Amazon EKS Auto Mode

Inside EKS:

LEFT
Application Runtime

RIGHT
MongoDB Persistence

The application pod communicates with MongoDB.

MongoDB stores data using Persistent Volumes.

The final result should look polished enough to appear in a professional GitHub portfolio and during a Senior DevOps technical interview.