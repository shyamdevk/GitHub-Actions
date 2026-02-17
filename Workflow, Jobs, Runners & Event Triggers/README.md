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
