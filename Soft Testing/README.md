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
