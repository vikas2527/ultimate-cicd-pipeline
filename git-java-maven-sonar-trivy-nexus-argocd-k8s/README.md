🚀 Ultimate CI/CD Pipeline with Jenkins

This repository demonstrates a complete CI/CD pipeline built using Jenkins and integrated with industry-standard DevOps tools. The pipeline automates the entire process — from code commit to deployment on Kubernetes — ensuring faster, reliable, and production-ready releases.

🛠️ Tools & Technologies Used

   Jenkins – CI/CD orchestration
   Maven – Build & dependency management
   SonarQube – Static code analysis & quality gates
   Nexus – Artifact repository (optional)
   Docker – Containerization of applications
   Docker Hub – Image registry
   ArgoCD – GitOps-based deployment
   Kubernetes – Container orchestration platform
   GitHub – Source code management

🔄 Pipeline Workflow
   Checkout Code – Jenkins fetches code from GitHub
   Build & Test – Maven compiles and runs tests
   Code Quality Check – SonarQube analysis ensures code meets quality standards
   Package & Push Artifact – Artifact is stored in Nexus (optional)
   Build Docker Image – Application is containerized
   Push Image to DockerHub – Versioned image is pushed to Docker registry
   Update Deployment Manifest – Jenkins updates Kubernetes manifests with the new image tag
   ArgoCD Sync – ArgoCD detects manifest changes and deploys automatically to Kubernetes

📂 Repository Structure
.
├── spring-boot-app/                 # Sample Java Spring Boot application
│   ├── src/                         # Source code
│   ├── pom.xml                      # Maven build file
│   └── Dockerfile                   # Docker image build
├── spring-boot-app-manifests/       # Kubernetes deployment manifests
│   └── deployment.yml
├── Jenkinsfile                      # Jenkins pipeline script
└── README.md                        # Project documentation

Prerequisites:

   -  Java application code hosted on a Git repository
   -  Jenkins server with Maven and Docker 
   -  Sonarqube Server
   -  Trivy Server
   -  Nexus Server
   -  Kubernetes cluster
   -  Helm package manager
   -  Argo CD


👤 Author
Vikas Singh
💼 DevOps Engineer | ⚙️ CI/CD & Cloud Enthusiast
📧 vikas9878@gmail.com
