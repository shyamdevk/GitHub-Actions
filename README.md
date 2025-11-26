
# ✨ **GitHub Actions – DevOps**
![GitHub Actions](https://github.com/shyamdevk/GitHub-Actions/blob/image/githubaction.gif)

---

## 📌 **What is GitHub Actions?**

GitHub Actions is a **CI/CD automation tool** built directly into GitHub.
It helps developers **build, test, and deploy applications automatically** using simple YAML workflows stored in:

```
.github/workflows/
```

---
Here is your **fully structured, clean, decorated `README.md` section** for:

✔ Workflow
✔ Jobs
✔ Hosted & Self-Hosted Runners
✔ Event-Driven Triggers

Perfect to paste directly into your README.

---

# ⚙️ **GitHub Actions – Workflow, Jobs, Runners & Event Triggers**

<p align="center">
  <img src="https://skillicons.dev/icons?i=githubactions,git,github" height="80" />
</p>

---

## 📘 **1. Workflow**

A **workflow** is an automated process that runs inside GitHub Actions.

* Written in **YAML**
* Saved inside:

  ```
  .github/workflows/
  ```
* Used for CI, CD, testing, deployment, scanning, etc.

### **Example:**

```yaml
name: CI
on: push
jobs:
  build:
    runs-on: ubuntu-latest
```

---

# 🔧 **2. Job**

A **job** is a group of steps executed on a runner.

### Key Points:

* Each job runs on its own runner
* Jobs run in **parallel** unless `needs:` is used
* Contains multiple steps (commands/action calls)

### Example:

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
```

---

# 🖥️ **3. Runners (Hosted & Self-Hosted)**

## 🟦 **3.1 GitHub-Hosted Runner**

Fully managed machines provided by GitHub.

| Feature  | Details                                        |
| -------- | ---------------------------------------------- |
| OS       | ubuntu, windows, macOS                         |
| Setup    | No setup required                              |
| Tools    | Pre-installed: git, Docker, Node, Python, Java |
| Best For | Standard CI/CD automation                      |

### **Pros**

* No maintenance
* Fast
* Secure
* Ready-to-use

### **Cons**

* Limited free minutes
* No deep customization

---

## 🟩 **3.2 Self-Hosted Runner**

Your own machine that executes workflows.

| Feature       | Details                                        |
| ------------- | ---------------------------------------------- |
| Machine       | Your server, PC, VM, cloud instance            |
| Setup         | Must install GitHub runner manually            |
| Customization | Full root/admin control                        |
| Best For      | Heavy builds, private networks, custom tooling |

### **Pros**

* Unlimited runtime
* Full customization
* No GitHub minutes usage

### **Cons**

* You maintain OS/security
* More setup needed

---

# ⚡ **Hosted vs Self-Hosted (Comparison Table)**

| Feature       | GitHub-Hosted  | Self-Hosted                    |
| ------------- | -------------- | ------------------------------ |
| Setup         | Automatic      | Manual                         |
| Maintenance   | GitHub handles | You handle                     |
| Cost          | Free (limited) | Hardware cost                  |
| Customization | Low            | Full                           |
| Best Use      | Normal CI/CD   | Heavy workloads / custom tools |
| Security      | Managed        | Your responsibility            |

---

# 🔔 **4. Event-Driven Triggers (How Workflows Start)**

Workflows run automatically based on **GitHub events**.

---

## 📂 **4.1 Code-Based Triggers**

| Trigger        | When It Runs          |
| -------------- | --------------------- |
| `push`         | Code pushed to branch |
| `pull_request` | PR opened or updated  |
| `delete`       | Branch or tag deleted |

**Example:**

```yaml
on: push
```

---

## 🧑‍💻 **4.2 Manual Trigger**

Starts workflow manually from the GitHub UI.

```yaml
on:
  workflow_dispatch:
```

---

## ⏱️ **4.3 Scheduled Trigger (Cron Jobs)**

Runs at fixed times (daily, hourly, etc.)

```yaml
on:
  schedule:
    - cron: "0 0 * * *"   # runs daily at midnight
```

---

## 📦 **4.4 Repository Activity Triggers**

Triggered by GitHub activity:

| Event     | Description            |
| --------- | ---------------------- |
| `issues`  | Issue created/edited   |
| `release` | Release published      |
| `fork`    | Repo is forked         |
| `watch`   | Someone stars the repo |

---

## 🚀 **4.5 Deployment Triggers**

Used for CD pipelines.

| Event               | Description                 |
| ------------------- | --------------------------- |
| `deployment`        | Deployment request created  |
| `deployment_status` | Deployment succeeded/failed |

---

# 🔄 **Workflow → Job → Runner → Output Flow**

```
(Event Trigger)
        ↓
Workflow Starts
        ↓
Jobs Run (parallel or sequential)
        ↓
Runner Executes Steps
        ↓
Outputs (build, test, deploy)
```

---

# 🎯 **Summary Table**

| Concept            | Meaning                                    |
| ------------------ | ------------------------------------------ |
| **Workflow**       | Automation file that defines CI/CD         |
| **Job**            | Group of steps executed on a runner        |
| **Runner**         | Machine that executes job steps            |
| **GitHub-Hosted**  | Pre-configured GitHub machine              |
| **Self-Hosted**    | Your own custom machine                    |
| **Event Triggers** | Actions that start workflows automatically |

---

# 🚀 **CI / CD in GitHub Actions**

![GitHub Actions](https://github.com/shyamdevk/GitHub-Actions/blob/image/cicd.gif)

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

Here is your **well-structured, clean, decorated `README.md`** for **CI/CD Flow in DevOps** — formatted perfectly for GitHub.

You can copy-paste directly into your repo.

---

# ✨ **CI/CD Flow in DevOps — Complete Notes**

<p align="center">
  <img src="https://skillicons.dev/icons?i=githubactions,git,github,devops" height="85" />
</p>

---

## 📌 **Overview**

CI/CD (Continuous Integration & Continuous Delivery/Deployment) is the core practice in DevOps that automates **building**, **testing**, **releasing**, and **deploying** software reliably and quickly.

The flow follows the **DevOps Infinity Loop**, covering everything from planning to monitoring.

---

# 🔁 **DevOps Infinity Loop (CI/CD Phases)**
![GitHub Actions](https://github.com/shyamdevk/GitHub-Actions/blob/image/flow.gif)

<p align="center">
  <b>PLAN → CODE → BUILD → TEST → RELEASE → DEPLOY → OPERATE → MONITOR</b>
</p>

---

# 🔵 **1. CI – Continuous Integration (Left Side)**

CI focuses on improving code quality and preventing bugs before deployment.

### **1️⃣ PLAN**

* Understand requirements
* Break tasks into stories
* Prepare development roadmap

### **2️⃣ CODE**

* Developers write code
* Code is pushed to GitHub
* Version control using Git

### **3️⃣ BUILD**

* Compile application
* Install dependencies
* Create artifacts (Docker images, executables)

### **4️⃣ TEST**

* Automated tests run:

  * Unit tests
  * Integration tests
  * Security scanning
* Ensures no broken code reaches main branch

> ✅ **Goal of CI:** Early bug detection + stable codebase

---

# 🟠 **2. CD – Continuous Delivery / Deployment (Right Side)**

CD focuses on pushing ready code into production environments.

### **5️⃣ RELEASE**

* Generate production-ready artifacts
* Store Docker images / zip files
* Choose between Delivery (manual approval) or Deployment (automatic release)

### **6️⃣ DEPLOY**

* Deploy to cloud platforms:

  * AWS ECS / EC2 / EKS
  * Kubernetes
  * Azure
  * Google Cloud
* Can deploy using GitHub Actions, Terraform, ArgoCD, Jenkins

### **7️⃣ OPERATE**

* Application runs in production
* Handle traffic, logs, scaling
* Ensure availability and performance

### **8️⃣ MONITOR**

* Track metrics:

  * Latency
  * CPU/Memory
  * Errors
  * Crashes
* Tools like Prometheus, Grafana, CloudWatch

> ✅ **Goal of CD:** Fast, reliable, automated deployments

---

# 📦 **Complete CI/CD Pipeline Flow**

```
Developer Pushes Code
        ↓
Continuous Integration
(Build → Test → Scan)
        ↓
Create Production Artifact
        ↓
Continuous Delivery/Deployment
(Release → Deploy)
        ↓
App Runs in Production
        ↓
Monitor → Feedback → Plan
```

---

# 🎯 **Final Summary**

| Phase       | Description            |
| ----------- | ---------------------- |
| **Plan**    | Define what to build   |
| **Code**    | Write application code |
| **Build**   | Compile / package      |
| **Test**    | Ensure quality         |
| **Release** | Prepare for deployment |
| **Deploy**  | Push to cloud/servers  |
| **Operate** | Run app in production  |
| **Monitor** | Track performance      |

---


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
Here you go — **well-structured, clean, decorated `README.md` for TESTING ONLY**.
Simple, easy to understand, perfect for DevOps notes or GitHub documentation.

---

# 🧪 **Software Testing – DevOps Notes (Simple & Clear)**

![GitHub Actions](https://github.com/shyamdevk/GitHub-Actions/blob/image/test.gif)
<p align="center">
  <img src="https://skillicons.dev/icons?i=pytest,selenium,githubactions,git" height="80" />
</p>

---

## 📌 **What is Testing?**

Testing is the process of checking whether software is **free from defects**, works as expected, and meets requirements before it is released.

---

# 🎯 **Goal of Testing**

* Ensure software is **bug-free**
* Confirm features work as expected
* Improve reliability & performance
* Detect issues early (before production)
* Reduce failures, downtime, and customer issues

---

# 🧠 **Why Testing is Important in DevOps / CI**

| Benefit                 | Description                         |
| ----------------------- | ----------------------------------- |
| 🛡️ Early bug detection | Issues are caught before deployment |
| 🚀 Faster development   | Automated tests speed up delivery   |
| 🔒 More stable releases | Only tested code moves forward      |
| 📉 Reduced risk         | Prevents failures in production     |
| 🔄 Continuous feedback  | Devs get fast feedback on changes   |

---

# 🔍 **Types of Testing in DevOps**

| Test Type               | What It Checks                  | When Used              |
| ----------------------- | ------------------------------- | ---------------------- |
| **Unit Testing**        | Tests small modules/functions   | During CI, very early  |
| **Integration Testing** | Tests how modules interact      | After build            |
| **Functional Testing**  | Tests feature behaviour         | Before staging release |
| **End-to-End (E2E)**    | Simulates real user flow        | In staging/QA          |
| **Regression Testing**  | Ensures old features still work | Every build/test cycle |
| **Performance Testing** | Speed, load, stress             | Pre-production         |
| **Security Testing**    | Vulnerabilities, security gaps  | CI or CD               |
| **Acceptance (UAT)**    | Final business-level validation | Before production      |

---

# 🔄 **Where Testing Fits in CI/CD Pipeline**

```
PLAN → CODE → BUILD → TEST → RELEASE → DEPLOY → OPERATE → MONITOR
                     ↑
                (Testing Happens Here)
```

Tests are typically executed **immediately after the Build stage** and before Release.

---

# 🛠️ **Common Testing Tools**

| Category             | Tools                         |
| -------------------- | ----------------------------- |
| 🧪 Unit Testing      | PyTest, JUnit, Jest, Mocha    |
| 🔗 Integration / E2E | Selenium, Cypress, Playwright |
| 🔌 API Testing       | Postman, Newman, REST Assured |
| ⚡ Performance        | JMeter, Locust, k6            |
| 🔐 Security          | Snyk, Trivy, GitHub CodeQL    |

---

# 🧩 **Testing in GitHub Actions (CI)**

Most pipelines follow this structure:

### 1️⃣ Checkout Code

### 2️⃣ Install Dependencies

### 3️⃣ Run Unit Tests

### 4️⃣ Run Integration Tests

### 5️⃣ Stop Pipeline if Any Test Fails

Example:

```yaml
- name: Run Tests
  run: pytest
```

If tests fail → **CI fails** → code cannot be merged.

---


