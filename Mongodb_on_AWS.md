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
