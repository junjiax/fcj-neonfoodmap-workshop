---
title: "Creating an ECS Cluster and Service"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 5.4.8. </b> "
---

---

### 5.4.8. Creating an ECS Cluster and Service

After completing this section, the system will meet the following requirements:

- Successfully create an ECS Cluster using **AWS Fargate**.
- Configure the ECS Service to use Subnets across **2 Availability Zones (AZ1, AZ2)** to improve availability.
- Create Task Definitions for the Backend and Frontend with **256 CPU** and **512 MB RAM**.
- Configure CloudWatch Logs for the Containers.
- Configure environment variables and Secrets for the application.
- Configure the IAM Task Execution Role to allow ECS to pull Docker Images from Amazon ECR and write logs to CloudWatch.
- Verify that the Tasks start and operate normally.

---

### Implementation Steps

#### Step 1. Create an ECS Cluster Using AWS Fargate

1. Access the **AWS Management Console**.

2. Search for and select the **Amazon ECS** service.

3. In the left navigation menu, select **Clusters**.

4. Select **Create cluster**.

5. In **Cluster name**, enter the Cluster name:

```text
neonfoodmap-cluster
```

6. Under **Infrastructure**, select:

```text
AWS Fargate (serverless)
```

7. Review the Cluster information.

8. Select **Create** to create the Cluster.

9. After the Cluster is successfully created, it will appear in the list.

> **Note:** An ECS Cluster is a logical resource and is not directly assigned to AZ1 or AZ2. Running Tasks across multiple Availability Zones is configured when creating the ECS Service by selecting Subnets belonging to AZ1 and AZ2.

---

![](images/5-Workshop/5.4-Neon-Deployment/image010.png)
![](images/5-Workshop/5.4-Neon-Deployment/image011.png)
![](images/5-Workshop/5.4-Neon-Deployment/image012.png)
![](images/5-Workshop/5.4-Neon-Deployment/image013.png)
![](images/5-Workshop/5.4-Neon-Deployment/image014.png)
![](images/5-Workshop/5.4-Neon-Deployment/image015.png)

#### Step 2. Create a Backend Task Definition with 256 CPU and 512 MB RAM

The Task Definition specifies how ECS launches the Backend Container, including the Docker Image, CPU, RAM, Port, Environment Variables, and Log Configuration.

1. In Amazon ECS, select **Task definitions**.

2. Select **Create new task definition**.

3. Enter the Task Definition name:

```text
neonfoodmap-backend
```

4. Under **Infrastructure requirements**, select:

```text
AWS Fargate
```

5. Configure the resources:

```text
CPU: 0.25 vCPU
Memory: 0.5 GB
```

Equivalent values:

```text
CPU: 256
RAM: 512 MiB
```

6. Under **Task execution role**, select the IAM Role for ECS Task Execution.

For example:

```text
NeonFoodmap-ECS-TaskExecution-Role
```

7. Under **Container**, select **Add container**.

8. Enter the Container name:

```text
backend
```

9. Under **Image URI**, enter the Backend Docker Image stored in Amazon ECR.

For example:

```text
<AWS_ACCOUNT_ID>.dkr.ecr.<AWS_REGION>.amazonaws.com/<BACKEND_REPOSITORY>:latest
```

10. Configure **Port mapping** according to the Port used by the Backend Container.

For example:

```text
Container port: 8000
Protocol: TCP
```

11. Configure the **Environment variables** required by the application.

For example:

```text
DJANGO_SETTINGS_MODULE
DEBUG
ALLOWED_HOSTS
AWS_REGION
```

12. For sensitive information such as RDS connection credentials or API Keys, configure them through **Secrets** instead of storing their values directly in the Task Definition.

13. Configure Container Logs using **Amazon CloudWatch Logs**.

Use the following Log Group:

```text
/ecs/neonfoodmap-backend
```

14. Verify the following:

- Docker Image.
- CPU and RAM.
- Container Port.
- Environment Variables.
- Secrets.
- Task Execution Role.
- CloudWatch Log Group.

15. Select **Create** to create the Task Definition.

---

![](images/5-Workshop/5.4-Neon-Deployment/image016.png)
![](images/5-Workshop/5.4-Neon-Deployment/image017.png)
![](images/5-Workshop/5.4-Neon-Deployment/image018.png)
![](images/5-Workshop/5.4-Neon-Deployment/image019.png)
![](images/5-Workshop/5.4-Neon-Deployment/image020.png)
![](images/5-Workshop/5.4-Neon-Deployment/image021.png)
![](images/5-Workshop/5.4-Neon-Deployment/image022.png)
![](images/5-Workshop/5.4-Neon-Deployment/image023.png)
![](images/5-Workshop/5.4-Neon-Deployment/image024.png)

#### Step 3. Create a Frontend Task Definition with 256 CPU and 512 MB RAM

Follow the same procedure as for the Backend, but use the Frontend Docker Image.

1. Navigate to:

**Amazon ECS → Task definitions → Create new task definition**.

2. Enter the Task Definition name:

```text
neonfoodmap-frontend
```

3. Select:

```text
AWS Fargate
```

4. Configure the resources:

```text
CPU: 0.25 vCPU
Memory: 0.5 GB
```

5. Select the **Task execution role**:

```text
NeonFoodmap-ECS-TaskExecution-Role
```

6. Select **Add container**.

7. Enter the Container name:

```text
frontend
```

8. Enter the Frontend Docker Image from Amazon ECR.

For example:

```text
<AWS_ACCOUNT_ID>.dkr.ecr.<AWS_REGION>.amazonaws.com/<FRONTEND_REPOSITORY>:latest
```

9. Configure Port Mapping according to the Port used by the Frontend Container.

For example:

```text
Container port: 80
Protocol: TCP
```

10. Configure the Environment Variables required by the Frontend.

11. Configure CloudWatch Logs with the following Log Group:

```text
/ecs/neonfoodmap-frontend
```

12. Review the configuration and select **Create**.

![alt text](image.png)

![alt text](image-1.png)

![alt text](image-2.png)

---

#### Step 4. Configure CloudWatch Log Groups for the Backend and Frontend

CloudWatch Logs are used to centralize logs from ECS Containers for monitoring application activity and troubleshooting.

1. Navigate to the **Amazon CloudWatch** service.

2. Select **Logs → Log groups**.

3. Select **Create log group**.

4. Create a Log Group for the Backend:

```text
/ecs/neonfoodmap-backend
```

5. Select **Create**.

6. Continue creating a Log Group for the Frontend:

```text
/ecs/neonfoodmap-frontend
```

7. Verify that both Log Groups appear in the list.

8. Compare the Log Group names in the Task Definitions with the Log Groups that were created.

| Container | CloudWatch Log Group        |
| --------- | --------------------------- |
| Backend   | `/ecs/neonfoodmap-backend`  |
| Frontend  | `/ecs/neonfoodmap-frontend` |

> When the ECS Task starts, Container logs are sent to the corresponding Log Group through the `awslogs` configuration.

---

#### Step 5. Configure Environment Variables and Secrets for RDS and API Keys

Application configuration information is divided into two groups: **Environment Variables** and **Secrets**.

##### 5.1. Configure Environment Variables

In the Backend Task Definition, under **Environment variables**, add configuration variables that do not contain sensitive information.

For example:

```text
DJANGO_SETTINGS_MODULE=config.settings
DEBUG=False
ALLOWED_HOSTS=<DOMAIN>
AWS_REGION=<AWS_REGION>
```

The actual values should be replaced according to the deployment environment.

##### 5.2. Configure RDS Connection Information

Database connection information may include:

```text
DB_HOST
DB_NAME
DB_USER
DB_PASSWORD
DB_PORT
```

Sensitive information such as `DB_PASSWORD` should be stored in **AWS Secrets Manager**.

In the Task Definition:

1. Open the **Secrets** section of the Backend Container.

2. Select **Add secret**.

3. Enter the Environment Variable name used by the application.

4. Select the corresponding Secret in **AWS Secrets Manager**.

For example:

```text
Name: DB_PASSWORD
ValueFrom: <RDS Database Secret>
```

##### 5.3. Configure API Keys

For API Keys or authentication credentials for external services, follow the same procedure:

```text
Name: API_KEY
ValueFrom: <API Key Secret>
```

5. Verify that all Environment Variables and Secrets have been configured correctly.

6. Do not store the RDS password or API Key directly in the source code, Dockerfile, or configuration files committed to Git.

> The Task must be granted the appropriate permissions to access Secrets from AWS Secrets Manager.

---

#### Step 6. Create a Task Execution Role with ECR Access

The Task Execution Role allows ECS to perform the operations required during Task startup.

1. Navigate to **AWS Console → IAM**.

2. Select **Roles**.

3. Find the Role:

```text
NeonFoodmap-ECS-TaskExecution-Role
```

![alt text](image-3.png)

4. Open the Role and select the **Permissions** tab.

5. Verify that the Role has the necessary permissions to:

- Pull Docker Images from Amazon ECR.
- Write Container Logs to Amazon CloudWatch Logs.
- Access Secrets from AWS Secrets Manager if the Task Definition uses Secrets.

![alt text](image-4.png)

6. For ECR, the Role must have the appropriate permissions for ECS/Fargate to authenticate and pull Images from the Repository.

![alt text](image-6.png)

7. Return to **Amazon ECS → Task definitions**.

8. Open the Backend Task Definition.

9. Verify that the following **Task execution role** is being used:

```text
NeonFoodmap-ECS-TaskExecution-Role
```

![alt text](image-7.png)

10. Perform the same verification for the Frontend Task Definition.

---

### Verification

After completing the six steps above, verify the configuration before creating the ECS Service:

| Component                | Expected Result                                                     |
| ------------------------ | ------------------------------------------------------------------- |
| ECS Cluster              | Created and in `ACTIVE` status                                      |
| Backend Task Definition  | Created with CPU 256 and RAM 512 MiB                                |
| Frontend Task Definition | Created with CPU 256 and RAM 512 MiB                                |
| Backend Image            | Points to the Backend Repository in ECR                             |
| Frontend Image           | Points to the Frontend Repository in ECR                            |
| CloudWatch Logs          | Contains `/ecs/neonfoodmap-backend` and `/ecs/neonfoodmap-frontend` |
| Environment Variables    | Configured                                                          |
| Secrets                  | Configured through Secrets Manager                                  |
| Task Execution Role      | Assigned to the Backend and Frontend                                |
| ECR Permission           | Allows ECS to pull the Image                                        |

After the above configurations are completed, the system is ready to create the **ECS Service** and deploy the Tasks across Subnets belonging to **AZ1 and AZ2**.

![](images/5-Workshop/5.4-Neon-Deployment/image039.png)
![](images/5-Workshop/5.4-Neon-Deployment/image040.png)
![](images/5-Workshop/5.4-Neon-Deployment/image041.png)
![](images/5-Workshop/5.4-Neon-Deployment/image042.png)
![alt text](image-8.png)

---
