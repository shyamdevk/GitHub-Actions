
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

```yaml
name: Hello World

on: push

jobs:
  hello:
    runs-on: ubuntu-latest
    steps:
      - name: Say Hello
        run: echo "Hello World"
```
Use of `workflow_dispatch`:

---


`workflow_dispatch` allows you to **run a workflow manually**.

That means you can click a **button in GitHub Actions** and start the workflow whenever you want.

# 📘 Example

```yaml
on:
  workflow_dispatch:
```

---

## 📝 Explanation

| Part       | Meaning                                   |
| ---------- | ----------------------------------------- |
| `name`     | Workflow name                             |
| `on: push` | Runs whenever code is pushed              |
| `jobs`     | Group of tasks                            |
| `hello`    | Job name                                  |
| `runs-on`  | Uses Ubuntu runner (virtual machine)      |
| `steps`    | List of commands to run                   |
| `run`      | Executes a command (`echo "Hello World"`) |

---

# 🔧 **2. Job**

A **job** is a group of steps executed on a runner.

### Key Points:

* Each job runs on its own runner
* Jobs run in **parallel** unless `needs:` is used
* Contains multiple steps (commands/action calls)


## ✅ Example Job

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
```

---

## 📝 Simple Explanation 

| Part                        | Meaning                                            |
| --------------------------- | -------------------------------------------------- |
| `test`                      | Job name                                           |
| `runs-on: ubuntu-latest`    | Uses an Ubuntu runner (GitHub VM)                  |
| `steps`                     | Commands/actions inside the job                    |
| `- name: Checkout`          | Step name                                          |
| `uses: actions/checkout@v3` | Downloads your **repository code** into the runner |

---

## ⭐ Why `actions/checkout` is used?

* It **pulls your GitHub repo** into the runner machine.
* Without this, the runner **won’t have your project files**.
* Almost all workflows need this step.

---

# 🖥️ **3. Runners (Hosted & Self-Hosted)**
A **Runner** is a server or virtual machine where your workflow jobs actually execute. It's the compute environment that picks up jobs from GitHub Actions, runs the defined steps, and reports the results back to GitHub.
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

# 🧪 **Software Testing – DevOps**

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



# 📘 Simple CI/CD Pipeline using GitHub Actions

A beginner-friendly guide to understanding a very simple CI/CD pipeline using GitHub Actions.

---

## 🚀 Overview

This guide explains a **basic CI/CD workflow** that:

* Runs automatically when you push code
* Checks out your project
* Installs dependencies
* Runs tests
* Builds your project

Everything is kept **simple for freshers**.

---

## 📂 Workflow File Location

Create the file in the following path:

```
.github/workflows/simple-ci-cd.yml
```

---

## 🧪 Simple CI/CD Workflow (YAML)

```yaml
name: Simple CI-CD

on:
  push:
    branches: [ main ]
  pull_request:

jobs:
  build-and-test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test

      - name: Build project
        run: npm run build
```

---

# 📝 Step-by-Step Explanation (Beginner Friendly)

## 1️⃣ Workflow Name

```yaml
name: Simple CI-CD
```

This gives a **name** to your pipeline.
It appears in GitHub → Actions tab.

---

## 2️⃣ When Should the Workflow Run?

```yaml
on:
  push:
    branches: [ main ]
  pull_request:
```

Your pipeline runs when:
✔ Code is **pushed to main branch**
✔ A **pull request** is created

This is how CI (Continuous Integration) works.

---

## 3️⃣ Define Jobs

```yaml
jobs:
  build-and-test:
```

A **job** is like a container of tasks.
Here the job name is `build-and-test`.

---

## 4️⃣ Choose the Runner (Server)

```yaml
runs-on: ubuntu-latest
```

GitHub gives you a temporary virtual machine:
✔ Ubuntu OS
✔ Clean environment
✔ Auto-destroyed after pipeline finishes

---

## 5️⃣ CI/CD Steps

Steps run one after another.

---

### ✔ Step 1: Checkout Code

```yaml
- name: Checkout code
  uses: actions/checkout@v3
```

Downloads your repository into the workflow runner.

---

### ✔ Step 2: Setup Node.js

```yaml
- name: Setup Node.js
  uses: actions/setup-node@v3
  with:
    node-version: '18'
```

Installs **Node.js v18**.
Required for projects using JavaScript or Node.

---

### ✔ Step 3: Install Dependencies

```yaml
- name: Install dependencies
  run: npm install
```

Installs packages from your `package.json`.
Example: Express, React, Vue, etc.

---

### ✔ Step 4: Run Tests

```yaml
- name: Run tests
  run: npm test
```

Executes your tests.
Helps find bugs early before deployment.

---

### ✔ Step 5: Build the Project

```yaml
- name: Build project
  run: npm run build
```

Builds your application.
Example: React build folder, optimized JS, etc.

---

### **`uses:`** → tells GitHub Actions to run a **pre-built reusable action** created by GitHub or the community.

### **`actions:`** → refers to those reusable **automation tools** (like checkout, setup-node) that perform specific tasks inside a workflow.


# 🎯 What This CI/CD Pipeline Does

| Step                 | Purpose                         |
| -------------------- | ------------------------------- |
| Checkout             | Gets code from GitHub           |
| Setup Node.js        | Prepares environment            |
| Install Dependencies | Sets up project                 |
| Run Tests            | Ensures code is correct         |
| Build                | Creates production-ready output |

Perfect for freshers learning DevOps + GitHub Actions.

---

# 📘 GitHub Actions: Simple Workflow to Display an Image File

This guide explains how to:

* Create a GitHub repository
* Upload an image file
* Create a GitHub Actions workflow
* Use an Action (`actions/checkout`)
* Run `ls` to display the image in workflow logs

Perfect for **beginners** learning GitHub Actions.

---

## 🧰 Prerequisites

* A GitHub account
* Basic understanding of repository creation

---

# 🪜 Step 1: Create a GitHub Repository

1. Go to **[https://github.com](https://github.com)**
2. Click **New Repository**
3. Enter a name → example: `actions-image-demo`
4. Click **Create Repository**

---

# 🖼️ Step 2: Upload an Image File

1. Open your new repository
2. Click **Add file → Upload files**
3. Upload any image, for example: `myphoto.png`
4. Click **Commit changes**

Your repository now has the image.

---

# 📂 Step 3: Create the Workflow Folder

GitHub Actions workflows must be inside this path:

```
.github/workflows/
```

To create it:

1. Click **Add file → Create new file**
2. Name it exactly:

```
.github/workflows/simple-image-check.yml
```

---

# ⚙️ Step 4: Add the Workflow YAML

Paste the workflow below:

```yaml
name: Display Image File

on:
  push:
    branches: [ main ]

jobs:
  show-image:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3     # Downloads your repo + image file

      - name: List files in repo
        run: ls -l                    # Shows your image in workflow logs
```

Click **Commit changes**.

---

# ▶️ Step 5: Run and Verify the Workflow

1. Go to the **Actions** tab
2. Select your workflow: **Display Image File**
3. GitHub runs the workflow automatically
4. Open the job
5. Look at the **List files in repo** step

You will see output like:

```
-rw-r--r--   1 runner  staff   20480 Dec 8  myphoto.png
```

This confirms:

* The workflow ran
* `actions/checkout` downloaded the image
* `ls` displayed it

---

# 📝 Explanation of Key Parts

### **`uses: actions/checkout@v3`**

This action **downloads your entire repository** into the GitHub Actions runner, including your image file.

### **`run: ls -l`**

Runs a shell command that **lists all files**, showing the image in workflow logs.

---


