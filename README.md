# Enterprise DevSecOps Pipeline

This project demonstrates the implementation of a complete DevSecOps CI/CD pipeline using Jenkins for automating application build, testing, containerization, security scanning, and deployment processes.

The pipeline integrates Docker for containerization, Syft for SBOM generation, and Grype for vulnerability scanning to ensure secure software delivery. AWS services such as S3 and EC2 are used for artifact storage and deployment.

The project follows DevSecOps practices by integrating security checks directly into the CI/CD workflow, enabling automated vulnerability detection before deployment.

## Key Features

- Automated CI/CD pipeline using Jenkins
- Docker image build and containerization
- Automated security scanning using Syft and Grype
- DockerHub integration for image storage
- AWS S3 integration for report storage
- Jenkins credentials management for secure secrets handling
- Automated deployment workflow
- Artifact archiving and reporting
- GitHub integration with webhook triggering

## Workflow

1. Developer Pushes Code
2. GitHub Repository
3. Jenkins Pipeline Triggered
4. Build Application
5. Build Docker Image
6. Syft Security Scan
7. Grype Vulnerability Scan
8. Push Image to DockerHub
9. Upload Reports to AWS S3
10. Deploy Application

## Technologies Used

| Technology | Purpose |
| --- | --- |
| Jenkins | CI/CD Automation |
| Docker | Containerization |
| Amazon Web Services | Cloud Services |
| Syft | SBOM Generation |
| Grype | Vulnerability Scanning |
| GitHub | Source Code Management |
| Python | Sample Application |

## Objectives

- Automate software delivery pipelines
- Implement DevSecOps practices
- Improve deployment reliability
- Enhance container security
- Integrate cloud services with CI/CD
- Demonstrate real-world DevOps workflows

## Expected Outcome

The project produces a fully automated and secure CI/CD pipeline capable of building, scanning, storing, and deploying containerized applications with integrated security validation and cloud deployment support.
