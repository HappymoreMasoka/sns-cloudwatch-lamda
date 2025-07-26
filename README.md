# AWS SNS Notification System with Lambda and CloudWatch

## 📌 Overview
This project demonstrates how to use **Amazon SNS (Simple Notification Service)** with **AWS Lambda** and **CloudWatch** to send automated notifications (email alerts) when a Lambda function encounters errors.

By integrating SNS with a CloudWatch alarm, this setup ensures that failures in serverless functions are detected in real time and trigger immediate alerts.

---

## 🏗️ Architecture
1. **Lambda Function** – A simple Python function that simulates an error.
2. **CloudWatch** – Monitors Lambda metrics (e.g., `Errors`) and triggers an alarm when errors occur.
3. **SNS Topic** – Sends an email notification when the CloudWatch alarm is triggered.

---

## ⚙️ Setup Instructions

### **1. Create Lambda Function**
- Go to **AWS Console > Lambda > Create Function**
- Use Python 3.x runtime and add the following code:
  ```python
  def lambda_handler(event, context):
      raise Exception("Test error for SNS alert")

2. Create an SNS Topic
Go to AWS Console > SNS > Create topic

Choose Standard type and give it a name (e.g., LambdaAlertTopic).

3. Subscribe an Email to SNS
Under the topic, create a subscription:

Protocol: Email

Endpoint: Your email (e.g., you@example.com)

Check your inbox and confirm the subscription.

4. Create a CloudWatch Alarm
Go to CloudWatch > Alarms > Create Alarm.

Browse metrics: AWS/Lambda > By Function Name > Errors.

Set threshold: Errors >= 1.

Choose Send notification to SNS topic.

5. Test
Re-invoke the Lambda function.

Check your email for the SNS notification.

🧰 Tools & Technologies
AWS Lambda – Serverless function for triggering events.

Amazon SNS – Notification service (email alerts).

Amazon CloudWatch – Monitoring and alarms.

Python (boto3) – (Optional) Automate SNS topic and subscription creation.

