---

title : "CI/CD Pipeline Verification"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b> 5.4.9. </b> "
-------------------------

### 5.4.9. CI/CD Pipeline Verification

After completing the GitHub Actions configuration, navigate to **GitHub → Actions** to monitor the pipeline execution process. The pipeline consists of **06 jobs** that run sequentially to validate the source code, build Docker Images, and deploy the application to AWS.

| Order | Job              | Purpose                                          |
| ----- | ---------------- | ------------------------------------------------ |
| 1     | `backend-test`   | Check Backend code quality and run Unit Tests    |
| 2     | `frontend-check` | Check the Frontend and build the application     |
| 3     | `e2e-tests`      | Run Playwright End-to-End Tests                  |
| 4     | `build-and-push` | Build the Docker Image and push it to Amazon ECR |
| 5     | `deploy-backend` | Deploy the new version to Amazon ECS             |
| 6     | `smoke-tests`    | Verify the service status after deployment       |

---

### Pipeline Triggers

| Event          | Branch                  | Jobs Executed                                 |
| -------------- | ----------------------- | --------------------------------------------- |
| `push`         | `main`                  | All 6 jobs                                    |
| `push`         | `develop`, `feature/**` | `backend-test`, `frontend-check`, `e2e-tests` |
| `pull_request` | `main`                  | `backend-test`, `frontend-check`, `e2e-tests` |

---

### Job Details

#### Job 1 – `backend-test`

| Item           | Value                                     |
| -------------- | ----------------------------------------- |
| Purpose        | Check Backend source code quality         |
| Runner         | `ubuntu-latest` + Python 3.12             |
| Tasks          | `flake8` and `python manage.py test`      |
| PASS Condition | No linting errors and all Unit Tests pass |

---

#### Job 2 – `frontend-check`

| Item           | Value                                |
| -------------- | ------------------------------------ |
| Purpose        | Check and build the Frontend         |
| Runner         | `ubuntu-latest` + Node.js 22         |
| Tasks          | `npm run lint`, `npm run build`      |
| PASS Condition | Build succeeds with no ESLint errors |

---

#### Job 3 – `e2e-tests`

| Item      | Value                                     |
| --------- | ----------------------------------------- |
| Purpose   | Test critical application functions       |
| Tool      | Playwright (Chromium)                     |
| Condition | `frontend-check` succeeds                 |
| Result    | Test reports are stored in GitHub Actions |

---

#### Job 4 – `build-and-push`

| Item           | Value                                            |
| -------------- | ------------------------------------------------ |
| Purpose        | Build the Docker Image and push it to Amazon ECR |
| Condition      | `backend-test` and `e2e-tests` succeed           |
| Runs Only      | When pushing to the `main` branch                |
| Authentication | GitHub OIDC Assume IAM Role                      |

---

#### Job 5 – `deploy-backend`

| Item           | Value                                |
| -------------- | ------------------------------------ |
| Purpose        | Deploy the new version to Amazon ECS |
| Strategy       | Rolling Update                       |
| Migration      | Performed using ECS Run Task         |
| PASS Condition | Service update succeeds              |

---

#### Job 6 – `smoke-tests`

| Item           | Value                                                    |
| -------------- | -------------------------------------------------------- |
| Purpose        | Verify the service after deployment                      |
| Endpoints      | `/api/`, `/api/pois/`, `/api/tours/`, `/api/categories/` |
| PASS Condition | HTTP Status < 500                                        |

---

### Pipeline Authentication and Security

The pipeline uses **GitHub OIDC Federation** to authenticate with AWS through an **IAM Role** instead of storing static Access Keys in GitHub Secrets. This improves security and ensures that only the specified repository is authorized to perform deployments.

| Component              | Description                                                       |
| ---------------------- | ----------------------------------------------------------------- |
| OIDC Federation        | Authentication using temporary tokens                             |
| Least Privilege        | The IAM Role grants only the permissions required for ECR and ECS |
| Environment Protection | Approval can be required before deploying to Production           |
| Secret Management      | Sensitive information is stored in GitHub Secrets                 |
| Branch Protection      | Only the `main` branch can perform deployments                    |

---

### Common Troubleshooting Issues

| Issue                  | Cause                                        | Solution                                             |
| ---------------------- | -------------------------------------------- | ---------------------------------------------------- |
| OIDC login failed      | Incorrect Role ARN or Trust Policy           | Check `AWS_ROLE_ARN` and the OIDC configuration      |
| Backend test failed    | Source code or Unit Test errors              | Review GitHub Actions logs and run the tests locally |
| Frontend build failed  | Dependency or TypeScript errors              | Run `npm ci` and `npm run build`                     |
| ECS deployment timeout | Container failed to start successfully       | Check CloudWatch Logs and environment variables      |
| Smoke test failed      | Service is not ready or the URL is incorrect | Check the application's Health Check and Endpoints   |

---
