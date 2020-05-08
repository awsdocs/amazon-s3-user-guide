# How do I set up a destination to receive event notifications?<a name="setup-event-notification-destination"></a>

Before you can enable event notifications for your bucket you must set up one of the following destination types:

**An Amazon SNS topic**  
Amazon Simple Notification Service \(Amazon SNS\) is a web service that coordinates and manages the delivery or sending of messages to subscribing endpoints or clients\. You can use the Amazon SNS console to create an Amazon SNS topic that your notifications can be sent to\. The Amazon SNS topic must be in the same region as your Amazon S3 bucket\. For information about creating an Amazon SNS topic, see [Getting Started](https://docs.aws.amazon.com/sns/latest/dg/GettingStarted.html) in the *Amazon Simple Notification Service Developer Guide*\.  
Before you can use the Amazon SNS topic that you create as an event notification destination, you need the following:  
+ The Amazon Resource Name \(ARN\) for the Amazon SNS topic
+ A valid Amazon SNS topic subscription \(the topic subscribers are notified when a message is published to your Amazon SNS topic\)
+ A permissions policy that you set up in the Amazon SNS console \(as shown in the following example\)

  ```
  {
    "Version":"2012-10-17",
    "Id": "__example_policy_ID",
    "Statement":[
      {
        "Sid": "example-statement-ID",
        "Effect":"Allow",
        "Principal": "*",
        "Action": "SNS:Publish",
        "Resource":"arn:aws:sns:region:account-number:topic-name", 
        "Condition": { 
          "ArnEquals": {
  	       "aws:SourceArn": "arn:aws:s3:::bucket-name"
           }
         } 
       }
     ]
  }
  ```

**An Amazon SQS queue**  
You can use the Amazon SQS console to create an Amazon SQS queue that your notifications can be sent to\. The Amazon SQS queue must be in the same region as your Amazon S3 bucket\. For information about creating an Amazon SQS queue, see [Getting Started with Amazon SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-getting-started.html) in the *Amazon Simple Queue Service Developer Guide*\.   
Before you can use the Amazon SQS queue as an event notification destination, you need the following:  
+ The Amazon Resource Name \(ARN\) for the Amazon SQS topic
+ A permissions policy that you set up in the Amazon SQS console \(as shown in the following example\)

  ```
  {
    "Version":"2012-10-17",
    "Id": "__example_policy_ID",
    "Statement":[
      {
        "Sid": "example-statement-ID",
        "Effect":"Allow",
        "Principal": "*",
        "Action": "SQS:*",
        "Resource":"arn:aws:sqs:region:account-number:queue-name", 
        "Condition": { 
          "ArnEquals": {
  	       "aws:SourceArn": "arn:aws:s3:::bucket-name"
           }
         } 
       }
     ]
  }
  ```

**A Lambda function**  
You can use the AWS Lambda console to create a Lambda function\. The Lambda function must be in the same region as your S3 bucket\. For information about creating a Lambda function, see the [AWS Lambda Developer Guide](https://docs.aws.amazon.com/lambda/latest/dg/)\.  
Before you can use the Lambda function as an event notification destination, you must have the name or the ARN of a Lambda function to set up the Lambda function as a event notification destination\. 

**Warning**  
If your notification ends up writing to the bucket that triggers the notification, this could cause an execution loop\. For example, if the bucket triggers a Lambda function each time an object is uploaded, and the function uploads an object to the bucket, then the function indirectly triggers itself\. To avoid this, use two buckets, or configure the trigger to only apply to a prefix used for incoming objects\.  
For more information and an example of using Amazon S3 notifications with AWS Lambda, see [Using AWS Lambda with Amazon S3](https://docs.aws.amazon.com/lambda/latest/dg/with-s3.html) in the *AWS Lambda Developer Guide*\. 