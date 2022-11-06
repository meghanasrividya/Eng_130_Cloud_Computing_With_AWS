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

