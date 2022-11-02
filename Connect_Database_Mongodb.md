![image](https://user-images.githubusercontent.com/97250268/199527934-c0b34f07-d79e-43ff-b75b-e2d2a445c53f.png)

### Steps to connect MongoDb  with th APP:

- Install the mongodb in the db vm
```sudo apt-get update
sudo apt-get upgrade -y
curl -fsSL https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
sudo apt update
sudo apt install mongodb-org -y
sudo apt install net-tools -y
rm /etc/mongod.conf
cp /home/vagrant/sync/mongod.conf /etc/mongod.conf
sudo systemctl start mongod.service
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
- create an env var called DB_HOST=mongodb://192.168.10.150:27017/posts
- printenv DB_HOST
