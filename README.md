# Netflix Clone DevSecOps Project

In this project, I worked on a **Netflix streaming clone** using various DevSecOps practices. The goal was to build, secure, and monitor the application while setting up a continuous integration and continuous delivery (CI/CD) pipeline using Jenkins. I focused heavily on automation and integrating security checks throughout the process. Here’s a breakdown of the stacks and tools I used across different phases of the project:

---

### Phase 1: Initial Setup and Deployment
First, I provisioned an EC2 instance on AWS running Ubuntu 22.04. Once connected via SSH, I cloned the application code from my GitHub repository. After that, I installed Docker and used it to containerize the Netflix app.

![Docker Setup](./public/assets/docker.png)
*The image is automatically pushed to DockerHub after building the application.*

---

### Phase 2: Security with SonarQube and Trivy
Security was a crucial aspect of the project, so I set up **SonarQube** and **Trivy** to scan the code and Docker images for vulnerabilities. SonarQube was integrated into my Jenkins pipeline to check code quality and security issues.

![SonarQube](./public/assets/sonarqube.png)
*SonarQube confirms that the code passed all quality gates.*

---

### Phase 3: CI/CD with Jenkins
Jenkins played a central role in automating the deployment process. I set up a Jenkins pipeline that included multiple stages, including code checkout, quality gate validation, and vulnerability scanning.

![Jenkins Pipeline](./public/assets/jenkins.png)
*Jenkins CI/CD pipeline automatically triggers deployments.*

---

### Phase 4: Monitoring with Prometheus and Grafana
To keep the app monitored, I installed **Prometheus** and **Grafana**. Prometheus scrapes metrics from my Kubernetes nodes and monitors the system’s health. Grafana visualizes these metrics for easy monitoring.

![Prometheus Metrics](./public/assets/Prometheus.png)
*Prometheus is scraping metrics from Kubernetes.*

![Grafana Dashboards](./public/assets/grafana.png)
*Grafana visualizes CPU and memory usage metrics from Kubernetes nodes.*

---

### Phase 5: Kubernetes Deployment with ArgoCD
I deployed the app using **Kubernetes on AWS EKS** (Elastic Kubernetes Service). I also integrated **ArgoCD** for continuous delivery, which synced my GitHub repository with the Kubernetes cluster.

![AWS EKS Cluster](./public/assets/eks.png)
*AWS EKS cluster running the Netflix app.*

![ArgoCD Sync](./public/assets/argocd.png)
*ArgoCD synchronizing changes from GitHub to the Kubernetes cluster.*

---

### Phase 6: Netflix App Interface
Once the deployment was complete, the Netflix streaming clone was fully functional and accessible.

![Netflix App Interface](./public/assets/netflixpage.png)
*Netflix clone app user interface, streaming "Beetlejuice".*

---

### Conclusion
This project gave me hands-on experience with a wide variety of DevSecOps tools and technologies such as Jenkins, SonarQube, Trivy, Prometheus, Grafana, Docker, Kubernetes, and ArgoCD. The emphasis was not just on getting the Netflix clone app up and running but ensuring it was secure and properly monitored.

---
