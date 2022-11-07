### What is VPC

![image](https://user-images.githubusercontent.com/97250268/200319917-5dc37804-cbe3-448b-8a52-f8ab0f82d8da.png)

- VPC stands for Virtual Private Cloud.
- Amazon Virtual Private Cloud (Amazon VPC) provides a logically isolated area of the AWS cloud where you can launch AWS resources in a virtual network that you define.
- You have complete control over your virtual networking environment, including a selection of your IP address range, the creation of subnets, and configuration of route tables and network gateways.
- You can easily customize the network configuration for your Amazon Virtual Private Cloud. For example, you can create a public-facing subnet for web servers that can access to the internet and can also place your backend system such as databases or application servers to a private-facing subnet.
- You can provide multiple layers of security, including security groups and network access control lists, to help control access to Amazon EC2 instances in each subnet.

### What is Internet Gateway:
- A computer that sits between different networks or applications. The gateway converts information, data or other communications from one protocol or format to another. A router may perform some of the functions of a gateway. An Internet gateway can transfer communications between an enterprise network and the Internet.

### What is Route Table
- The route table contains existing routes with targets other than a network interface, Gateway Load Balancer endpoint, or the default local route. The route table contains existing routes to CIDR blocks outside of the ranges in your VPC. Route propagation is enabled for the route table.

### What is CIDR blocks
- CIDR blocks are groups of addresses that share the same prefix and contain the same number of bits. The combination of multiple connecting CIDR blocks into a larger whole, sharing a common network prefix, is what constitutes supernetting. The size of CIDR blocks can be determined by the length of the prefix.

### What is subnet
- A subnet, or subnetwork, is a network inside a network. Subnets make networks more efficient. Through subnetting, network traffic can travel a shorter distance without passing through unnecessary routers to reach its destination.

### What is NACL
- NACL stands for Network Access Control Lists.
- It is a security layer for your VPC that controls the traffic in and out of one or more subnets.
- It is an optional layer for your VPC.
- You can set up a Network ACL similar to the security group that adds an additional layer of security to your VPC.

### What is the difference between NACL and Security Groups

![image](https://user-images.githubusercontent.com/97250268/200323512-1177f491-736c-416c-b6bf-d7b2c81c016b.png)

### Steps to create VPC and 2 tier architecture inside the VPC

![image](https://user-images.githubusercontent.com/97250268/200359849-3b2959fa-3c6c-408e-9259-44cd1c6da483.png)


- Step 1: Create a VPC
   - Click on Create VPC
   - Click on vpc only under `Resources to create`
   - Give the name tag `eng130-meghana-vpc`
   - Under IPV4 CIDR give the CIDR of VPC `10.0.0.0/16`
   - Click on `create vpc`
- Step 2: Create an internet gateway
   - Go to Internet gateways , then click on `create Internet gateway`
- 2.1 :attach the IG to our VPC
- Step 3: Create a public subnet 10.0.5.0/24
- Step 4: route table
- 4.1: add routes to connect to IG
- 4.2 associate RT to public subnet
- Create the private subnet
- Launch EC2 using the node app AMI and give the security groups
- Security Group rules for app :ssh - my ip,80-anywhere,3000-anywhere
- Launch EC2 using the mongodb AMI and give the security group
- Security Group rules for mongodb: 27017 from CIDR of app
**In app instance**
- SSH into the app instance and create the enviromental variable using the private ip of mongodb
- `ubuntu@ip-10-0-5-118:~$ export DB_HOST=mongodb://10.0.17.33:27017/posts`
-  We have to go inside the app folder and give command`node seeds/seed.js`
-  Then give command  `npm start`
-  Copy the public ip of the app instance and paste in the browser `http://3.252.247.92/posts`
-  You can see the posts.
 ![image](https://user-images.githubusercontent.com/97250268/200358208-eadeb8ea-d367-473a-8e4b-867af8dfb7d0.png)

