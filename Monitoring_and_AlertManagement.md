### Monitoring And Alert Management:

## Monitoring:

- Gain complete visibility and control of your cloud resources and application workloads running on your AWS environment with Applications Manager's AWS monitoring. Instantly detect and fix issues, respond to business-critical alerts, and optimize resource usage for improved performance and cost savings.

 ![image](https://user-images.githubusercontent.com/97250268/200147743-c60e1d2b-111b-44e7-bce8-6f736cc33f4d.png)
 
 
 ## Cloud Watch:
 
 - Amazon CloudWatch collects and visualizes real-time logs, metrics, and event data in automated dashboards to streamline your infrastructure and application maintenance.

![image](https://user-images.githubusercontent.com/97250268/200147945-f50931b5-b3a6-4ff5-9976-506912764d3a.png)

- CloudWatch is a service used to monitor your AWS resources and applications that you run on AWS in real time. CloudWatch is used to collect and track metrics that measure your resources and applications.

- It displays the metrics automatically about every AWS service that you choose.

- You can create the dashboard to display the metrics about your custom application and also display the metrics of custom collections that you choose.

- You can also create an alarm to watch metrics. For example, you can monitor CPU usage, disk read and disk writes of Amazon EC2 instance to determine whether the additional EC2 instances are required to handle the load or not. It can also be used to stop the instance to save money.


![image](https://user-images.githubusercontent.com/97250268/200147760-9bcaddbf-7fab-4be1-b80a-736d9378d5d0.png)

Following are the terms associated with CloudWatch:

- Dashboards: CloudWatch is used to create dashboards to show what is happening with your AWS environment.

- Alarms: It allows you to set alarms to notify you whenever a particular threshold is hit.

- Logs: CloudWatch logs help you to aggregate, monitor, and store logs.

- Events: CloudWatch help you to respond to state changes to your AWS resources.

## SNS:

- SNS stands for Simple Notification Service.
- It is a web service which makes it easy to set up, operate, and send a notification from the cloud.
- It provides developers with the highly scalable, cost-effective, and flexible capability to publish messages from an application and sends them to other applications.
- It is a way of sending messages. When you are using AutoScaling, it triggers an SNS service which will email you that "your EC2 instance is growing".
- SNS can also send the messages to devices by sending push notifications to Apple, Google, Fire OS, and Windows devices, as well as Android devices in China with Baidu Cloud Push.
- Besides sending the push notifications to the mobile devices, Amazon SNS sends the notifications through SMS or email to an Amazon Simple Queue Service (SQS), or to an HTTP endpoint.
- SNS notifications can also trigger the Lambda function. When a message is published to an SNS topic that has a Lambda function associated with it, Lambda function is invoked with the payload of the message. Therefore, we can say that the Lambda function is invoked with a message payload as an input parameter and manipulate the information in the message and then sends the message to other SNS topics or other AWS services.
- Amazon SNS allows you to group multiple recipients using topics where the topic is a logical access point that sends the identical copies of the same message to the subscribe recipients.
- Amazon SNS supports multiple endpoint types. For example, you can group together IOS, Android and SMS recipients. Once you publish the message to the topic, SNS delivers the formatted copies of your message to the subscribers.
- To prevent the loss of data, all messages published to SNS are stored redundantly across multiple availability zones.

![image](https://user-images.githubusercontent.com/97250268/200147781-b7fd0a41-cfc6-4116-b75b-4e663847535a.png)

### Steps to setup SNS :
- Create an EC2 instance
- Select the EC2 instance --->Monitoring--->Add to Dashboard

![image](https://user-images.githubusercontent.com/97250268/200175729-c929a168-1c6b-459d-8259-8a32767a0741.png)

- Select or create dashboadoard and `Add to Dashboard`

![image](https://user-images.githubusercontent.com/97250268/200175815-4af1b070-075f-429e-8994-f74fed34fff6.png)

- Select the metric and specify the conditions 

![image](https://user-images.githubusercontent.com/97250268/200176722-9ed79141-302b-44d0-a277-5f9ff30babb1.png)

- Create a new topic and give the email address to recieve notifications

![image](https://user-images.githubusercontent.com/97250268/200177005-c1e70107-4a24-4b84-af70-84e90f7aa914.png)

- Add alarm name and description and click next
![image](https://user-images.githubusercontent.com/97250268/200177102-bb4788fa-6cb9-48ee-9df2-83f0eb855e68.png)

- Click on create alarm

![image](https://user-images.githubusercontent.com/97250268/200177149-5f05a73d-f000-4ff4-a7e2-e316ba7dbcbc.png)
 
 - You can see the message successfully created alarm
 
 ![image](https://user-images.githubusercontent.com/97250268/200177242-d1a10f1c-0f88-4f71-af47-7c4b8c32534c.png)

- Confirm the subscription 

![image](https://user-images.githubusercontent.com/97250268/200177631-cb16378f-8204-4bdf-b3d2-73e5238bf4cf.png)

- You will start receiving the notifications when CPU >=20
![image](https://user-images.githubusercontent.com/97250268/200178218-c85f1582-a33b-477f-b531-cef6ab440c9b.png)

