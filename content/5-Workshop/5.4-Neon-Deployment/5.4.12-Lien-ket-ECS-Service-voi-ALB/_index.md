---

title : "Connecting the ECS Service to the ALB"
date : 2024-01-01
weight : 12
chapter : false
pre : " <b> 5.4.12. </b> "
--------------------------

### 5.4.12. Connecting the ECS Service to the ALB

To allow ECS to automatically register Tasks with the target group, load balancing must be configured in the ECS Service.

1. Open the **ECS Console**.
2. Select the `neonfoodmap-cluster` cluster.
3. Select the Frontend or Backend Service.
4. Edit or create the Service.
5. Under **Load balancing**:

   * Select `Application Load Balancer`.
   * Select `ALB-NeonFoodMap`.
   * Select the corresponding Container.
   * Select the `80:HTTP` listener.
   * Select the corresponding Target Group.
6. Save the configuration.

