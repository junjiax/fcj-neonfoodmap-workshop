---
title : "Prerequisites"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

### 5.2. Prerequisites

Before starting the NeonFoodMap deployment process on AWS, prepare the AWS account, source code, local development environment, GitHub repository, and the required AWS access permissions.

The prerequisites in this section only cover the environment and access requirements. The creation and configuration of AWS resources such as IAM, VPC, RDS, S3, ECR, ECS, and CloudWatch are performed in the subsequent deployment sections.

---

### 5.2.1. AWS Account and Region

An AWS account is required to deploy and operate the NeonFoodMap application.

1. Access the **AWS Management Console**.

2. Sign in using an AWS account with sufficient permissions to perform the deployment.

3. Set the AWS Region to:

```text
Asia Pacific (Singapore) - ap-southeast-1
```

4. Verify that the selected Region is displayed consistently in the AWS Management Console before creating resources.

The project uses `ap-southeast-1` as the primary deployment Region. AWS resources created in subsequent steps should be deployed in this Region unless otherwise specified.

> The AWS resources are not created in this prerequisite section. This section only verifies that the AWS account and deployment Region are ready.

---

### 5.2.2. NeonFoodMap Source Code

NeonFoodMap consists of two main application components:

```text
NeonFoodMap
├── Backend
│   └── Django
│
└── Frontend
    └── React + TypeScript
```

The source code must be available locally before starting the deployment process.

Clone the NeonFoodMap repository:

```bash
git clone https://github.com/HaoWasabi/NeonFoodmap.git
```

Navigate to the project directory:

```bash
cd NeonFoodmap
```

Verify the source code:

```bash
git status
```

The repository should contain the source code required for both the Backend and Frontend.

The source code will later be used to:

- Install Backend and Frontend dependencies.
- Run the applications locally.
- Build Docker Images.
- Push Docker Images to Amazon ECR.
- Execute the CI/CD pipeline through GitHub Actions.

---

### 5.2.3. Development Environment

The local development environment must contain the tools required to develop, test, and package the NeonFoodMap application.

The required tools are:

```text
Development Environment
├── Git
├── Python
├── Python Virtual Environment
├── Node.js / npm
└── Docker
```

#### Git

Git is used to clone the NeonFoodMap source code and manage changes during development.

Check the installed Git version:

```bash
git --version
```

Example:

```text
git version 2.x.x
```

If the command returns the Git version, Git is ready to use.

---

#### Python

Python is required to run the NeonFoodMap Django Backend.

Check the installed Python version:

```bash
python --version
```

Example:

```text
Python 3.12.x
```

If the system uses `python3`, run:

```bash
python3 --version
```

The Python version should be compatible with the version required by the Backend project.

---

#### Python Virtual Environment

A Python virtual environment is used to isolate the Backend dependencies from the system Python environment.

Navigate to the Backend directory:

```bash
cd backend
```

Create a virtual environment:

```bash
python -m venv venv
```

After creation, the Backend directory will contain:

```text
backend/
├── venv/
├── manage.py
├── requirements.txt
├── config/
└── ...
```

Activate the virtual environment.

**Windows PowerShell:**

```powershell
.\venv\Scripts\Activate.ps1
```

**Windows Command Prompt:**

```cmd
venv\Scripts\activate
```

**Linux/macOS:**

```bash
source venv/bin/activate
```

After successful activation, `(venv)` appears at the beginning of the terminal prompt:

```text
(venv) PS D:\NeonFoodMap\backend>
```

Update `pip`:

```bash
python -m pip install --upgrade pip
```

Install the Backend dependencies from `requirements.txt`:

```bash
pip install -r requirements.txt
```

Verify the Django installation:

```bash
python -m django --version
```

The virtual environment should not be committed to Git. Add the following entry to `.gitignore`:

```gitignore
venv/
```

> The virtual environment is used for local development and testing. During the ECS deployment process, Python dependencies are installed inside the Docker Image according to `requirements.txt`.

---

#### Node.js / npm

Node.js and npm are required to install dependencies and build the NeonFoodMap React Frontend.

Check the Node.js version:

```bash
node --version
```

Check the npm version:

```bash
npm --version
```

Example:

```text
Node.js: 22.x.x
npm: 10.x.x
```

Navigate to the Frontend directory:

```bash
cd frontend
```

Install the Frontend dependencies:

```bash
npm install
```

Verify that the Frontend dependencies are installed successfully.

The Frontend can then be tested locally using the project's configured npm scripts.

---

#### Docker

Docker is required to build and test the Container Images used by NeonFoodMap.

Check the Docker installation:

```bash
docker --version
```

Verify that Docker is running:

```bash
docker info
```

Docker will later be used to package the application into Container Images:

```text
Backend Source Code
        ↓
Docker Build
        ↓
Backend Image
```

and:

```text
Frontend Source Code
        ↓
Docker Build
        ↓
Frontend Image
```

The resulting Images will subsequently be pushed to Amazon ECR and deployed to Amazon ECS Fargate.

---

### 5.2.4. GitHub Repository

The NeonFoodMap source code is hosted in the following GitHub repository:

```text
https://github.com/HaoWasabi/NeonFoodmap.git
```

Verify that the local repository is connected to the correct remote:

```bash
git remote -v
```

Expected result:

```text
origin  https://github.com/HaoWasabi/NeonFoodmap.git (fetch)
origin  https://github.com/HaoWasabi/NeonFoodmap.git (push)
```

The repository will later be used by the CI/CD pipeline to:

1. Trigger the workflow when code is pushed or a Pull Request is created.
2. Run Backend tests.
3. Run Frontend checks.
4. Run End-to-End tests.
5. Build Docker Images.
6. Push Images to Amazon ECR.
7. Deploy the application to Amazon ECS.
8. Execute post-deployment smoke tests.

The GitHub Actions workflow should be stored under:

```text
.github/
└── workflows/
```

At this stage, only verify that the repository is accessible and the source code can be cloned. The detailed configuration of GitHub Actions, OIDC, ECR, and ECS deployment is performed in the subsequent CI/CD sections.

---

### 5.2.5. Required AWS Access

The AWS account used for the project must have sufficient permissions to create and configure the AWS resources required by NeonFoodMap.

The deployment process will require access to services including:

| AWS Service | Purpose |
|-------------|---------|
| IAM | Manage users, groups, policies, and roles |
| VPC | Configure the application network |
| Amazon RDS | Provide the application database |
| Amazon S3 | Store application files and static assets |
| Amazon ECR | Store Docker Images |
| Amazon ECS | Run Backend and Frontend Containers |
| Elastic Load Balancing | Distribute application traffic |
| Amazon CloudWatch | Collect and monitor application logs |
| AWS Secrets Manager | Store sensitive application configuration |
| AWS STS | Provide temporary credentials for CI/CD authentication |

Before starting the deployment, verify that the AWS account or IAM identity being used is authorized to access the required services.

The project follows the **Principle of Least Privilege**, so permissions should only be granted according to the operations required by each user, role, or deployment component.

> The IAM policies and roles are not created in this prerequisite section. Their detailed configuration is performed in the IAM deployment section.

---

### Prerequisite Checklist

Before proceeding to the AWS deployment steps, verify the following:

| No. | Requirement | Status |
|-----|-------------|--------|
| 1 | AWS Account | Ready |
| 2 | AWS Region `ap-southeast-1` | Selected |
| 3 | NeonFoodMap Source Code | Available |
| 4 | Git | Installed |
| 5 | Python | Installed |
| 6 | Python Virtual Environment | Created |
| 7 | Backend Dependencies | Installed |
| 8 | Node.js / npm | Installed |
| 9 | Frontend Dependencies | Installed |
| 10 | Docker | Installed and running |
| 11 | GitHub Repository | Accessible |
| 12 | GitHub Actions Workflow | Available |
| 13 | Required AWS Access | Available |

After all prerequisites are satisfied, the environment is ready to proceed with the detailed AWS deployment of **NeonFoodMap**.