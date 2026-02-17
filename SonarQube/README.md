## 📘 SonarQube in GitHub Actions

![Image](https://media.licdn.com/dms/image/v2/D4E12AQEdnHEcn-jP9w/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1700936838542?e=2147483647\&t=6OViaARKoA7NNIW3_dKtSI0_jJA-0u9SHs7-ut8SO6A\&v=beta)

![Image](https://gofore.com/media/2022/11/sonar_code-quality-metrics_overview_2019-04-1.png)

![Image](https://d2908q01vomqb2.cloudfront.net/7719a1c782a1ba91c031a682a0a2f8658209adbf/2022/03/27/1-ArchitectureDiagram.png)

![GitHub Actions](https://github.com/shyamdevk/GitHub-Actions/blob/image/sonar.gif)

---

## 🔍 What is SonarQube?

**SonarQube** is a **code quality and security analysis tool**.
It scans source code and finds:

* 🐞 Bugs
* 🔐 Security vulnerabilities
* 🧹 Code smells (bad coding practices)

👉 It works **without running the code** (this is called *static code analysis*).

---

## ⚙️ What is GitHub Actions?

**GitHub Actions** is a **CI/CD automation tool** inside GitHub.
It runs workflows written in `.yml` files when:

* Code is pushed
* A pull request is created

---

## 🔗 Why use SonarQube with GitHub Actions?

Using SonarQube in GitHub Actions helps to:

* Automatically check **code quality**
* Detect **security issues early**
* Maintain **clean and professional code**
* Block bad code using **Quality Gates**

**Simple idea:**

> Push code → GitHub Actions runs → SonarQube scans → Report is generated

---

## 🔄 How It Works (Flow)

1. Developer pushes code to GitHub
2. GitHub Actions workflow starts
3. SonarQube Scanner analyzes the code
4. Results are sent to SonarQube dashboard
5. Quality Gate decides **Pass ✅ or Fail ❌**

---

## 🛑 What Issues Does SonarQube Detect?

* Hardcoded passwords or secrets
* Unused variables and dead code
* Duplicate code blocks
* Security risks like SQL Injection, XSS

---

## 🧠 Important Terms (Easy)

* **Static Code Analysis** → Checking code without execution
* **Quality Gate** → Rules to allow or block code
* **Sonar Token** → Secret key to connect GitHub with SonarQube

---

## ☁️ Where Can SonarQube Run?

* **SonarQube Cloud** (recommended for beginners)
* **Self-hosted SonarQube** (EC2 / on-prem server)

---

## ⭐ One-Line Summary

> **SonarQube in GitHub Actions automatically checks code quality and security in a CI/CD pipeline.**


# 🔍 SonarQube Code Quality Analysis using GitHub Actions (EC2 Based)

---

## 📌 Lab Overview

This lab demonstrates how to integrate **SonarQube** with **GitHub Actions** to perform **static code analysis** on a GitHub repository.

🔹 SonarQube is hosted on an **AWS EC2 instance**
🔹 GitHub Actions automatically scans code on every push
🔹 **No ngrok is used** — EC2 public IP is used directly

---

## 🎯 What You Will Learn

* How to install and run SonarQube on an EC2 instance
* How to create a SonarQube project and token
* How to connect GitHub Actions with SonarQube
* How to view code quality reports and Quality Gates

---

## 🧱 Architecture (Simple)

1. Developer pushes code to GitHub
2. GitHub Actions workflow starts
3. SonarQube Scanner sends code to SonarQube (EC2)
4. SonarQube analyzes code and generates reports
5. Results are shown in SonarQube dashboard

---

## 🖥️ Prerequisites

* AWS account
* Ubuntu EC2 instance
* GitHub repository
* Basic knowledge of Git & Docker

---

## 1️⃣ Launch EC2 Instance

1. Go to **AWS Console → EC2 → Launch Instance**
2. AMI: **Ubuntu 22.04 LTS**
3. Instance type: `t2.micro` (minimum)
4. Security Group:

   * TCP **22** → SSH
   * TCP **9000** → SonarQube UI
5. Launch instance and connect via SSH

---

## 2️⃣ Install Docker on EC2

```bash
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

Verify:

```bash
docker --version
```

---

## 3️⃣ Run SonarQube on EC2 (UPDATED – docker run method)

### 🔹 Pull SonarQube Image

```bash
sudo docker pull sonarqube:latest
```

### 🔹 Run SonarQube Container

```bash
sudo docker run -d \
  --name sonarqube \
  -p 9000:9000 \
  sonarqube
```

### 🔹 Required System Setting (IMPORTANT)

```bash
sudo sysctl -w vm.max_map_count=262144
sudo docker restart sonarqube
```

### 🔹 Verify Container

```bash
sudo docker ps
```

---

## 4️⃣ Access SonarQube Dashboard

Open browser:

```
http://<EC2_PUBLIC_IP>:9000
```

Default login:

```
Username: admin
Password: admin
```

(Change password when prompted)

---

## 5️⃣ Create SonarQube Project

1. Go to **Projects → Create Project**
2. Enter:

   * Project Name
   * Project Key
3. Choose **Manually**
4. Generate **Sonar Token**
5. 📌 Copy and save the token securely

---

## 6️⃣ Configure GitHub Secrets

In your GitHub repository:

**Settings → Secrets and variables → Actions**

Add:

* `SONAR_HOST_URL` = `http://<EC2_PUBLIC_IP>:9000`
* `SONAR_TOKEN` = `<generated_token>`

---

## 7️⃣ Add GitHub Actions Workflow

Create file:

```
.github/workflows/sonarqube.yml
```

```yaml
name: SonarQube Scan

on:
  push:
    branches: [ main ]
  pull_request:

jobs:
  sonar:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v4
      with:
        fetch-depth: 0

    - name: Set up Java
      uses: actions/setup-java@v3
      with:
        distribution: temurin
        java-version: '17'

    - name: SonarQube Scan
      uses: sonarsource/sonarqube-scan-action@v2
      env:
        SONAR_HOST_URL: ${{ secrets.SONAR_HOST_URL }}
        SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
```

---

## 8️⃣ Push Code to GitHub

```bash
git add .
git commit -m "Add SonarQube GitHub Actions workflow"
git push
```

Go to **GitHub → Actions tab** to see the workflow running.

---

## 9️⃣ View Analysis Results

1. Open SonarQube Dashboard
2. Select your project
3. View:

   * Bugs
   * Vulnerabilities
   * Code Smells
   * Quality Gate status

---

## 🧠 Key Concepts (Easy)

* **Static Code Analysis** → Code is analyzed without execution
* **Quality Gate** → Pass/Fail rules for code quality
* **Sonar Token** → Secure authentication between GitHub & SonarQube

---

## 🆚 Why `docker run` Instead of docker-compose?

* Easier for beginners
* Fewer dependencies
* Perfect for labs and interviews
* No docker-compose installation issues on EC2

---

## ⭐ One-Line Summary

> This lab integrates SonarQube running on an EC2 instance with GitHub Actions to perform automated static code analysis on every code push.

---

## ✅ Lab Status

✔ EC2-based SonarQube
✔ No ngrok used
✔ Beginner-friendly
✔ Interview-ready

---
