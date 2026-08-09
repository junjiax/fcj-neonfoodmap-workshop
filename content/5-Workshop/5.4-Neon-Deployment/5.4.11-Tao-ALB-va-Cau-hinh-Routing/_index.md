---

title : "Creating an Application Load Balancer and Configuring Routing"
date : 2024-01-01
weight : 11
chapter : false
pre : " <b> 5.4.11. </b> "
--------------------------

### 5.4.11. Creating an Application Load Balancer and Configuring Routing

#### 1. Creating a Security Group for the ALB

1. Open **EC2 Console → Security Groups**.
2. Select **Create security group**.
3. Configure:

   * Name: `alb-sg`
   * Description: `Security Group for the Public Application Load Balancer`
   * VPC: Select the project's VPC.
4. Add inbound rules:

   * HTTP `80` from `0.0.0.0/0`
   * HTTPS `443` from `0.0.0.0/0`
5. Keep the default outbound rule.

![alt text](image.png)

![alt text](image-1.png)

#### 2. Creating Target Groups for the Frontend and Backend

* `TG-NeonFoodMap-FE` for the Frontend
* `TG-NeonFoodMap-BE` for the Backend

Main configurations:

* Target type: `IP addresses`
* Protocol/Port: Frontend `HTTP:80`, Backend `HTTP:8000`
* Health check protocol: `HTTP`
* Health check path: `/` or `/api/health`
* Healthy threshold: `2`
* Unhealthy threshold: `2`
* Interval: `30 seconds`

![](images/5-Workshop/5.4-Neon-Deployment/image025.png)
![](images/5-Workshop/5.4-Neon-Deployment/image026.png)
![](images/5-Workshop/5.4-Neon-Deployment/image027.png)
![](images/5-Workshop/5.4-Neon-Deployment/image028.png)
![](images/5-Workshop/5.4-Neon-Deployment/image029.png)

#### 3. Creating an Application Load Balancer

1. Open **EC2 Console → Load Balancers**.
2. Select **Create load balancer → Application Load Balancer**.
3. Configure:

   * Name: `ALB-NeonFoodMap`
   * Scheme: `Internet-facing`
   * IP address type: `IPv4`
4. Select the appropriate public Subnets in the VPC.
5. Select the `alb-sg` security group.
6. Configure the `HTTP:80` listener and set the default route to the Frontend target group.
7. Create the Load Balancer.

![](images/5-Workshop/5.4-Neon-Deployment/image031.png)
![](images/5-Workshop/5.4-Neon-Deployment/image032.png)
![](images/5-Workshop/5.4-Neon-Deployment/image033.png)
![](images/5-Workshop/5.4-Neon-Deployment/image034.png)

#### 4. Creating a Listener Rule for the API Path

1. Open the ALB → **Listeners and rules**.

![alt text](image-2.png)

2. Select the `HTTP:80` listener.
3. Add a rule:

   * Name: `route-backend-api`
   * Condition: Path `/api/*`
   * Action: Forward to the Backend target group.
4. Save the rule.

![alt text](image-3.png)
