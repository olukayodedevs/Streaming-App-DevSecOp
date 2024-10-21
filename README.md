# Netflix Clone - DevSecOps Project

In this project, I worked on a **Netflix streaming clone** using various **DevSecOps** practices. The goal was to build, secure, and monitor the application while setting up a **CI/CD** pipeline using **Jenkins**. The focus was heavily on automation and integrating security checks throughout the process.

---

## Project Overview

- **Project Type**: DevSecOps Implementation
- **Tech Stack**: Jenkins, Docker, SonarQube, Trivy, Prometheus, Grafana, Kubernetes, ArgoCD, AWS EKS
- **Objective**: Automate the build, deployment, security scanning, and monitoring processes for a Netflix clone using best practices in DevSecOps.

---

### Phase 1: Initial Setup and Deployment

1. **EC2 Instance Setup**: 
   - Provisioned an EC2 instance running **Ubuntu 22.04** on AWS.
   - Connected via SSH to set up the environment.

2. **Code Cloning**:
   - Cloned the application code from **GitHub**:
     ```bash
     git clone https://github.com/N4si/DevSecOps-Project.git
     ```

3. **Docker Installation & App Deployment**:
   - Installed Docker and containerized the Netflix app.
   - Fetched the **TMDB API Key** for movie data and rebuilt the Docker image.
   - Deployed the application with Docker:
     ```bash
     docker build --build-arg TMDB_V3_API_KEY=<your-api-key> -t netflix .
     docker run -d --name netflix -p 8081:80 netflix:latest
     ```

---

### Phase 2: Security with SonarQube and Trivy

1. **SonarQube**:
   - Integrated **SonarQube** into Jenkins for code quality and vulnerability scans.
   - Ensured the code passed all quality gates before proceeding with deployment.

2. **Trivy**:
   - Configured **Trivy** to scan Docker images for filesystem vulnerabilities. This step ensured that the containerized app was secure from known vulnerabilities:
     ```bash
     trivy image netflix:latest
     ```

---

### Phase 3: CI/CD with Jenkins

**Jenkins Pipeline** was the backbone of the entire deployment process, automating everything from code checkout to final deployment. The pipeline stages included:

1. **Clean Workspace**:
   - Cleaned the Jenkins workspace to avoid conflicts from leftover files.
   
2. **Checkout from Git**:
   - Pulled the latest code from the GitHub repository.

3. **SonarQube Analysis**:
   - Ran **SonarQube** analysis to ensure the code met the required quality standards.

4. **Quality Gate**:
   - Checked whether the code passed **SonarQube's quality gate** before moving forward.

5. **Install Dependencies**:
   - Installed required dependencies using Node.js and npm.

6. **OWASP & Trivy Scans**:
   - Conducted **OWASP Dependency Check** and **Trivy** scans to secure the code and Docker images from known vulnerabilities.

7. **Docker Build & Push**:
   - Built the Docker image and pushed it to **DockerHub** for storage and management:
     ```bash
     docker build -t kellapaw/netflix .
     docker push kellapaw/netflix
     ```

8. **Deploy to Container**:
   - Deployed the app to the container.

---

### Phase 4: Monitoring with Prometheus and Grafana

1. **Prometheus**:
   - Installed **Prometheus** to scrape metrics from the Kubernetes nodes and monitor the app’s health.

2. **Grafana**:
   - Set up **Grafana** to visualize real-time metrics like CPU, memory, and container usage.

3. **Node Exporter**:
   - Configured **Node Exporter** to gather detailed system-level metrics from the Kubernetes cluster.

---

### Phase 5: Kubernetes Deployment with ArgoCD

1. **AWS EKS (Elastic Kubernetes Service)**:
   - Deployed the Netflix app using **Kubernetes** on **AWS EKS** for scaling and management.

2. **ArgoCD**:
   - Integrated **ArgoCD** for continuous delivery, automatically syncing the **GitHub** repository with the **Kubernetes** cluster.
   - This helped ensure that any code updates were deployed smoothly.

---

### Phase 6: Notifications

1. **Jenkins Notifications**:
   - Implemented email notifications in Jenkins to alert me of build statuses and any pipeline failures.

---

## Conclusion

This project gave me hands-on experience with a wide variety of **DevSecOps** tools and technologies, such as **Jenkins**, **SonarQube**, **Trivy**, **Prometheus**, **Grafana**, **Docker**, **Kubernetes**, and **ArgoCD**. The key takeaway was learning to automate the entire process, from code quality checks to deployment, with an emphasis on security.

---

### Technologies Used

- **Jenkins**: CI/CD pipeline automation
- **SonarQube**: Code quality and security scans
- **Trivy**: Container security scans
- **Docker**: Containerization
- **Kubernetes**: Orchestration of containers on AWS EKS
- **ArgoCD**: GitOps for continuous delivery
- **Prometheus**: Monitoring
- **Grafana**: Visualization of system metrics
- **AWS EC2**: Compute instances for hosting services
- **DockerHub**: Container image storage

---

### How to Run This Project

1. Clone the repository:
   ```bash
   git clone https://github.com/N4si/DevSecOps-Project.git
