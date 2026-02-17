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
