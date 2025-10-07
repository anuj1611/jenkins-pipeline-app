# Flask Application with CI/CD using Jenkins and Docker

This project demonstrates a **complete CI/CD pipeline** for deploying a Flask application using **Jenkins**, **Docker**, and **GitHub**.
It automates the process of building and deploying the app whenever new code is pushed to the `main` branch.

---

## Project Overview

- **Application** → Python Flask web app.
- **Containerization** → Dockerized Flask app.
- **Automation Tool** → Jenkins (Declarative Pipeline).
- **Source Control** → Git & GitHub.
- **Trigger Mechanism** → Manual build.

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

1. Developer pushes new code to **GitHub `main` branch**.
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
```

---

## Push Code to GitHub (Required before CI runs)

If you haven't already pushed your project to GitHub, follow these steps from your project root directory:

```bash
# initialize git repo (if not already)
git init

# set main branch name (if your local branch is master)
git branch -M main

# add remote (replace with your repo URL)
git remote add origin https://github.com/anuj1611/jenkins-pipeline-app.git

# add files and commit
git add .
git commit -m "Initial commit: add Flask app, Dockerfile, jenkinsfile"

# push to GitHub
git push -u origin main
```

> After pushing, Jenkins (configured with your repo) can pull the `main` branch and execute the `jenkinsfile` pipeline.

---

## Build, Run & Test Locally (Manual Verification)

These steps let you verify the Docker image and container locally before relying on Jenkins.

### 1. Build the Docker image
```bash
docker build -t jenkins-pipeline-app .
```
**Expected result:** Docker builds the image and tags it as `jenkins-pipeline-app`.

### 2. Run the Docker container
```bash
docker run -d -p 5000:5000 --name flask-container jenkins-pipeline-app
```
**What this does:** Runs the container in detached mode, maps container port `5000` to host port `5000`, and names the container `flask-container`.

### 3. Verify the container is running
```bash
docker ps
```
You should see `flask-container` listed. To view logs:
```bash
docker logs -f flask-container
```

### 4. Test the application
Open your browser and visit:  
```
http://localhost:5000
```
Or use `curl`:
```bash
curl http://localhost:5000
```

Expected response:  
```
Hello from Jenkins CI/CD Pipeline 
```

### 5. Stop & Remove the container (cleanup)
```bash
docker rm -f flask-container
```

---

## Jenkins Setup

### Step 2️— Install Jenkins Plugins
- Git Plugin
- Pipeline Plugin
- Docker Pipeline Plugin
- Blue Ocean (optional)

### Step 3️— Create a Pipeline Job
1. Jenkins Dashboard → **New Item → Pipeline**  
2. Name it `flask-pipeline`  
3. Under **Pipeline Definition**, choose **Pipeline script from SCM**  
4. Select **Git** and add the repository URL:  
   `https://github.com/anuj1611/jenkins-pipeline-app.git`  
5. Branch: `*/main`  
6. Script Path: `Jenkinsfile`  
7. Save and click **Build Now**

---

## 📸 Jenkins Pipeline Stages

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
- Verified the pipeline locally by building and running Docker containers manually.  
- Understood end-to-end **DevOps workflow** from Code → Build → Deploy.

---

Happy Learning! 😊
