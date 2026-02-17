
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
