# GitHub Actions - Complete Guide

## 1. What is GitHub Actions?
**Layman Example:**  
Think of GitHub as your workshop where you keep all your project code.  
GitHub Actions is like robots in that workshop that automatically do repetitive tasks for you — such as testing your code, deploying it to a server, or sending you a success/failure report — without you touching anything.

**Technical Definition:**  
GitHub Actions is a CI/CD (Continuous Integration / Continuous Deployment) automation feature built into GitHub that lets you create workflows using YAML files to automate build, test, and deploy processes.

---

## 2. Why We Need GitHub Actions?
- Saves time by automating repetitive tasks (build, test, deploy).
- Ensures consistency (robots don’t forget steps).
- Integrates deeply with GitHub (no separate tool needed).
- Runs on GitHub’s servers (no need to set up infrastructure).

---

## 3. Uses of GitHub Actions
- Automatically run tests when new code is pushed.
- Build and package apps.
- Deploy to AWS, Azure, or other platforms.
- Send notifications (Slack, email) after builds.
- Run scheduled tasks (daily backups, reports).

---

## 4. When to Use GitHub Actions?
- Whenever you have code hosted on GitHub and want to automate tasks.
- When you need a free or low-cost CI/CD tool for small-to-medium projects.
- For open-source projects that require automated testing for every contribution.

---

## 5. Versions of GitHub Actions
GitHub Actions doesn’t have “version numbers” like Terraform or Docker — it’s continuously updated by GitHub.  
Instead, individual Actions (pre-built scripts) have their own versions (e.g., `actions/checkout@v3`).

---

## 6. GitHub Actions Terminologies (with Examples)
| Term       | Definition | Example |
|------------|------------|---------|
| **Workflow** | The complete automation process. | “Test & Deploy Website” workflow |
| **Event**   | Trigger that starts the workflow. | Pushing code to `main` branch |
| **Job**     | A set of steps run in sequence on a runner. | “Run unit tests” |
| **Step**    | An individual action in a job. | “Install dependencies” |
| **Action**  | A reusable script that performs a task. | `actions/checkout` to clone code |
| **Runner**  | The machine that executes the job. | GitHub-hosted Ubuntu runner |

---

## 7. How to "Install" GitHub Actions
You don’t install GitHub Actions on your PC — it’s built into GitHub.  
You just create a workflow file in your repository.

**Steps:**
1. Go to your GitHub repository.
2. Create a folder: `.github/workflows`
3. Inside it, create a file: `ci.yml`
4. Add this sample:

```yaml
name: CI Pipeline
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3
    - name: Run script
      run: echo "Hello from GitHub Actions!"
