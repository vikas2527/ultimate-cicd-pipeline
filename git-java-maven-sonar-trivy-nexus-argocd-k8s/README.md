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


🔹 Pipeline Stages & Their Meaning
1. Checkout

What happens: Jenkins pulls the source code from GitHub (ultimate-cicd-pipeline repo).

Why: Always start with fresh, latest code from version control.

2. Maven Compile

What happens: Runs mvn compile on the Spring Boot app.

Why: Compiles Java source code into .class files, ensuring there are no syntax errors.

3. Maven Test

What happens: Executes mvn test.

Why: Runs unit tests (JUnit/TestNG) to validate business logic. If tests fail, pipeline stops.

4. SonarQube Analysis

What happens: Runs mvn sonar:sonar with SonarQube server.

Why: Performs static code analysis → checks for code smells, bugs, vulnerabilities, and bad practices.

5. Quality Gate (added fix)

What happens: Jenkins waits for SonarQube’s Quality Gate status.

Why: If the project doesn’t meet quality standards, pipeline fails before going further.

6. Maven Package

What happens: Runs mvn package.

Why: Packages the app into a deployable artifact (like .jar file for Spring Boot).

7. Upload Artifact to Nexus

What happens: Runs mvn deploy to push the artifact to Nexus repository.

Why: Stores the build artifacts in a central repository → versioning + reusability.

8. Build Docker Image

What happens: Builds a Docker image with the compiled .jar and tags it (vikas115/java-cicd:<build number>).

Why: Containerizes the application for deployment across environments.

9. Trivy Scan

What happens: Scans the Docker image for vulnerabilities in OS packages & libraries.

Why: Ensures only secure images are deployed. Pipeline fails if HIGH/CRITICAL issues exist.

10. Push Docker Image

What happens: Pushes the Docker image to Docker Hub (vikas115/java-cicd).

Why: Makes the image available for deployment in Kubernetes (via ArgoCD).

11. Update Deployment File

What happens: Updates Kubernetes deployment.yml with the new Docker image tag and pushes it back to GitHub.

Why: This triggers GitOps flow with ArgoCD, which syncs manifests and updates the app in the cluster.

🔹 Post Actions
✅ On Success

Sends a success email with build details (build number, Docker image, branch).

❌ On Failure

Sends a failure email with an alert to check logs.

👤 Author
Vikas Singh
💼 DevOps Engineer | ⚙️ CI/CD & Cloud Enthusiast
📧 vikas9878@gmail.com
