
# ✨ **GitHub Actions – DevOps**
![GitHub Actions GIF](githubaction.gif)

---

## 📌 **What is GitHub Actions?**

GitHub Actions is a **CI/CD automation tool** built directly into GitHub.
It helps developers **build, test, and deploy applications automatically** using simple YAML workflows stored in:

```
.github/workflows/
```

---

# 🚀 **CI / CD in GitHub Actions**

![GitHub Actions GIF](cicd.gif)

## 🔧 **CI – Continuous Integration**

Continuous Integration means:

* Code is automatically **built** when pushed
* Code is **tested** before merging
* Ensures no bugs enter the main branch
* Improves code quality

**Triggers used in GitHub Actions:**

```yaml
on: push
on: pull_request
```

---

## 🚚 **CD – Continuous Delivery**

Application is packaged, tested, and **kept ready for deployment**, but deployment requires **manual approval**.

Used when:

* Production deployment needs human check
* Stable release cycles

GitHub Actions supports approvals using **Environments → Required Reviewers**.

---

## ⚡ **CD – Continuous Deployment**

Fully **automatic deployment** without manual approval.

Used when:

* You want fast releases
* Microservices architecture
* Frequent deployments

Examples where GitHub Actions deploys automatically:

* AWS (ECS, Lambda, EC2, EKS)
* Azure
* GCP
* Kubernetes
* Docker Hub / GHCR
* Any server via SSH

---

# ⭐ **Importance of GitHub Actions in DevOps**

| Benefit                          | Why it matters                            |
| -------------------------------- | ----------------------------------------- |
| **Fully automated pipeline**     | Speeds up development                     |
| **Built into GitHub**            | No extra setup needed                     |
| **Supports all languages**       | Python, JS, Java, Go, Docker, etc.        |
| **Huge Marketplace**             | Reusable actions (AWS, Docker, Terraform) |
| **Fast execution**               | Parallel jobs for faster builds           |
| **Secure**                       | Secrets, access controls, environments    |
| **Perfect for DevOps workflows** | GitOps, IaC, testing, scanning            |

---

# 🔄 **Pipeline Flow – How GitHub Actions Works**

<p align="center"><b>Push → Build → Test → Package → Deploy → Notify</b></p>

### **1️⃣ Developer pushes code**

⬇

### **2️⃣ Workflow triggers automatically**

(pull request, push, schedule, manual trigger)
⬇

### **3️⃣ CI Stage**

* Install dependencies
* Build app
* Run tests
* Run code scans
  ⬇

### **4️⃣ Package Application**

* Docker image
* Zip release
* Build artifact
  ⬇

### **5️⃣ CD Stage**

* Deploy to cloud
* Manual approval (Delivery) or Auto (Deployment)
  ⬇

### **6️⃣ Notification**

GitHub → Email → Slack → Teams

---

# 🛠️ **Common Tools Used With GitHub Actions**

## 🧩 **1. Cloud Providers**

* AWS (ECS, Lambda, EC2, EKS, S3)
* Microsoft Azure
* Google Cloud Platform

## 🐳 **2. Containers & Orchestration**

* Docker
* Docker Hub / GHCR
* Kubernetes (EKS, AKS, GKE)
* Helm

## 🏗️ **3. Infrastructure as Code**

* Terraform
* Ansible
* AWS CloudFormation

## 🧪 **4. Testing Frameworks**

* PyTest
* Jest
* JUnit
* Selenium

## 🔐 **5. Security & Scanning**

* CodeQL
* Trivy
* Snyk

## 🚀 **6. Deployment Utilities**

* SSH
* Rsync
* GitHub Environments
* GitHub Secrets


---

# 📝 **Quick Revision Table**

| Topic               | Easy Definition                        |
| ------------------- | -------------------------------------- |
| **GitHub Actions**  | Automation tool inside GitHub          |
| **CI**              | Auto build + test code                 |
| **CD (Delivery)**   | Ready to deploy, needs manual approval |
| **CD (Deployment)** | Fully automatic deployment             |
| **Importance**      | Faster development + automation        |
| **Pipeline**        | Push → Build → Test → Deploy           |
| **Tools**           | Docker, AWS, Terraform, Kubernetes     |

---

