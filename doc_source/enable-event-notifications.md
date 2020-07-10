# How do I enable and configure event notifications for an S3 Bucket?<a name="enable-event-notifications"></a>

You can enable certain Amazon S3 bucket events to send a notification message to a destination whenever the events occur\. This section explains how to use the Amazon S3 console to enable event notifications\. For information about using event notifications with the AWS SDKs and the Amazon S3 REST APIs, see [Configuring Amazon S3 Event Notifications](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html) in the *Amazon Simple Storage Service Developer Guide*\. 

**Topics**
+ [Event notification types](#enable-event-notifications-types)
+ [Event notification destinations](#s3-event-notification-destinations)
+ [Enabling and configuring event notifications](#enable-event-notifications-how-to)
+ [More info](#enable-event-notifications-moreinfo)

## Event notification types<a name="enable-event-notifications-types"></a>

When you configure event notifications for a bucket, you must specify the type of events for which you want to receive notifications\. For a complete list of event types, see [Supported Event Types](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html#supported-notification-event-types) section in the *Amazon Simple Storage Service Developer Guide*\. 

In the Amazon S3 console, you have the following options for configuring event notifications\. You can choose a single option or multiple options\.
+ **Object creation**
  + **ObjectCreated \(All\)** – Receive a notification when an object is created in your bucket for any of the following object creation actions: **Put**, **Post**, **Copy**, and **Multipart upload completed**\.
  +  **Put**, **Post**, **Copy**, and **Multipart upload completed** – Receive a notification for one of these specific object creation actions\.
+ **Object deletion**
  + **ObjectDelete \(All\)** – Receive a notification any time an object in your bucket is deleted\.
  + **Delete marker created** – Receive a notification when a delete marker is created for a versioned object\.

     For information about deleting versioned objects, see [Deleting Object Versions](https://docs.aws.amazon.com/AmazonS3/latest/dev/DeletingObjectVersions.html)\. For information about object versioning, see [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html)\.
+ **Object restoration from the S3 Glacier storage class** 
  + **Restore initiated** – Receive a notification for *Initiation* of object restoration\.
  + **Restore completed** – Receive a notification for *Completion* of object restoration\.
+ **Reduced Redundancy Storage \(RRS\) object lost events**
  + **Object in RSS Lost** – Receive a notification that an object of the RRS storage class has been lost
+ **Objects eligible for replication using Amazon S3 Replication Time Control**
  + **Replication time missed threshold** – Receive a notification that an object failed to replicate\.
  + **Replication time completed after threshold** – Receive a notification that an object exceeded the 15\-minute threshold for replication\.
  + **Replication time not tracked** – Receive a notification that an object replicated after the 15\-minute threshold\.
  + **Replication time failed** – Receive a notification that an object that was eligible for replication is no longer being tracked by replication metrics\.

**Note**  
When you delete the last object from a folder, Amazon S3 can generate an object creation event\. When there are multiple objects with the same prefix with a trailing slash \(/\) as part of their names, those objects are shown as being part of a folder in the Amazon S3 console\. The name of the folder is formed from the characters preceding the trailing slash \(/\)\.   
When you delete all the objects listed under that folder, no actual object is available to represent the empty folder\. Under such circumstances, the Amazon S3 console creates a zero\-byte object to represent that folder\. If you enabled event notification for the creation of objects, the zero\-byte object creation action that is taken by the console triggers an object creation event\.  
The Amazon S3 console displays a folder under the following circumstances:  
When a zero\-byte object has a trailing slash \(/\) in its name\. In this case, there is an actual Amazon S3 object of 0 bytes that represents a folder\.
If the object has a slash \(/\) within its name\. In this case, there isn't an actual object representing the folder\.

## Event notification destinations<a name="s3-event-notification-destinations"></a>

When you configure event notifications for a bucket, you also choose the notification destination\. Event notification messages can be sent to the following destinations:
+ **Amazon Simple Notification Service \(Amazon SNS\) topic** – Coordinates and manages the delivery or sending of messages to subscribing endpoints or clients\. For information about the Amazon SNS topic format, see [SNS FAQ](https://aws.amazon.com/sns/faqs/#10)\.
+ **Amazon Simple Queue Service \(Amazon SQS\) queue** – Offers reliable and scalable hosted queues for storing messages as they travel between computers\. For information about Amazon SQS, see [What is Amazon Simple Queue Service?](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/Welcome.html) in the *Amazon Simple Queue Service Developer Guide*\.
+ **AWS Lambda ** – Invoke a Lambda function and provide the event message as an argument\. When you create a Lambda function, you package up and upload your custom code to AWS Lambda\. AWS Lambda uses the AWS infrastructure to run the code on your behalf\. For information about using Lambda with Amazon S3, see [Using AWS Lambda with Amazon S3](https://docs.aws.amazon.com/lambda/latest/dg/with-s3.html) in the *AWS Lambda Developer Guide*\.

For more information about granting the Amazon S3 service principal the permissions required to publish event notifications to a destination, see [Granting Permissions to Publish Event Notification Messages to a Destination](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html#grant-destinations-permissions-to-s3) in the *Amazon S3 Developer Guide*\.

**Warning**  
If your notification ends up writing to the bucket that triggers the notification, this could cause an execution loop\. For example, if the bucket triggers a Lambda function each time an object is uploaded, and the function uploads an object to the bucket, then the function indirectly triggers itself\. To avoid this, use two buckets, or configure the trigger to only apply to a prefix used for incoming objects\.  
For more information and an example of using Amazon S3 notifications with AWS Lambda, see [Using AWS Lambda with Amazon S3](https://docs.aws.amazon.com/lambda/latest/dg/with-s3.html) in the *AWS Lambda Developer Guide*\. 

## Enabling and configuring event notifications<a name="enable-event-notifications-how-to"></a>

Before you can enable event notifications for your bucket, you must set up one of the destination types\. For more information, see [How do I set up a destination to receive event notifications?](setup-event-notification-destination.md)

**To enable and configure event notifications for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to enable events for\.  
![\[Console screenshot of the bucket list with the admin-created bucket selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Console screenshot of the Properties tab.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Under Advanced settings, choose **Events**\.  
![\[Console screenshot of the events section.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-box.png)

1. Choose **Add notification**\.  
![\[Console screenshot of the add notification option in the events dialog box.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-add-notification.png)

1. In **Name**, enter a descriptive name for your event notification\. 

   If you don't enter a name, a GUID is generated and used for the name\.   
![\[Console screenshot of the name box in the events dialog box.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-enter-name.png)

1. Under **Events**, select one or more events\. 

   For a listing of the event types, see [Event notification types](#enable-event-notifications-types)\.  
![\[Console screenshot showing the list of available events.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-add-event-types.png)

1. To filter event notifications by a prefix or suffix, enter a **Prefix** or a **Suffix**\. 

   For example, you can set up a prefix filter so that you receive notifications only when files are added to a specific folder \(for example, `images/`\)\. For more information, see [Configuring Notifications with Object Key Name Filtering](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html#notification-how-to-filtering)\.   
![\[Console screenshot showing the prefix and suffix text boxes.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-add-event-prefix.png)![\[Console screenshot showing the prefix and suffix text boxes.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)![\[Console screenshot showing the prefix and suffix text boxes.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)

1. Choose the event notification destination: **SNS Topic**, **SQS Queue**, or **Lambda Function**\. 

   For a description of the destinations, see [Event notification destinations](#s3-event-notification-destinations)\.  
![\[Console screenshot showing the Send to destination list for the notification.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/s3-bucket-properties-events-destination.png)![\[Console screenshot showing the Send to destination list for the notification.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)![\[Console screenshot showing the Send to destination list for the notification.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)

   When you choose your **Send to** destination, a box appears for you to enter your specific SNS, SQS, or Lambda function destination\. In the example image below, the **Send To** location is **SNS Topic**, and you can see a **SNS** box for the SNS topic name\.  
![\[Console screenshot showing SNS topic as the chosen destination.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/s3-bucket-properties-events-sns.png)![\[Console screenshot showing SNS topic as the chosen destination.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)![\[Console screenshot showing SNS topic as the chosen destination.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)

1. In the box that appears, choose or enter the destination SNS, SQS, or Lambda function\. 

   You can choose or enter the SNS, SQS, or Lambda function name, or you can choose to the destination Amazon Resource Name \(ARN\)\. The example screenshot below shows the **Add SNS topic ARN** option\.  
![\[Console screenshot showing Add SNS topic ARN option.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/s3-bucket-properties-events-sns-arn.png)![\[Console screenshot showing Add SNS topic ARN option.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)![\[Console screenshot showing Add SNS topic ARN option.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)

1. If you chose **Add ARN**, enter the SNS topic, SQS queue, or Lambda function ARN\.  
![\[Console screenshot showing Add SNS topic ARN box for entering the destination ARN.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/s3-bucket-properties-events-sns-arn-box.png)![\[Console screenshot showing Add SNS topic ARN box for entering the destination ARN.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)![\[Console screenshot showing Add SNS topic ARN box for entering the destination ARN.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)

1. Choose **Save**\. 

   Amazon S3 sends a test message to the event notification destination\.

## More info<a name="enable-event-notifications-moreinfo"></a>
+ [How do I restore an S3 object that has been archived?](restore-archived-objects.md)