# 🚀 Weekly Assessment - Jenkins Multi-Stage CI/CD Pipeline

## 📌 Project Overview

This project demonstrates a complete CI/CD workflow using Jenkins, GitHub, Docker-based Jenkins setup, and GitHub webhooks.

The pipeline is fully automated and triggers automatically whenever code is pushed to the GitHub repository.

---

# 🎯 Objective

Create a multi-stage Jenkins pipeline with the following stages:

- Checkout
- Build
- Test
- Deploy

Integrate GitHub webhook to automatically trigger the pipeline on every commit.

---

# 🛠 Technologies Used

- Ubuntu
- Jenkins (Docker)
- Git & GitHub
- ngrok
- Jenkins Pipeline (Declarative)
- Bash Shell

---

# 📂 Project Structure

```text
weekly-assessment-jenkins-pipeline/
│
├── Jenkinsfile
├── README.md
│
├── app/
│   ├── index.html
│   └── style.css
│
└── screenshots/
```

---

# 🌐 Mini Web Application

A simple static website was created to demonstrate the CI/CD pipeline workflow.

Files:
- `index.html`
- `style.css`

The application is used during:
- Build verification
- Testing
- Deployment simulation

---

# ⚙️ Jenkins Pipeline Workflow

```text
Git Push
   ↓
GitHub Webhook
   ↓
ngrok Tunnel
   ↓
Jenkins Trigger
   ↓
Checkout Stage
   ↓
Build Stage
   ↓
Test Stage
   ↓
Deploy Stage
   ↓
Pipeline Success 🚀
```

---

# 🧩 Pipeline Stages and Purpose

## 1️⃣ Checkout Stage

### Purpose
Fetch latest code from GitHub repository.

### What Happens
Jenkins connects to GitHub and pulls the latest project files.

---

## 2️⃣ Build Stage

### Purpose
Verify project structure and prepare application.

### What Happens
The pipeline checks whether required application files exist.

Example:
- `index.html`

If files are missing, pipeline fails.

---

## 3️⃣ Test Stage

### Purpose
Validate application content.

### What Happens
Pipeline checks if expected text/content exists in the application files.

If validation fails:
- Pipeline stops automatically.

---

## 4️⃣ Deploy Stage

### Purpose
Simulate deployment process.

### What Happens
Application files are copied into deployment directory.

This represents how applications are deployed in real DevOps workflows.

---

# 🔥 Jenkinsfile

```groovy
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo '📥 Cloning repository from GitHub...'
            }
        }

        stage('Build') {
            steps {
                echo '🔨 Building application...'

                sh '''
                if [ -f app/index.html ]; then
                    echo "Build Successful: index.html found"
                else
                    echo "Build Failed"
                    exit 1
                fi
                '''
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests...'

                sh '''
                grep "Jenkins CI/CD Pipeline Working Successfully" app/index.html
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying application...'

                sh '''
                mkdir -p deployment
                cp -r app/* deployment/
                echo "Deployment Successful"
                '''
            }
        }
    }
}
```

---

# 🔗 GitHub Webhook Integration

GitHub webhooks were configured using ngrok to expose the local Jenkins server publicly.

Whenever code is pushed:
1. GitHub sends webhook event
2. Jenkins receives trigger
3. Pipeline starts automatically

---

# 📸 Evidence

The `screenshots/` folder contains:

- Jenkins pipeline configuration
- ngrok setup
- GitHub webhook setup
- Pipeline stage view
- Automatic build trigger
- Successful console output

---

# ✅ Final Outcome

Successfully created a fully automated Jenkins CI/CD pipeline with:

- Multi-stage pipeline
- Jenkinsfile (Pipeline as Code)
- GitHub integration
- Webhook automation
- Build/Test/Deploy workflow

---

# 👩‍💻 Author
Arsh E Noor
DevOps Internship - Week 1 Assessment  
Jenkins CI/CD Pipeline Project