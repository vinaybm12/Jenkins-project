# 🚀 Static Website Deployment using Jenkins CI/CD Pipeline on AWS EC2 with Nginx

## 📌 Project Overview

This project demonstrates the implementation of a Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins to automate the deployment of a static website hosted on an Amazon EC2 instance running Ubuntu and Nginx.

The objective of this project is to eliminate manual deployment processes and establish an automated workflow where every code change pushed to GitHub is deployed seamlessly to the web server through Jenkins.

---

## 🏗️ Solution Architecture

```text
Developer
    │
    ▼
GitHub Repository
    │
    ▼
Jenkins Pipeline
    │
    ▼
AWS EC2 (Ubuntu)
    │
    ▼
Nginx Web Server
    │
    ▼
Live Static Website
```

---

## 🎯 Project Objectives

* Automate website deployment using Jenkins.
* Integrate GitHub with Jenkins for source code management.
* Deploy application files to an AWS EC2 instance.
* Host the website using Nginx.
* Implement DevOps best practices for continuous delivery.

---

## 🛠️ Technology Stack

| Technology    | Purpose                 |
| ------------- | ----------------------- |
| GitHub        | Source Code Repository  |
| Jenkins       | CI/CD Automation Server |
| AWS EC2       | Compute Infrastructure  |
| Ubuntu Server | Operating System        |
| Nginx         | Web Server              |
| Git           | Version Control         |
| Shell Script  | Deployment Automation   |

---

## 📂 Repository Structure

```text
Jenkins-project/
│
├── index.html
├── css/
├── js/
├── images/
├── Jenkinsfile
└── README.md
```

---

## ⚙️ Infrastructure Configuration

### AWS EC2 Instance

| Configuration    | Value  |
| ---------------- | ------ |
| Cloud Provider   | AWS    |
| Service          | EC2    |
| Operating System | Ubuntu |
| Web Server       | Nginx  |

### Jenkins Server

Jenkins is configured to:

* Pull source code from GitHub.
* Execute deployment pipeline stages.
* Deploy website files to the target server.
* Restart Nginx services when required.

---

## 🔄 CI/CD Workflow

### 1. Code Commit

Developers push code changes to the GitHub repository.

### 2. Source Code Checkout

Jenkins fetches the latest code from the repository.

### 3. Build & Validation

Pipeline validates the project structure and prepares deployment artifacts.

### 4. Deployment

Static website files are copied to the Nginx web root directory.

```bash
/var/www/html
```

### 5. Website Publication

Nginx serves the latest version of the website to end users.

---

## 📜 Jenkins Pipeline

The Jenkins pipeline automates the deployment process by performing the following tasks:

* Checkout Source Code
* Validate Deployment Files
* Deploy to Target Server
* Verify Deployment Status

Example Pipeline:

```groovy
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/vinaybm12/Jenkins-project.git'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo cp -r * /var/www/html/
                '''
            }
        }

        stage('Verify') {
            steps {
                sh 'systemctl status nginx'
            }
        }
    }
}
```

---

## 🌐 Nginx Configuration

Install Nginx:

```bash
sudo apt update
sudo apt install nginx -y
```

Verify Service Status:

```bash
sudo systemctl status nginx
```

Start Nginx:

```bash
sudo systemctl start nginx
```

Enable Nginx at Boot:

```bash
sudo systemctl enable nginx
```

Restart Nginx:

```bash
sudo systemctl restart nginx
```

---

## 🚀 Deployment Process

### Clone Repository

```bash
git clone https://github.com/vinaybm12/Jenkins-project.git
```

### Configure Jenkins Job

1. Create a Jenkins Pipeline Job.
2. Connect the GitHub repository.
3. Configure SCM settings.
4. Add Jenkinsfile configuration.
5. Trigger the build.

### Execute Pipeline

Run the pipeline manually or configure GitHub Webhooks for automatic deployments.

---

## 📈 Benefits of This Implementation

✅ Automated Deployments

✅ Faster Release Cycles

✅ Reduced Manual Errors

✅ Consistent Deployment Process

✅ Improved Reliability

✅ Enhanced DevOps Workflow

---

## 🔐 Future Enhancements

* Configure GitHub Webhooks for automatic triggers.
* Implement SSH-based deployment.
* Integrate Docker containers.
* Add SonarQube code quality analysis.
* Implement Blue-Green Deployments.
* Add Monitoring using Prometheus and Grafana.
* Configure SSL/TLS using Let's Encrypt.

---

## 📸 Project Demonstration

The deployment pipeline automatically updates the live website whenever changes are pushed to the GitHub repository, ensuring rapid and reliable delivery.

---

## 👨‍💻 Author

### Vinay B M

DevOps Engineer | Cloud Enthusiast | Automation Advocate

**GitHub Repository:**
https://github.com/vinaybm12/Jenkins-project

---

## 📝 Conclusion

This project showcases a practical implementation of CI/CD principles using Jenkins, AWS EC2, Ubuntu, and Nginx. It demonstrates how automation can streamline deployment workflows, reduce operational overhead, and improve software delivery efficiency.

The solution serves as a foundational DevOps project and can be extended further with containerization, infrastructure as code, monitoring, and advanced deployment strategies.
