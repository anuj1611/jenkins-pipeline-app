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
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/24695b86-a6c0-4b66-9459-f218080a46b1" />


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

<img width="1191" height="217" alt="image" src="https://github.com/user-attachments/assets/5ef74c5c-08c4-4965-87a9-e34436862f01" />
<img width="885" height="373" alt="image" src="https://github.com/user-attachments/assets/ffb5b45e-58fd-4c01-b8c5-8578128b09dd" />



---

## Build, Run & Test Locally (Manual Verification)

These steps let you verify the Docker image and container locally before relying on Jenkins.

### 1. Build the Docker image
```bash
docker build -t jenkins-pipeline-app .
```
**Expected result:** Docker builds the image and tags it as `jenkins-pipeline-app`.
<img width="1510" height="752" alt="image" src="https://github.com/user-attachments/assets/c6dc7e6f-0c68-4a1c-97cc-c425f5eca756" />


### 2. Run the Docker container
```bash
docker run -d -p 5000:5000 --name flask-container jenkins-pipeline-app
```
**What this does:** Runs the container in detached mode, maps container port `5000` to host port `5000`, and names the container `flask-container`.
<img width="1021" height="62" alt="image" src="https://github.com/user-attachments/assets/75d5085d-8159-48d6-9e47-46e57a0f2ae0" />


### 3. Verify the container is running
```bash
docker ps
```
You should see `flask-container` listed. 
<img width="1281" height="59" alt="image" src="https://github.com/user-attachments/assets/6afe2a2f-c2be-4883-aa14-57e6a0baa980" />



### 4. Test the application
Open your browser and visit:  
```
http://localhost:5000
```
<img width="1919" height="967" alt="Screenshot 2025-10-07 194110" src="https://github.com/user-attachments/assets/d14f08ec-f56d-4f5b-8f0e-660faa33212c" />

---
Expected response:  
```
Hello from Jenkins CI/CD Pipeline 
```

### 5. Stop & Remove the container (cleanup)
```bash
docker rm -f flask-container
```
<img width="1397" height="263" alt="image" src="https://github.com/user-attachments/assets/d377aea0-ffe4-4c8d-92bc-0cb0570490c6" />

---


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
<img width="1919" height="1035" alt="Screenshot 2025-10-07 181707" src="https://github.com/user-attachments/assets/36c6d442-5e1d-4781-9ce8-a2b9526e97fc" />


---

## Jenkins Pipeline Stages

| Stage | Description |
|--------|--------------|
| **Checkout** | Pulls latest code from GitHub |
| **Build Docker Image** | Builds image using Dockerfile |
| **Deploy Container** | Runs Flask app in a Docker container |

---
<img width="1919" height="1032" alt="Screenshot 2025-10-07 181542" src="https://github.com/user-attachments/assets/ee571c24-d4de-4e75-b2b4-01adb835a747" />

---


## Learning Outcomes

- Built a working **CI/CD pipeline** using Jenkins.  
- Automated Flask app deployment using Docker.  
- Configured Jenkins with **Git SCM**.  
- Verified the pipeline locally by building and running Docker containers manually.  
- Understood end-to-end **DevOps workflow** from Code → Build → Deploy.

---

Happy Learning! 😊
