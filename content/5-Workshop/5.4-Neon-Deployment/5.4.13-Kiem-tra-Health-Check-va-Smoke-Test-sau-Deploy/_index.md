---

title : "Checking Health Checks and Smoke Tests After Deployment"
date : 2024-01-01
weight : 13
chapter : false
pre : " <b> 5.4.13. </b> "
--------------------------

### 5.4.13. Checking Health Checks and Smoke Tests After Deployment

After the ECS Tasks have started successfully, check the status of the Target Groups.

The following items should be verified:

* The Frontend Target Group changes to `Healthy`.

![alt text](/images/image-1.png)

* The Backend Target Group changes to `Healthy`.

![alt text](/images/image.png)

* The ALB DNS name is accessible through a browser.

```text
http://alb-neonfoodmap-406336237.ap-southeast-1.elb.amazonaws.com/map
```

* The `/api/...` endpoint returns a valid response.

```text
http://alb-neonfoodmap-406336237.ap-southeast-1.elb.amazonaws.com/api/
```

![alt text](/images/image-2.png)
