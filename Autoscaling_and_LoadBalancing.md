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
``












  



