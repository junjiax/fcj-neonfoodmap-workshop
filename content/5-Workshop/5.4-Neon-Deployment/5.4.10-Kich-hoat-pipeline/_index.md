---

title : "Triggering the Pipeline"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b> 5.4.10. </b> "
--------------------------

### 5.4.10. Triggering the Pipeline

After completing the GitHub Actions configuration and confirming that the workflow has been saved in the repository, push the source code to the `main` branch to trigger the CI/CD process. When a **push** event occurs on the `main` branch, GitHub Actions automatically executes the entire pipeline, including source code validation, Docker Image building, deployment to Amazon ECS, and application status verification after deployment.

#### 1. Switch to the `main` Branch

Open a Terminal in the project directory and switch to the `main` branch.

```bash
git checkout main
```

> If the `main` branch does not contain the latest version from GitHub, synchronize it before performing the merge.

```bash
git pull origin main
```

---

#### 2. Merge the Source Code from the `develop` Branch

Merge all changes from the `develop` branch into `main`.

```bash
git merge develop
```

If a **Merge Conflict** occurs, resolve the conflicts in the affected files and then continue the merge process.

```bash
git add .
git commit
```

After the merge is completed successfully, all changes from the `develop` branch will be incorporated into the `main` branch.

---

#### 3. Push the Source Code to GitHub

Push the `main` branch to GitHub.

```bash
git push origin main
```

Immediately after the command completes, GitHub generates a **push** event, which automatically triggers the workflow defined in the `.github/workflows` directory.

---

#### 4. Monitor the Pipeline Execution

Access the repository on GitHub and select **Actions** to monitor the pipeline execution status.

The pipeline executes the following jobs sequentially:

1. `backend-test`
2. `frontend-check`
3. `e2e-tests`
4. `build-and-push`
5. `deploy-backend`
6. `smoke-tests`

Each job is executed only when the preceding job completes successfully. If a job fails, the dependent subsequent steps will not be executed.

---

#### 5. Verify the Results

After the pipeline completes, verify the following items:

| Item           | Expected Result                     |
| -------------- | ----------------------------------- |
| Backend Test   | Successful                          |
| Frontend Build | Successful                          |
| Playwright E2E | Successful                          |
| Docker Image   | Pushed to Amazon ECR                |
| ECS Deployment | Service updated to the new version  |
| Smoke Test     | APIs return valid HTTP Status codes |

If all jobs display a **Success** status, the CI/CD process has been successfully triggered and deployed.

---

#### Example

```bash
git checkout main
git pull origin main

git merge develop

git push origin main
```
