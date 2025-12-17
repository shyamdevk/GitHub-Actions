
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
---

## 🔗 Apache Maven – Basics & Hands-on Lab
### 👉 GitHub Repository:
🔹 **Apache Maven Basics & Lab**  
🔗 https://github.com/shyamdevk/Apache-Maven.git

---

---

# 🚀 GitHub CI/CD Self-Hosted Runner Lab

## 📌 Overview
This lab demonstrates how to set up a **CI/CD pipeline using a GitHub Self-Hosted Runner**.  
Instead of using GitHub’s default runners, the workflow runs on **your own system (local machine / VM / EC2)**.

## 🎯 Objectives
By completing this lab, you will:
- Understand what a **self-hosted runner** is
- Configure a self-hosted runner in GitHub
- Execute a CI/CD workflow on your own system
- Verify pipeline execution using GitHub Actions logs

---

## 🛠 Tools & Technologies
- **GitHub**
- **GitHub Actions**
- **Self-Hosted Runner**
- **Linux System / VM / EC2**
- **Shell Commands**

---

## 🧩 Lab Architecture (Simple View)

```

Developer (You)
    |
    v
GitHub Repository
    |
    v
GitHub Actions Workflow
    |
    v
Self-Hosted Runner (Your System)

```

---

## 📁 Repository Structure

```

self-hosted-ci-lab/
├── README.md
└── .github/
└── workflows/
└── self-hosted.yml

```

---

## 🚀 Step 1: Create GitHub Repository

1. Login to **GitHub**
2. Click **New Repository**
3. Repository name:
```

self-hosted-ci-lab

````
4. ✅ Select **Add README.md**
5. Click **Create Repository**

✔ Repository created successfully

---

## 🚀 Step 2: Open Self-Hosted Runner Settings

1. Open your repository
2. Go to **Settings**
3. Navigate to **Actions → Runners**
4. Click **New self-hosted runner**

GitHub will now show setup instructions.

---

## 🚀 Step 3: Choose Runner Platform

- Operating System: **Linux**
- Architecture: **x64**

> Linux is commonly used in real DevOps environments.

---

## 🚀 Step 4: Download Runner on Your System

Run the following commands on your Linux system:

### Create a directory
```bash
mkdir actions-runner
cd actions-runner
````

### Download runner package

```bash
curl -o actions-runner-linux-x64-2.317.0.tar.gz \
https://github.com/actions/runner/releases/download/v2.317.0/actions-runner-linux-x64-2.317.0.tar.gz
```

### Extract the package

```bash
tar xzf actions-runner-linux-x64-2.317.0.tar.gz
```

✔ Runner files downloaded successfully

---

## 🚀 Step 5: Configure the Runner

GitHub provides a configuration command similar to:

```bash
./config.sh --url https://github.com/<your-username>/self-hosted-ci-lab --token <TOKEN>
```

### During configuration:

* Runner name → Press **Enter**
* Work folder → Press **Enter**
* Labels → Press **Enter**

✔ Your system is now linked to the GitHub repository

---

## 🚀 Step 6: Start the Runner

Run:

```bash
./run.sh
```

⚠️ **Important**

* Keep this terminal **open**
* Closing it will stop the runner

### Verify runner status:

* GitHub → **Settings → Actions → Runners**
* Status should show **Idle (green)**

---

## 🚀 Step 7: Create CI/CD Workflow

1. In your repository, click **Add file → Create new file**

2. File name:

   ```
   .github/workflows/self-hosted.yml
   ```

3. Paste the following workflow:

```yaml
name: Self-Hosted CI/CD Lab

on:
  push:
    branches: [ "main" ]

jobs:
  demo-job:
    runs-on: self-hosted

    steps:
    - name: Print welcome message
      run: echo "Hello from Self-Hosted Runner!"

    - name: Show system information
      run: |
        uname -a
        whoami
        pwd
```

4. Click **Commit new file**

---

## 🚀 Step 8: Trigger the Pipeline

* Any commit to `main` triggers the workflow
* Go to **Actions** tab
* Open the latest workflow run

✔ Job executes on your **self-hosted runner**

---

## 📊 Expected Output (Verification)

You should see logs like:

```
Hello from Self-Hosted Runner!
Linux ip-172-31-xx-xx ...
runner
/home/runner/actions-runner
```

✅ This confirms:

* Pipeline executed successfully
* Job ran on **your system**
* Self-hosted runner is working

---

## 🧠 Important Notes

* Runner works only when your system is **ON**
* Internet connection is required
* Used widely in real-world DevOps environments

---

## ✅ Result

✔ Self-hosted runner configured
✔ CI/CD workflow executed
✔ Output verified in GitHub Actions

---

## 🎯 Conclusion

This lab demonstrates how to configure and use a **GitHub Self-Hosted Runner** to execute CI/CD workflows on a user-managed system. It provides hands-on experience with real-world DevOps practices and GitHub Actions.

---

# 📧 CI/CD Email Notifications using AWS SES & GitHub Actions (OIDC)

![AWS](https://img.shields.io/badge/AWS-SES-orange)
![GitHub Actions](https://img.shields.io/badge/GitHub-Actions-blue)
![Security](https://img.shields.io/badge/Auth-OIDC-green)

---

## 🧪 Lab Title

**Integrate AWS SES with GitHub Actions CI/CD Pipeline using OIDC Authentication**

---

## 🎯 Lab Objective

This lab demonstrates how to **send email notifications using AWS Simple Email Service (SES)** when a **GitHub Actions workflow succeeds or fails**, using **OIDC (OpenID Connect)** for secure authentication **without storing AWS access keys**.

---

## 🧠 What You Will Learn

* Verify email identities in **AWS SES**
* Configure **GitHub → AWS authentication** using OIDC
* Create an **IAM Role for GitHub Actions**
* Send **Success & Failure emails** from CI/CD pipeline
* Implement **secure, production-ready CI/CD**

---

## 🏗️ Architecture Overview

<p align="center">
  <img src="https://github.com/shyamdevk/GitHub-Actions/blob/image/ses.png" 
       alt="GitHub Actions SES Flow Diagram" 
       width="450"/>
</p>
---

## 📌 Prerequisites

* AWS Account
* GitHub Account
* AWS SES Region: **us-east-1**
* GitHub Repository with `main` branch

---

## 🔹 STEP 1: Verify Email Identities in AWS SES

1. Open **AWS Console → Simple Email Service (SES)**
2. Ensure region is **us-east-1**
3. Go to **Identities → Create identity**
4. Select **Email address**
5. Add **Sender Email ID** and verify it
6. Repeat the same steps for **Receiver Email ID**

⚠️ **Note:**
If SES is in **Sandbox mode**, **both sender and receiver emails must be verified**.

---

## 🔹 STEP 2: Create OIDC Identity Provider for GitHub

1. Go to **AWS IAM → Identity providers**
2. Click **Add provider**
3. Configure as follows:

| Setting       | Value                                         |
| ------------- | --------------------------------------------- |
| Provider type | OpenID Connect                                |
| Provider URL  | `https://token.actions.githubusercontent.com` |
| Audience      | `sts.amazonaws.com`                           |

4. Click **Add provider**

---

## 🔹 STEP 3: Create IAM Role for GitHub Actions

1. Go to **IAM → Roles → Create role**

2. Select **Web identity**

3. Choose:

   * Identity provider: **GitHub**
   * Audience: **sts.amazonaws.com**

4. Repository condition:

```
repo:YOUR_GITHUB_USERNAME/YOUR_REPOSITORY_NAME:*
```

5. Attach this **SES permissions policy**:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ses:SendEmail",
        "ses:SendRawEmail"
      ],
      "Resource": "*"
    }
  ]
}
```

6. Name the role:

```
GitHub-SES
```

7. Copy the **Role ARN** (used in GitHub Actions)

---

## 🔹 STEP 4: Create GitHub Repository

* Create a new GitHub repository
* Ensure default branch is **main**

---

## 🔹 STEP 5: Add GitHub Actions Workflow

Create the file:

```
.github/workflows/ses-ci.yml
```

### 📄 Workflow Code

```yaml
name: CI with AWS SES Email (OIDC)

on:
  push:
    branches:
      - main
  workflow_dispatch:

permissions:
  id-token: write
  contents: read

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v4
        with:
          role-to-assume: arn:aws:iam::526888234336:role/GitHub-SES
          aws-region: us-east-1

      - name: Run build
        run: |
          echo "Running build..."
          echo "Build completed successfully"
          # Uncomment below line to test failure email
          # exit 1

      - name: Send Email Notification (Success)
        if: success()
        run: |
          aws ses send-email \
            --from "shyamdevk677@gmail.com" \
            --destination "ToAddresses=novagaming677@gmail.com" \
            --message "Subject={Data='✅ Build Success'},Body={Text={Data='CI build for ${{ github.repository }} succeeded.\nBranch: ${{ github.ref_name }}\nCommit: ${{ github.sha }}\nRun URL: ${{ github.server_url }}/${{ github.repository }}/actions/runs/${{ github.run_id }}'}}" \
            --region us-east-1

      - name: Send Email Notification (Failure)
        if: failure()
        run: |
          aws ses send-email \
            --from "shyamdevk677@gmail.com" \
            --destination "ToAddresses=novagaming677@gmail.com" \
            --message "Subject={Data='❌ Build Failed'},Body={Text={Data='CI build FAILED for ${{ github.repository }}.\nBranch: ${{ github.ref_name }}\nCommit: ${{ github.sha }}\nLogs: ${{ github.server_url }}/${{ github.repository }}/actions/runs/${{ github.run_id }}'}}" \
            --region us-east-1
```

---

## 🧪 STEP 6: Test the Workflow

### ✔ Success Email Test

* Push any commit to `main`
* Workflow succeeds
* **Success email received**

### ❌ Failure Email Test

* Uncomment `exit 1`
* Push again
* **Failure email received**

---

## 🔐 Security Best Practices Used

* No AWS access keys stored in GitHub
* Uses **OIDC with short-lived credentials**
* Least-privilege IAM role
* Production-grade CI/CD security

---

## 📄 Final Outcome

✔ Secure GitHub → AWS authentication
✔ Automated email notifications
✔ CI/CD success & failure visibility
✔ Resume-ready DevOps project

---
Below is a **clean, well-decorated, beginner-friendly `README.md`** on **Environment Variables in GitHub Actions CI/CD**.
You can **copy–paste directly** into your repository.

---

# 🌱 Environment Variables in GitHub Actions (CI/CD)

![GitHub Actions](https://img.shields.io/badge/GitHub-Actions-blue)
![CI/CD](https://img.shields.io/badge/CI%2FCD-Automation-green)
![Beginner Friendly](https://img.shields.io/badge/Level-Beginner-brightgreen)

![GitHub Actions](https://github.com/shyamdevk/GitHub-Actions/blob/image/env.gif)

---

## 📘 What Are Environment Variables?

Environment variables are **named values** that you can use inside your GitHub Actions workflows.
They help you **store configuration values once and reuse them** without repeating or hard-coding them.

### ✅ Why we use them

* Avoid repeating the same values
* Make workflows easy to read and maintain
* Change values without touching multiple steps
* Keep workflows clean and professional

---

## 📌 Levels of Environment Variables

GitHub Actions supports **three levels** of environment variables:

1. **Workflow level**
2. **Job level**
3. **Step level**

Each level has a **different scope** (where it can be used).

---

## 1️⃣ Workflow-Level Environment Variables

### 🔹 What is it?

Variables defined at the **top of the workflow**.
They are available to **all jobs and all steps**.

### 🔹 When to use?

Use when the value is needed **everywhere**, such as:

* AWS Region
* Application name
* Environment name (dev, test, prod)

### 🔹 Example

```yaml
name: Demo Workflow

env:
  AWS_REGION: us-east-1  #env variable declared here
  APP_NAME: sample-app

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Print variables
        run: |
          echo "Region: $AWS_REGION"      #used here
          echo "App Name: $APP_NAME"
```

### ✅ Beginner Tip

> Defined **once**, used **everywhere**.

---

## 2️⃣ Job-Level Environment Variables

### 🔹 What is it?

Variables defined **inside a job**.
They are available to **all steps of that job only**.

### 🔹 When to use?

Use when the value is needed **only for one job**, such as:

* Build environment
* Job-specific configuration

### 🔹 Example

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    env:
      BUILD_ENV: production   #env variable declared here

    steps:
      - name: Print job variable
        run: |
          echo "Build Environment: $BUILD_ENV"   #env used here
```

### ✅ Beginner Tip

> Job-level variables **do not work in other jobs**.

---

## 3️⃣ Step-Level Environment Variables

### 🔹 What is it?

Variables defined **inside a single step**.
They are available **only in that step**.

### 🔹 When to use?

Use for:

* Temporary values
* Step-specific flags
* Values used only once

### 🔹 Example

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Step with variable
        env:
          MESSAGE: "Hello from this step"     #env variable here
        run: |
          echo "$MESSAGE"    #env varaible used here
```

### ✅ Beginner Tip

> Step-level variables are **not shared** with other steps.

---

## 🔁 Priority Order (Very Important)

If the **same variable name** is defined at multiple levels, GitHub Actions uses this priority:

```
Step level > Job level > Workflow level
```

### 🔹 Example

```yaml
env:
  ENV_NAME: workflow

jobs:
  build:
    env:
      ENV_NAME: job

    steps:
      - name: Check priority
        env:
          ENV_NAME: step
        run: |
          echo $ENV_NAME
```

### 🔹 Output:

```
step
```

### ✅ Beginner Tip

> The **closest definition wins**.

---

## 🔐 Environment Variables vs Secrets (Simple)

| Environment Variables | Secrets                    |
| --------------------- | -------------------------- |
| Plain text            | Encrypted                  |
| Visible in workflow   | Hidden in logs             |
| Used for configs      | Used for passwords, tokens |

### 🔹 Using Secrets as Env Variables

```yaml
env:
  DB_PASSWORD: ${{ secrets.DB_PASSWORD }}
```

---

## 🧪 Real-World Example (CI/CD)

```yaml
env:
  AWS_REGION: us-east-1

jobs:
  deploy:
    runs-on: ubuntu-latest
    env:
      SERVICE: SES

    steps:
      - name: Deployment step
        env:
          STATUS: SUCCESS
        run: |
          echo "Deploying $SERVICE in $AWS_REGION with status $STATUS"
```

---
Got it 👍
Here is a **very simple, beginner-friendly `README.md`** with **just ONE clear example** showing **environment variable + expression** together.

---

# 🌱 Environment Variables & Expressions in GitHub Actions

## 📘 What is an Environment Variable?

An environment variable stores a value that can be reused in a workflow.

Example:

```yaml
ENV_NAME=production
```

---

## 🧮 What is an Expression?

An expression uses `${{ }}` to access GitHub information like:

* repository name
* branch name
* commit ID

Example:

```yaml
${{ github.repository }}
```

---

## ✅ One Simple Example

```yaml
name: Simple Env and Expression Demo

on: [push]

env:
  APP_NAME: DemoApp

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Print values
        run: |
          echo "Application Name: $APP_NAME"
          echo "Repository Name: ${{ github.repository }}"
```

---

## 🔍 What is Happening Here?

* `APP_NAME` → **Environment variable** (defined at workflow level)
* `$APP_NAME` → Used inside shell command
* `${{ github.repository }}` → **Expression** (gets repo name automatically)

---


# 🧪 LAB: Environment Variables in GitHub Actions (Workflow & Job Level)

![GitHub Actions](https://img.shields.io/badge/GitHub-Actions-blue)
![CI/CD](https://img.shields.io/badge/CI%2FCD-Beginner-green)

---

## 🎯 Lab Objective

This lab helps beginners understand how to use **Environment Variables** in **GitHub Actions**.

You will learn how to:

* Create a GitHub Actions workflow
* Define **workflow-level environment variables**
* Define **job-level environment variables**
* Use **both variables inside a job**

---

## 🔹 Step 1: Create a GitHub Repository

1. Go to **GitHub**
2. Click **New Repository**
3. Name it (example: `env-variable-lab`)
4. Keep the default branch as **main**
5. Click **Create repository**

---

## 🔹 Step 2: Create Workflow File

Inside your repository:

1. Create the folder:

   ```
   .github/workflows
   ```
2. Create a file inside it:

   ```
   env-demo.yml
   ```

---

## 🔹 Step 3: Add Workflow Code

Paste the following code into **`env-demo.yml`**:

```yaml
name: Environment Variable Demo

on:
  push:
    branches:
      - main

# Workflow-level environment variable
env:
  APP_NAME: MyFirstApp

jobs:
  demo-job:
    runs-on: ubuntu-latest

    # Job-level environment variable
    env:
      ENVIRONMENT: Development

    steps:
      - name: Print environment variables
        run: |
          echo "Application Name (Workflow Level): $APP_NAME"
          echo "Environment Name (Job Level): $ENVIRONMENT"
```

---

## 🔍 Step 4: Understand the Workflow (Simple Explanation)

### ✔ Workflow-Level Environment Variable

```yaml
env:
  APP_NAME: MyFirstApp
```

* Defined at the **workflow level**
* Available to **all jobs and steps**
* Accessed using:

  ```bash
  $APP_NAME
  ```

---

### ✔ Job-Level Environment Variable

```yaml
env:
  ENVIRONMENT: Development
```

* Defined **inside the job**
* Available to **all steps of that job**
* Accessed using:

  ```bash
  $ENVIRONMENT
  ```

---

### ✔ Using Both Variables Together

```bash
echo "Application Name (Workflow Level): $APP_NAME"
echo "Environment Name (Job Level): $ENVIRONMENT"
```

✔ Workflow-level variable is accessible inside the job
✔ Job-level variable is accessible inside steps

---

## ▶️ Step 5: Run the Workflow

1. Commit and push the file to the **main** branch
2. Go to the **Actions** tab in GitHub
3. Click **Environment Variable Demo**
4. Open the latest workflow run
5. Check the logs

---

## 📤 Expected Output

You should see the following in the workflow logs:

```
Application Name (Workflow Level): MyFirstApp
Environment Name (Job Level): Development
```

---

## 🧠 Easy Way to Remember

* **Workflow-level env** → Used everywhere
* **Job-level env** → Used only in that job
* Environment variables are accessed using `$VARIABLE_NAME`

---

# 📦 GitHub Actions Context Objects

![GitHub Actions](https://img.shields.io/badge/GitHub-Actions-blue)
![CI/CD](https://img.shields.io/badge/CI%2FCD-Automation-green)
![Level](https://img.shields.io/badge/Level-Beginner-brightgreen)

---

## 📘 What Are Context Objects?

**Context objects** are built-in objects provided by GitHub Actions.
They contain **information about the workflow run**, such as:

* Repository details
* Branch and commit
* Runner (machine) information
* Job status

You access context values using **expressions**:

```text
${{ context_name.property }}
```

---

## 1️⃣ GitHub Context (`github`)

### 🔹 What it Provides

Information about:

* Repository
* Branch
* Commit
* Workflow trigger event
* Actor (who triggered workflow)
* Pull request information (if PR workflow)

---

### 🔹 Syntax

```yaml
${{ github.<property> }}
```

---

### 🔹 Simple Example

```yaml
- name: GitHub context example
  run: |
    echo "Repository: ${{ github.repository }}"
    echo "Branch (ref_name): ${{ github.ref_name }}"
    echo "Full ref: ${{ github.ref }}"
    echo "Triggered By: ${{ github.actor }}"
    echo "Event Name: ${{ github.event_name }}"
    echo "Pull Request Number: ${{ github.event.pull_request.number }}"
```

---

### 🔹 Common Properties (Updated Table)

| Property                           | Description                                        |
| ---------------------------------- | -------------------------------------------------- |
| `github.repository`                | Repository name (`user/repo`)                      |
| `github.ref_name`                  | Branch name only (e.g., `main`)                    |
| `github.ref`                       | Full Git ref (e.g., `refs/heads/main`)             |
| `github.sha`                       | Commit ID                                          |
| `github.actor`                     | Username who triggered workflow                    |
| `github.event_name`                | Event type (push, pull_request, workflow_dispatch) |
| `github.event.pull_request.number` | PR number (only for pull_request events)           |

---

## 🧠 Quick Explanation of Added Properties

### ✔ `github.ref`

Full reference string
Example:

```
refs/heads/main
```

### ✔ `github.actor`

Who triggered the workflow
Example:

```
shyamdevk
```

### ✔ `github.event_name`

Type of event
Examples:

```
push  
pull_request  
workflow_dispatch
```

### ✔ `github.event.pull_request.number`

Pull request number
Example:

```
12
```

(Only works when workflow is triggered by a `pull_request` event)

---

## 2️⃣ Runner Context (`runner`)

### 🔹 What it Provides

Information about the **runner machine** that executes the job.

### 🔹 Syntax

```yaml
${{ runner.<property> }}
```

### 🔹 Simple Example

```yaml
- name: Runner context example
  run: |
    echo "Runner OS: ${{ runner.os }}"
    echo "Runner Name: ${{ runner.name }}"
```

### 🔹 Common Properties

| Property      | Description      |
| ------------- | ---------------- |
| `runner.os`   | Operating system |
| `runner.name` | Runner name      |

---

## 3️⃣ Job Context (`job`)

### 🔹 What it Provides

Information about the **current job**, especially its status.

### 🔹 Syntax

```yaml
${{ job.<property> }}
```

### 🔹 Simple Example

```yaml
- name: Job context example
  if: success()
  run: |
    echo "Job Status: ${{ job.status }}"
```

### 🔹 Common Properties

| Property     | Description                   |
| ------------ | ----------------------------- |
| `job.status` | success / failure / cancelled |

---

## 🔁 One Combined Example (Easy to Understand)

```yaml
- name: Context objects demo
  run: |
    echo "Repository: ${{ github.repository }}"
    echo "Branch: ${{ github.ref_name }}"
    echo "Runner OS: ${{ runner.os }}"
    echo "Job Status: ${{ job.status }}"
```

---

## 🧠 Easy Way to Remember

| Context  | Gives Information About |
| -------- | ----------------------- |
| `github` | Repo, branch, commit    |
| `runner` | Machine running the job |
| `job`    | Job execution status    |

---

# 📘 **GitHub Actions Lab – Understanding Context Objects**

Welcome to the simplest and most practical lab for understanding **GitHub Context Objects**.
This guide will help you learn how GitHub Actions reads information about your repository, workflow, runner, and job.

---

## 🎯 **Lab Objectives**

By the end of this lab, you will learn:

* What GitHub **context objects** are
* How to **print context values** inside a workflow
* How to **use step outputs**
* How to **view context values** in GitHub Actions logs

---

---

# 🧪 **1. Lab Setup**

## 👉 **Step 1: Create a New Repository**

1. Go to **[https://github.com](https://github.com)**
2. Click **New Repository**
3. Name it:

   ```
   context-objects-lab
   ```
4. Keep it **Public** (recommended for beginners)
5. Click **Create Repository**

---

## 👉 **Step 2: Create Workflow File**

Inside your new repo:

1. Click **Add file → Create new file**
2. Name the file:

   ```
   .github/workflows/context.yml
   ```

---

# 📝 **2. Add Workflow Code**

Copy and paste the workflow below:

```yaml
name: Context Objects Lab

on:
  workflow_dispatch:

jobs:
  show-contexts:
    runs-on: ubuntu-latest

    steps:
      - name: Print GitHub Context
        run: echo "Repository: ${{ github.repository }}"

      - name: Print Trigger Details
        run: echo "Event Name: ${{ github.event_name }}"

      - name: Print Commit Info
        run: echo "Commit Actor: ${{ github.actor }}"

      - name: Print Runner Info
        run: echo "Runner OS: ${{ runner.os }}"

      - name: Print Environment Variable
        env:
          MY_VAR: "Hello from environment"
        run: echo "Env Value: $MY_VAR"

      - name: Save Output Using Steps Context
        id: example
        run: echo "value=This is a step output" >> $GITHUB_OUTPUT

      - name: Print Step Output
        run: echo "Output from previous step: ${{ steps.example.outputs.value }}"

```

---

# ▶️ **3. Run the Workflow**

1. Go to the **Actions** tab
2. Select **Context Objects Lab**
3. Click **Run Workflow**
4. Click **Run Workflow** again to start the job

---

# 📊 **4. View the Results**

Open the workflow run → expand each step → you will see context values such as:

| Context                       | Description               | Example Output             |
| ----------------------------- | ------------------------- | -------------------------- |
| `github.repository`           | Repo name                 | `user/context-objects-lab` |
| `github.event_name`           | Event triggered workflow  | `workflow_dispatch`        |
| `github.actor`                | Who triggered workflow    | `shyamdevk`                |
| `runner.os`                   | OS of GitHub runner       | `Linux`                    |
| `job.status`                  | Job status                | `Success`                  |
| `steps.example.outputs.value` | Output from previous step | `This is a step output`    |

---


