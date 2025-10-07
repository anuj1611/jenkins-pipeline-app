# Flask Application with CI/CD using Jenkins and Docker

This project demonstrates a **complete CI/CD pipeline** for deploying a Flask application using **Jenkins**, **Docker**, and **GitHub**.
It automates the process of building and deploying the app whenever new code is pushed to the main branch.

---

## Project Overview

- **Application** → Python Flask web app.
- **Containerization** → Dockerized Flask app.
- **Automation Tool** → Jenkins (Declarative Pipeline).
- **Source Control** → Git & GitHub.
- **Trigger Mechanism** → Manual build or GitHub Webhook.

The goal is to achieve a continuous integration and continuous deployment (CI/CD) workflow where every code change is automatically built and deployed inside a Docker container using Jenkins.

---

## Tools & Technologies Used

| Category | Tool |
|-----------|------|
| **Language** | Python 3.10 |
| **Framework** | Flask |
| **Containerization** | Docker Desktop |
| **CI/CD Automation** | Jenkins |
| **Version Control** | Git & GitHub |
| **Operating System** | Windows 11 |

---

## CI/CD Pipeline Summary

1. Developer pushes new code to **GitHub main branch**.
2. **Jenkins** fetches the latest code (via Git SCM).
3. The Jenkins pipeline automatically:
   - Clones the repository.
   - Builds a **Docker image**.
   - Deploys the Flask container.
4. Application becomes accessible locally at **http://localhost:5000**.

---

## Project Structure

```
flask-jenkins-pipeline/
│-- app.py
│-- requirements.txt
│-- Dockerfile
│-- Jenkinsfile
│-- README
```

---

## Steps I took

### Step 1️— Install Prerequisites
- **Java 21**
- **Jenkins (LTS)**
- **Docker Desktop**
- **Visual Studio Code (optional)**

### Step 2️— Install Jenkins Plugins
- Git Plugin
- Pipeline Plugin
- Docker Pipeline Plugin
- Blue Ocean (optional)

### Step 3️— Create a Pipeline Job
1. Go to Jenkins Dashboard → **New Item → Pipeline**
2. Name it `flask-pipeline`
3. Under **Pipeline Definition**, choose **Pipeline script from SCM**
4. Select **Git**
5. Add repository URL:  
   `https://github.com/anuj1611/jenkins-pipeline-app.git`
6. Branch: `*/main`
7. Script Path: `Jenkinsfile`
8. Click **Save → Build Now**

---

## Jenkins Pipeline Stages

| Stage | Description |
|--------|--------------|
| **Checkout** | Pulls latest code from GitHub |
| **Build Docker Image** | Builds image using Dockerfile |
| **Deploy Container** | Runs Flask app in a Docker container |

---

## Learning Outcomes

- Built a working **CI/CD pipeline** using Jenkins.
- Automated Flask app deployment using Docker.
- Configured Jenkins with **Git SCM**.
- Understood end-to-end **DevOps workflow** from Code → Build → Deploy.

---
## Happy Learning!😊

