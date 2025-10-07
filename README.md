# 🚀 Flask Application with CI/CD using Jenkins and Docker

This project demonstrates a **complete CI/CD pipeline** for deploying a Flask application using **Jenkins**, **Docker**, and **GitHub**.
It automates the process of building and deploying the app whenever new code is pushed to the main branch.

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

1. Developer pushes new code to **GitHub main branch**.
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

## 🌐 Optional: Setup GitHub Webhook

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
