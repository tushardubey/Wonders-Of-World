# Wonders of the World - DevSecOps Pipeline

## Project Overview
It is a web-based platform designed to showcase iconic global landmarks. This repository includes both the frontend and backend services, with MongoDB as the database. The project integrates a **DevSecOps pipeline** ensuring continuous security checks, automated deployments, and vulnerability scans through **OWASP**, **SonarQube**, and **Trivy**.

## Key Technologies
- **Frontend**: React.js (UI/UX)
- **Backend**: Node.js, Express (API)
- **Database**: MongoDB
- **Security**: OWASP for application security, Trivy for Docker image vulnerability scanning, SonarQube for code quality analysis
- **DevSecOps**: Jenkins, Docker, Git

## Architecture Overview
- **Backend**: Provides the APIs to interact with the MongoDB database.
- **Frontend**: Displays the data fetched from the backend.
- **Database**: MongoDB, hosted in a Docker container, persists application data.
- **Redis**: Used for caching and faster data retrieval.

## Steps
- Create image
- Create docker-compose
- Set up Jenkins with the necessary plugins (Docker, Git, SonarQube, OWASP ZAP, Trivy).
- Configure the pipeline with the appropriate build, test, security scanning, and deploy steps.

## DevSecOps Features
- **Continuous Security Scanning**:
  - **SonarQube**: Performs static code analysis for vulnerabilities, code quality issues, and security flaws.
  - **OWASP ZAP**: Conducts dynamic application security testing (DAST) to identify runtime vulnerabilities and attacks.
  - **Trivy**: Scans Docker images for known vulnerabilities in software dependencies and configurations.
  
- **Automated Deployment**: Docker ensures consistent and repeatable deployments, enhancing security through isolated containers.
- **Environment Variables**: Secure handling of sensitive information via `.env.docker` files for both frontend and backend.
- **Image Integrity**: Docker images built from Dockerfiles ensure that the application is deployed securely and consistently across environments.

## Docker Compose Configuration
This project uses Docker Compose to manage multi-container deployments:

- **mongodb**: MongoDB database for storing application data.
- **backend**: Node.js backend server that interacts with MongoDB.
- **frontend**: React.js frontend to display data.
- **redis**: Redis for caching to enhance application performance.
- **sonarqube**: SonarQube for static code analysis and quality checks.

## Known Issues
- SonarQube Slow Analysis: In some cases, the SonarQube analysis may take longer depending on the size of the codebase. Ensure sufficient system resources (memory, CPU) are allocated to the container running SonarQube.
- Trivy False Positives: Occasionally, Trivy may report vulnerabilities that are not actual threats. Verify the vulnerability by checking its CVE details.
- Jenkins Pipeline Failures: If the Jenkins pipeline fails at any stage, ensure that the required plugins (SonarQube, Docker, Git) are properly installed and configured go through the logs to get the reason and troubleshoot the failure.
- Make sure java_home is pointing to the correct user
- .git issue - If it get corrupted remove the files and again clone it


