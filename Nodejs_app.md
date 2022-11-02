### How to copy the folders from local machine to EC2 instance.
- Use the below command to copy the folders from local machine to database

- `scp -i eng130.pem -r /C/Users/MA/eng_130_virtualisation/app/  ubuntu@ec2-34-245-81-47.eu-west-1.compute.amazonaws.com:/home/ubuntu/~`
-  ```sudo apt-get install python -y
      sudo apt-get install software-properties-common -y
      curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
      
      sudo apt-get install nodejs -y
      sudo npm install pm2 -g

     # navigate to the app folder
     sudo npm install
     sudo systemctl restart nginx
     npm start
     ```
### How to setup reverse proxy

- Replace the location block with the below lines. change the localhost:3000
  ```proxy_pass http://localhost:3000;
     proxy_http_version 1.1;
     proxy_set_header Upgrade $http_upgrade;
     proxy_set_header Connection 'upgrade';
     proxy_set_header Host $host;
     proxy_cache_bypass $http_upgrade;
   ```
 - Make sure you delete the line `tryfiles..404` inside the location block only then you are able to view the image of the app.

- To check whether the syntax is correct `sudo nginx -t`
- Give the command `sudo systemctl restart nginx`

