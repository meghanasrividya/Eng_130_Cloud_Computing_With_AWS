### AWS Two Tier Architecture

![image](https://user-images.githubusercontent.com/97250268/199527934-c0b34f07-d79e-43ff-b75b-e2d2a445c53f.png)

### Steps to connect MongoDb  with th APP:

For the Mongodb EC2 instance  add the security group 

![image](https://user-images.githubusercontent.com/97250268/199565012-6a225766-68ff-4a01-96f4-3608586df2b7.png)


- Install the mongodb in the db vm
```sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927
echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt-get update -y
sudo apt-get upgrade -y

# sudo apt-get install mongodb-org=3.2.20 -y
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
# sudo apt-get install mongodb-org=3.2.20 -y
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

# if mongo is is set up correctly these will be successful
sudo systemctl restart mongod
sudo systemctl enable mongod
```

- Change the mongod.conf file
- `cd /etc`
- Give the command `sudo nano mongod.conf`
-   port: 27017
    bindIp: 0.0.0.0
- `sudo systemctl restart mongodb`
- `sudo systemctl restart mongodb`

- Go to the app machine create 
- create an env var called DB_HOST=mongodb:ipaddressofmongodb//:27017/posts
- printenv DB_HOST
- Go inside app folder and node
- npm start
  `node seeds/seed.js`
- https://[ipaddress_of_app]/posts

### What is Disaster Recovery
- Disaster recovery involves a set of policies, tools, and procedures to enable the recovery or continuation of vital technology infrastructure and systems following a natural or human-induced disaster.
#### What is S3?
- Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can use Amazon S3 to store and protect any amount of data for a range of use cases, such as data lakes, websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics. Amazon S3 provides management features so that you can optimize, organize, and configure access to your data to meet your specific business, organizational, and compliance requirements.

#### What are the benefits of S3?
- Compliance Capability
- Flexible Management
- Flexible data transfer
- A systematic way of work
- Durability, Availability, and Scalability

#### What are the use cases of S3?

- Data Archiving
- Large Data Storage and Analytics
- Backup and recovery


## Disastor Recovery Diagram


![image](https://user-images.githubusercontent.com/97250268/199713753-807b52d1-ce3a-4ed3-a4fd-1d25aab590ab.png)

### Steps to access S3

- ssh into the EC2 instance
- Install python 3 `sudo apt-get install python3`
- Install pip3 `sudo apt-get intall python3-pip`
- Install awscli `sudo pip3 install awscli`
- Give the command `ams configure`
- Give access key, secret key, region name,outpput format
- To check whether connected to S3 , we have to give the command `aws s3 ls`
- We can the list of items that s3 bucket have

