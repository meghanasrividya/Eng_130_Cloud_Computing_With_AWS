### Creating new EC2

- **Step 1:**  Go to EC2 dashboard and click on the launch instance 

- **Step 2:**  Give the name of the Ec2 instance in the below format

![image](https://user-images.githubusercontent.com/97250268/199283566-d9e1a1de-53cb-47d5-a986-e47cbbd47ff8.png)



- **Step 3:** Select the OS for the EC2 instance . Here I selected 

![image](https://user-images.githubusercontent.com/97250268/199284077-b52ccd45-b805-455e-87d5-076e9964efd0.png)



- **Step 4:** Select the instance type as below

![image](https://user-images.githubusercontent.com/97250268/199284283-9390e26c-f3ab-4204-8d05-18e0ee23a93d.png)



- **Step 5:** Give the key - pair  as eng130

![image](https://user-images.githubusercontent.com/97250268/199284560-e5f12fee-940a-4ef6-b00d-0a901749802d.png)



- **Step 6 :** Go to the network settings and create a security group if you are creating the instance for the first time .If you have already created select security group you created from the drop down box.

![image](https://user-images.githubusercontent.com/97250268/199285808-da01d5e3-49de-41b8-9af5-e9a53b078d71.png)



- **Step 7:**  create security group rules .Select My IP in the source type 

![image](https://user-images.githubusercontent.com/97250268/199286131-a772cad0-00ae-4701-8f95-c541635bc040.png)



- **Step 8:** Select the Configuration

![image](https://user-images.githubusercontent.com/97250268/199286490-fe2023eb-66a5-4519-b4c0-a826399748d0.png)

- **Step 9:** Click on the launch instance. You can see the launching instance is successful.Click on the link

![image](https://user-images.githubusercontent.com/97250268/199288700-2a08546a-bfc3-40f2-9311-fc9a5873be39.png)


- **Step 10:** Select the EC2 instance and click on connect 

![image](https://user-images.githubusercontent.com/97250268/199288401-b0e74413-b68e-480a-ac8e-46c9505441e8.png)

- **Step 11:** Select EC2 instance connect copy the public IP address and paste in the browser 

![image](https://user-images.githubusercontent.com/97250268/199290844-7ad88b6d-97e6-431d-89cb-bfd5e370aa4d.png)

- **Step 12:** The browser shows the page not reachable 

- **Step 13:** Go to the SSH client and copy the below command and SSH into your EC2 instance

![image](https://user-images.githubusercontent.com/97250268/199299309-ee942436-c537-4741-8507-1ac74ca6b674.png)


- **Step 14:** Give the command `sudo apt-get update -y` 
- **Step 15:** Give the command  `sudo apt-get upgrade -y`
- **Step 16:** Give the command  `sudo apt-get install nginx -y`
- **Step 17:**  Now go into the browser in which you have given the public IP address and refresh the page .

![image](https://user-images.githubusercontent.com/97250268/199301094-9de83952-6b6d-43cb-bd26-2a4e6e207d74.png)


## Steps to set up reverse proxy:

- Give the command  to open the default file `sudo nano /etc/nginx/sites-available/default`

- Replace the location block with the below lines. change the localhost:3000

![image](https://user-images.githubusercontent.com/97250268/199302765-5a299db5-6f37-4b61-a0e8-b4860b6c2b98.png

- To check whether the sysnx is correct `sudo nginx -t`
- Give the command `sudo systemctl restart nginx`
- Now to check whether reverse proxy is working ,go to the browser in which you have given the public IP address and refresh the page .


![image](https://user-images.githubusercontent.com/97250268/199303555-8d5a360e-a693-467b-958c-3eb82d5d1ad8.png)










