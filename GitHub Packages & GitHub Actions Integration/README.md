# 🔗 GitHub Packages & GitHub Actions Integration  

---

## 📘 What is GitHub Packages?

**GitHub Packages** is a package registry provided by GitHub.  
It allows you to **store, version, and share packages** such as:

- Docker images
- npm packages
- Maven packages
- Python packages

📌 Think of GitHub Packages as **Docker Hub / npm registry, but inside GitHub**.

---

## ⚙️ What is GitHub Actions?

**GitHub Actions** is GitHub’s built-in **CI/CD automation tool**.

It helps you:
- Build applications automatically
- Run tests
- Build Docker images
- Push packages to GitHub Packages

📌 Simply: **automation that runs when you push code to GitHub**.

---

## 🔗 Why Integrate GitHub Packages with GitHub Actions?

Because:
- GitHub Actions can **build your package**
- Automatically **push it to GitHub Packages**
- No manual Docker or package upload needed

### 🔄 Simple Flow
```

Code Push → GitHub Actions Runs → Package Built → Stored in GitHub Packages

````

---

## 🧪 LAB: Push Docker Image to GitHub Packages using GitHub Actions

### 🎯 Lab Goal
Automatically build a Docker image and push it to **GitHub Packages** using **GitHub Actions**.

---

## 🛠️ Prerequisites
- GitHub account
- Git installed
- Basic Docker knowledge
- Public GitHub repository

---

## 📁 Step 1: Create a GitHub Repository

1. Go to GitHub
2. Click **New Repository**
3. Repository name: `github-packages-lab`
4. Select **Public**
5. Add a README file
6. Create repository

---

## 📁 Step 2: Create a Simple Application

### Create `app.py`
```python
print("Hello from GitHub Packages Lab!")
````

---

### Create `Dockerfile`

```dockerfile
FROM python:3.10-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

📌 This Dockerfile creates a simple Python container.

---

## ⚙️ Step 3: Create GitHub Actions Workflow

### Create folders

```text
.github/
 └── workflows/
```

### Create file

`.github/workflows/docker-publish.yml`

```yaml
name: Build and Push Docker Image

on:
  push:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout source code
        uses: actions/checkout@v4

      - name: Login to GitHub Container Registry
        uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Build Docker image
        run: |
          docker build -t ghcr.io/${{ github.repository_owner }}/github-packages-lab:latest .

      - name: Push Docker image
        run: |
          docker push ghcr.io/${{ github.repository_owner }}/github-packages-lab:latest
```

---

## 🔐 Step 4: Enable Workflow Permissions

1. Go to **Repository → Settings**
2. Open **Actions → General**
3. Under **Workflow permissions**
4. Select:

   ```
   ✅ Read and write permissions
   ```
5. Click **Save**

📌 Required to push packages to GitHub Packages.

---

## ▶️ Step 5: Push Code to GitHub

```bash
git add .
git commit -m "GitHub Packages Actions Lab"
git push origin main
```

📌 This triggers the GitHub Actions workflow automatically.

---

## 📦 Step 6: Verify GitHub Packages

1. Go to your GitHub repository
2. Click **Packages** (right side)
3. You should see:

   ```
   ghcr.io/<your-username>/github-packages-lab
   ```

🎉 **Docker image successfully published!**

---

## 🔁 Step 7: Pull the Image (Optional Test)

```bash
docker pull ghcr.io/<your-username>/github-packages-lab:latest
```

---

## 🧠 Interview One-Liners

* **GitHub Packages**: A registry to store and manage application packages inside GitHub.
* **GitHub Actions**: CI/CD tool to automate build, test, and deployment.
* **Integration**: GitHub Actions builds and pushes packages automatically to GitHub Packages.

---

## ✅ Final Summary

> GitHub Actions automates the build process,
> GitHub Packages stores the output,
> and the package is ready for deployment or reuse.

---

# 🚀 GitHub Actions – What is an Action?

## 📌 What is an Action?

A **GitHub Action** is a **reusable task** that performs **one specific job** in a GitHub Actions workflow.

👉 Think of an **Action** as a **ready-made script** that you can plug into your CI/CD pipeline.

---

## 🧠 Simple Explanation

An **Action** can do things like:
- 📥 Download your code
- 🧪 Run tests
- 🏗️ Build your application
- 🚀 Deploy your app
- 🔐 Scan code for security issues

Actions help **automate work** whenever something happens in a repository (like a push or pull request).

---

## 🧩 Where Actions Fit

Actions are used inside **workflows** in **:contentReference[oaicite:1]{index=1} Actions**.

### Workflow Structure
```

Workflow
└── Job
└── Step
└── Action ✅

````

---

## 🛠️ Simple Action Example

```yaml
- name: Checkout source code
  uses: actions/checkout@v4
````

### 🔍 What this does?

* Downloads your GitHub repository code
* Makes the code available for the next steps

---

## 📂 Types of GitHub Actions

### 1️⃣ Official Actions

* Created by GitHub
* Trusted and widely used
  Example:

```
actions/checkout
```

### 2️⃣ Community Actions

* Created by developers worldwide
* Available publicly

### 3️⃣ Custom Actions

* Actions you create yourself
* Useful for custom workflows

---

## 🛒 Where Do Actions Come From?

You can find Actions in the **GitHub Marketplace**.

👉 You can directly use them in your workflow using the `uses:` keyword.

---

## ⭐ Why GitHub Actions Are Useful

* ✅ Saves time
* ♻️ Reusable across projects
* 🧩 No need to write scripts from scratch
* 🚀 Makes CI/CD easy and automated

---

## 📝 One-Line Summary (Interview Ready)

> **A GitHub Action is a reusable unit of code that performs a specific task inside a GitHub Actions workflow.**

---
Here is a **clean, simple, well-decorated `README.md`** based on the **Custom Actions** concept from the shared repository.
You can **directly copy–paste** this into your notes or project.

---

# ⚙️ GitHub Actions – Importance, Uses & Custom Action Guide

## ⭐ Importance of GitHub Actions

### 🔹 1. Automation
- Automatically run tasks when an event occurs (push, pull request, release)
- No manual work needed

### 🔹 2. Saves Time
- Reuse existing actions instead of writing scripts every time
- Faster development and deployment

### 🔹 3. Consistency
- Same process runs every time
- Reduces human errors

### 🔹 4. Easy CI/CD
- Build → Test → Deploy automatically
- Works directly inside GitHub

---

## 🧠 Uses of GitHub Actions

GitHub Actions are used to:

- 🧪 Run tests automatically
- 🏗️ Build applications
- 🚀 Deploy applications
- 🔐 Scan code for security issues
- 📦 Publish packages
- 📢 Send notifications (Slack, Email, etc.)

---

## 🧩 Why Custom Actions?

Custom Actions are used when:
- Built-in actions are not enough
- You want **your own reusable logic**
- You want to keep workflows **clean and simple**

### ✅ Benefits of Custom Actions
- Reusable across multiple workflows
- Clean workflow files
- Easy team collaboration
- Shareable via GitHub Marketplace (optional)

---

# 🧪 GitHub Actions Custom Action – Simple Lab

This lab helps you understand **how to create and use a custom GitHub Action** and run it using **GitHub Actions workflow**.

---

## 🎯 Lab Objective

- Create a **custom GitHub Action**
- Use it inside a **GitHub Actions workflow**
- Push `.yml` files into GitHub repository
- Automatically trigger workflow on `git push`

---

## 🧠 What is a Custom GitHub Action?

A **custom action** is an action that **you create yourself** instead of using ready-made actions from the GitHub Marketplace.

---

## 📁 Project Structure

```

github-actions-custom-lab/
├── .github/
│   └── workflows/
│       └── custom-action.yml
├── my-custom-action/
│   └── action.yml
├── README.md

```

---

## 🛠 Step 1: Create GitHub Repository

1. Go to GitHub
2. Click **New Repository**
3. Repository name:
```

github-actions-custom-lab

````
4. Set visibility to **Public**
5. Click **Create repository**

---

## 🛠 Step 2: Clone Repository

```bash
git clone https://github.com/<your-username>/github-actions-custom-lab.git
cd github-actions-custom-lab
````

---

## 🛠 Step 3: Create Custom Action

```bash
mkdir my-custom-action
cd my-custom-action
nano action.yml
```

### 📄 `my-custom-action/action.yml`

```yaml
name: "My Custom Action"
description: "Simple custom GitHub Action"
author: "Your Name"

runs:
  using: "composite"
  steps:
    - name: Print message
      run: echo "✅ Hello from my custom GitHub Action!"
      shell: bash
```

Save and exit.

---

## 🛠 Step 4: Create Workflow File

```bash
cd ..
mkdir -p .github/workflows
nano .github/workflows/custom-action.yml
```

### 📄 `.github/workflows/custom-action.yml`

```yaml
name: Custom Action Workflow

on:
  push:
    branches:
      - main

jobs:
  run-custom-action:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Run my custom action
        uses: ./my-custom-action
```

---

## 🛠 Step 5: Push Files to GitHub

> ⚠️ GitHub **does not allow password authentication**.
> You must use a **Personal Access Token (PAT)** with `repo` and `workflow` permissions.

```bash
git add .
git commit -m "Added custom GitHub Action and workflow"
git push origin main
```

When prompted:

* **Username** → your GitHub username
* **Password** → paste your **PAT token**

---

## ▶️ Step 6: Verify Workflow Execution

1. Open your repository on GitHub
2. Click **Actions**
3. Select **Custom Action Workflow**
4. Open logs

### ✅ Expected Output

```
✅ Hello from my custom GitHub Action!
```

---

## 🧠 Key Learnings

* GitHub Actions run workflows defined in `.github/workflows`
* Custom actions can be stored locally in the repository
* Workflow files require `workflow` permission in PAT
* Actions are triggered automatically on events like `push`

---

## 🔐 Common Errors & Fixes

| Error                  | Solution                    |
| ---------------------- | --------------------------- |
| 403 permission denied  | Use PAT instead of password |
| Workflow push rejected | Add `workflow` scope to PAT |

---
# GitHub Actions – Matrix (Multi Configuration) Strategy

## What is Matrix in GitHub Actions?
**Matrix strategy** in GitHub Actions allows you to run the **same job multiple times** with **different configurations** such as:
- Operating systems
- Programming language versions
- Tool versions

👉 One workflow can test many environments automatically.

---

## Why Use Matrix?
- ✅ Test your code on **multiple environments**
- ✅ Avoid **duplicate jobs**
- ✅ Faster and cleaner CI workflows
- ✅ Easy to scale testing

---

## Matrix Strategy Example with Comments

```yaml
# Name of the GitHub Actions workflow
name: Matrix Demo

# Workflow will run whenever code is pushed to the repository
on: [push]

jobs:
  # Job name
  build:
    # The OS where the job runs
    # This value comes from the matrix (ubuntu or windows)
    runs-on: ${{ matrix.os }}

    # Matrix strategy allows running the same job
    # with multiple configurations
    strategy:
      matrix:
        # Operating systems to test on
        os: [ubuntu-latest, windows-latest]

        # Node.js versions to test with
        node-version: [16, 18]

    steps:
    # Step 1: Checkout (download) the repository code
    - uses: actions/checkout@v4

    # Step 2: Setup Node.js environment
    # Node version comes from matrix.node-version
    - name: Setup Node.js
      uses: actions/setup-node@v4
      with:
        node-version: ${{ matrix.node-version }}

    # Step 3: Install project dependencies
    - name: Install dependencies
      run: npm install

    # Step 4: Run test cases
    - name: Run tests
      run: npm test
```

## What Happens Internally?

GitHub Actions creates **multiple jobs automatically**:

| OS      | Node Version |
| ------- | ------------ |
| Ubuntu  | 16           |
| Ubuntu  | 18           |
| Windows | 16           |
| Windows | 18           |

✔ Same steps
✔ Different environments

---

## Accessing Matrix Values

Use matrix variables like this:

```yaml
${{ matrix.os }}
${{ matrix.node-version }}
```

---

## Excluding a Matrix Combination

If a specific combination should not run:

```yaml
strategy:
  matrix:
    os: [ubuntu-latest, windows-latest]
    node-version: [16, 18]
    exclude:
      - os: windows-latest
        node-version: 16
```

❌ Windows + Node 16 will be skipped

---

## Including Custom Values

You can add extra values for special cases:

```yaml
strategy:
  matrix:
    os: [ubuntu-latest, windows-latest]
    include:
      - os: ubuntu-latest
        special: true
```

Use it in steps like:

```yaml
${{ matrix.special }}
```

---

## Real-World Use Cases

* Cross-platform testing (Linux, Windows, macOS)
* Testing with multiple language versions
* Running security scans with different tools
* CI for enterprise-level applications

---

## Interview One-Liner 🎯

> Matrix strategy in GitHub Actions allows running the same job multiple times with different configurations like OS or software versions.

---
# Java CI/CD Pipeline using GitHub Actions (Matrix Strategy Lab)

This is a **beginner-friendly hands-on lab** to build a **Java application** using **multiple JDK versions (17, 21, 24)** and **multiple OS (Ubuntu & Windows)** using **GitHub Actions Matrix strategy**.

You will:
- Create a simple Java app
- Configure GitHub Actions CI pipeline
- Build the app on different OS + JDK versions automatically

---

## Lab Objective 🎯
- Learn **Matrix (Multi-configuration)** in GitHub Actions
- Understand **DRY principle** in CI/CD
- Build Java using **JDK 17, 21, 24**
- Run builds on **Ubuntu & Windows**

---

## Prerequisites ✅
- GitHub account
- Basic Java knowledge
- Git installed
- Java code editor (VS Code recommended)

---

## Step 1: Create a New GitHub Repository

1. Go to GitHub
2. Click **New Repository**
3. Repository name: `java-matrix-ci`
4. Select **Public**
5. Click **Create repository**

---

## Step 2: Clone the Repository

```bash
git clone https://github.com/<your-username>/java-matrix-ci.git
cd java-matrix-ci
````

---

## Step 3: Create Project Structure

```text
java-matrix-ci/
│
├── src/
│   └── App.java
│
├── .github/
│   └── workflows/
│       └── java-ci.yml
│
└── README.md
```

---

## Step 4: Create Java File (App.java)

📁 `src/App.java`

```java
public class App {
    public static void main(String[] args) {
        System.out.println("Java CI/CD Matrix Build Successful!");
    }
}
```

✔ Simple Java program
✔ No dependencies needed

---

## Step 5: Create GitHub Actions Workflow

📁 `.github/workflows/java-ci.yml`

```yaml
# Name of the workflow
name: Java Matrix CI Pipeline

# Trigger workflow on push
on: [push]

jobs:
  build:
    # OS comes from matrix
    runs-on: ${{ matrix.os }}

    # Matrix strategy for multiple OS and JDK versions
    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest]
        java-version: [17, 21, 24]

    steps:
    # Step 1: Checkout repository code
    - name: Checkout code
      uses: actions/checkout@v4

    # Step 2: Setup Java based on matrix version
    - name: Set up JDK
      uses: actions/setup-java@v4
      with:
        distribution: 'temurin'
        java-version: ${{ matrix.java-version }}

    # Step 3: Compile Java program
    - name: Compile Java
      run: javac src/App.java

    # Step 4: Run Java program
    - name: Run Java App
      run: java -cp src App
```

---

## Step 6: Push Code to GitHub

```bash
git add .
git commit -m "Add Java CI pipeline with matrix strategy"
git push origin main
```

---

## Step 7: Verify GitHub Actions

1. Go to your GitHub repository
2. Click **Actions**
3. Open **Java Matrix CI Pipeline**

You will see **6 jobs running**:

| OS      | JDK |
| ------- | --- |
| Ubuntu  | 17  |
| Ubuntu  | 21  |
| Ubuntu  | 24  |
| Windows | 17  |
| Windows | 21  |
| Windows | 24  |

✔ Same job
✔ Different configurations

---

## Step 8: Understand What Happened

* Matrix created **6 parallel builds**
* Same Java code compiled everywhere
* Follows **DRY principle**
* Ensures compatibility across environments

---

## Interview One-Liner 🎯

> I used GitHub Actions matrix strategy to build a Java application across multiple JDK versions and operating systems using a single CI pipeline.

---
# DRY Principle (Don't Repeat Yourself)

### What is DRY?
**DRY** stands for **Don’t Repeat Yourself**.

👉 It means **avoid writing the same code, logic, or configuration again and again**.  
Instead, **reuse** it from a single place.

---

### Simple Definition
> Every piece of knowledge or logic should have a **single, unambiguous source**.

---

### Why DRY is Important?
- ✅ Easier to **maintain**
- ✅ Reduces **errors**
- ✅ Saves **time and effort**
- ✅ Code/config becomes **clean and readable**
- ✅ Changes need to be done in **one place only**

---

### DRY in Programming (Simple Example)

❌ **Not DRY (Repeating Code)**
```python
print("Welcome User")
print("Welcome User")
print("Welcome User")
````

✅ **DRY (Reusable Code)**

```python
def welcome():
    print("Welcome User")

welcome()
welcome()
welcome()
```

---

### DRY in GitHub Actions (Without Matrix)

❌ Repeating jobs

```yaml
jobs:
  build-node-16:
    runs-on: ubuntu-latest
    steps:
      - run: node --version

  build-node-18:
    runs-on: ubuntu-latest
    steps:
      - run: node --version
```

---

### DRY in GitHub Actions (Using Matrix)

✅ Same logic, multiple configurations

```yaml
strategy:
  matrix:
    node-version: [16, 18]
```

✔ One job
✔ No duplication

---

### DRY in CI/CD Pipelines

* Use **matrix strategy**
* Reuse **steps**
* Use **reusable workflows**
* Use **variables & secrets**
* Avoid copy-pasting jobs

---

### DRY vs WET

| DRY                   | WET                    |
| --------------------- | ---------------------- |
| Don’t Repeat Yourself | Write Everything Twice |
| Clean & maintainable  | Messy & error-prone    |
| Easy updates          | Hard to fix            |

---

### Interview One-Liner 🎯

> DRY principle means avoiding duplication by reusing code or configurations from a single source.

---
