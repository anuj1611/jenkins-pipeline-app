# 🚀 Flask Application with CI/CD using Jenkins and Docker

This project demonstrates a **complete CI/CD pipeline** for deploying a Flask application using **Jenkins**, **Docker**, and **GitHub**.
It automates the process of building and deploying the app whenever new code is pushed to the `main` branch.

---

## 🧩 Project Overview

- **Application** → Python Flask web app.
- **Containerization** → Dockerized Flask app.
- **Automation Tool** → Jenkins (Declarative Pipeline).
- **Source Control** → Git & GitHub.
- **Trigger Mechanism** → Manual build or GitHub Webhook.

The goal is to achieve a continuous integration and continuous deployment (CI/CD) workflow where every code change is automatically built and deployed inside a Docker container using Jenkins.

---

## ⚙️ Tools & Technologies Used

| Category | Tool |
|-----------|------|
| **Language** | Python 3.10 |
| **Framework** | Flask |
| **Containerization** | Docker Desktop |
| **CI/CD Automation** | Jenkins |
| **Version Control** | Git & GitHub |
| **Build Trigger (Optional)** | GitHub Webhook |
| **Operating System** | Windows 10/11 |

---

## 🧠 CI/CD Pipeline Summary

1. Developer pushes new code to **GitHub `main` branch**.
2. **Jenkins** fetches the latest code (via Git SCM or webhook trigger).
3. The Jenkins pipeline automatically:
   - Clones the repository.
   - Builds a **Docker image**.
   - Deploys the Flask container.
4. Application becomes accessible locally at **http://localhost:5000**.

---

## 🗂️ Project Structure

```
flask-jenkins-pipeline/
│-- app.py
│-- requirements.txt
│-- Dockerfile
│-- Jenkinsfile
```

---

## 🔁 Push Code to GitHub (Required before CI runs)

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
git commit -m "Initial commit: add Flask app, Dockerfile, Jenkinsfile"

# push to GitHub
git push -u origin main
```

> ✅ After pushing, Jenkins (configured with your repo) can pull the `main` branch and execute the `Jenkinsfile` pipeline.

---

## 🐳 Build, Run & Test Locally (Manual Verification)

These steps let you verify the Docker image and container locally before relying on Jenkins.

### 1. Build the Docker image
```bash
docker build -t Jenkins-pipeline-app .
```
**Expected result:** Docker builds the image and tags it as `Jenkins-pipeline-app`.

### 2. Run the Docker container
```bash
docker run -d -p 5000:5000 --name flask-container Jenkins-pipeline-app
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
Hello from Jenkins CI/CD Pipeline 🚀
```

### 5. Stop & Remove the container (cleanup)
```bash
docker rm -f flask-container
```

---

## ⚡ Jenkins Setup

### Step 1️⃣ — Install Prerequisites
- **Java 21**
- **Jenkins (LTS)**
- **Docker Desktop**

### Step 2️⃣ — Install Jenkins Plugins
- Git Plugin
- Pipeline Plugin
- Docker Pipeline Plugin
- Blue Ocean (optional)

### Step 3️⃣ — Create a Pipeline Job
1. Jenkins Dashboard → **New Item → Pipeline**  
2. Name it `flask-pipeline`  
3. Under **Pipeline Definition**, choose **Pipeline script from SCM**  
4. Select **Git** and add the repository URL:  
   `https://github.com/anuj1611/jenkins-pipeline-app.git`  
5. Branch: `*/main`  
6. Script Path: `Jenkinsfile`  
7. Save and click **Build Now**

---

## 🌐 Optional: Setup GitHub Webhook (Auto-Trigger)

To automatically trigger Jenkins builds when code is pushed:

1. In your GitHub repo → **Settings → Webhooks → Add Webhook**  
2. **Payload URL:** `http://<your-machine-ip>:8080/github-webhook/`  
3. **Content type:** `application/json`  
4. Select **Just the push event**  
5. Click **Add Webhook**

Now every code push automatically triggers Jenkins to build and deploy.

---

## 📸 Jenkins Pipeline Stages

| Stage | Description |
|--------|--------------|
| **Checkout** | Pulls latest code from GitHub |
| **Build Docker Image** | Builds image using Dockerfile |
| **Deploy Container** | Runs Flask app in a Docker container |

---

## 🎯 Learning Outcomes

- Built a working **CI/CD pipeline** using Jenkins.  
- Automated Flask app deployment using Docker.  
- Configured Jenkins with **Git SCM** and **Webhooks**.  
- Verified the pipeline locally by building and running Docker containers manually.  
- Understood end-to-end **DevOps workflow** from Code → Build → Deploy.

---

## 🧑‍💻 Author

**Anuj Dhiraj Bhagat**  
🎓 B.Tech - Electronics and Computer Science  
📧 your.email@example.com  
🔗 [LinkedIn Profile or Portfolio Link]

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).
