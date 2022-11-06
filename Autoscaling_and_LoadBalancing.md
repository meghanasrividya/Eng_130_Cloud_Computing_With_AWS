### Autoscaling and Load Balancing:

### Autoscaling:

- AWS Auto Scaling monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost. Using AWS Auto Scaling, it's easy to setup application scaling for multiple resources across multiple services in minutes.

- Elastic Load Balancing automatically distributes your incoming traffic across multiple targets, such as EC2 instances, containers, and IP addresses, in one or more Availability Zones. It monitors the health of its registered targets, and routes traffic only to the healthy targets.


 ![image](https://user-images.githubusercontent.com/97250268/200147316-8aa7eb05-c932-4280-8c42-c2d66f626383.png)
 
 ### Steps to create Launch Template:
 
 - Click on launch templates under instances in AWS console
 
 ![image](https://user-images.githubusercontent.com/97250268/200170203-c6723487-fc15-4714-b621-ca7252d9937a.png)
 
 - Click on create Launch template 
 
 ![image](https://user-images.githubusercontent.com/97250268/200170309-09b5149e-ab37-42da-89dc-7c9dfd7bd7d8.png)

- Choose a name for `Launch template name - required` for instance as `eng130-meghana-lt-app`
- Copy the same thing under `Template version description`.
- Check/click on `Provide guidance to help me set up a template that I can use with EC2 Auto Scaling` under `Auto Scaling guidance  Info`
- Add tag under `Template tags` (It's optional) `Key: Name` ,`Value:eng130-meghana-lt-app`
- Under `Application and OS Images (Amazon Machine Image) - required Info` select `Ubuntu Server 18.04 LTS (HVM), SSD Volume Type`
- Under `Instance type` select `t2-micro`
![image](https://user-images.githubusercontent.com/97250268/200170984-8f7efe79-d7ac-428e-bd5a-4893d433777e.png)
- Choose the KeyPair as `eng130`
- Create new security group as `en130-meghana-asg-app`
- Copy the same under description
- Select the default VPC
- Add the Security group rules.
   - `Type:ssh` ,`Source type: My IP`
   - `Type:HTTP`, Source type:Anywhere`
- Under EBS, need not change keep the same `(8 GiB, EBS, General purpose SSD (gp2))`
- Under Resource tags 

![image](https://user-images.githubusercontent.com/97250268/200171558-5b77d56f-2a99-4dc7-b1ef-f29b29eaf5ef.png)

- Under the Advancd Details , got User data and add below commands
```
#!/bin/bash
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install nginx -y
sudo systemctl restart nginx
sudo systemctl enable nginx
```

- Click on `create launch template`,you can see the message successfully created launch template.

 ![image](https://user-images.githubusercontent.com/97250268/200171752-cab22333-11f5-4ec0-b02f-17ad4249fdf0.png)


### Steps to Create AutoScaling Group:

- Under `Auto Scaling` select `Auto Scaling Groups` and click on ` Create Auto Scaling Group`
- Give the name for `Auto scaling group` and select the luanch template and click on next.
- Select the default VPC and under `Avaliabilty zones and subnets` select the subnets and click on next.
![image](https://user-images.githubusercontent.com/97250268/200172485-d005f3b0-dc17-4959-be24-8b85b6e6cc85.png)
- Under `Load balancing - optionalInfo` select `Attach to a new load balancer`
- Under  `Load balancer type` select `Application Load Balancer`
- Give the name under `Load balancer name` as `eng130-meghana-app-asg-alb` ( do not include underscores in the name)
- Under the `Load Balancer Scheme` select `Internet Facing`
- Under `Liseters and routing` create new target group
- Under `Health checks - optional` check ELB and click on next
- Under the Group size  ,select the Desired Capacity, Minimum Capacity and Maximum Capacity
![image](https://user-images.githubusercontent.com/97250268/200173324-7b7db09f-db08-414d-9594-ee557736b6f7.png)
- Under Scaling Policies, select `Target Tracking scaling Policy`
![image](https://user-images.githubusercontent.com/97250268/200173416-69664093-e2ee-4513-9b93-cbbecd9f0611.png)

- click next-->next-->next--> review and click on `Create AutoScaling Group`

![image](https://user-images.githubusercontent.com/97250268/200173683-9d9bf999-447d-4e87-9fc5-9032d75aa9b7.png)
















  



