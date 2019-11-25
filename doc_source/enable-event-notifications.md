# How Do I Enable and Configure Event Notifications for an S3 Bucket?<a name="enable-event-notifications"></a>

You can enable certain Amazon S3 bucket events to send a notification message to a destination whenever the events occur\. This section explains how to use the Amazon S3 console to enable event notifications\. For information about using event notifications with the AWS SDKs, and the Amazon S3 REST APIs, see [Configuring Notifications for Amazon S3 Events](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html) in the *Amazon Simple Storage Service Developer Guide*\. 

**Topics**
+ [Amazon S3 Event Notification Types and Destinations](#enable-event-notifications-types)
+ [Enabling and Configuring Event Notifications](#enable-event-notifications-how-to)
+ [More Info](#enable-event-notifications-moreinfo)

## Amazon S3 Event Notification Types and Destinations<a name="enable-event-notifications-types"></a>

When configuring event notifications for a bucket you must specify the type of events you want to be notified of and the destination where you want the notifications sent\.

Amazon S3 can send notifications for the following types of events:
+ **An object created event** – You choose **ObjectCreated \(All\)** when configuring your events in the console to enable notifications for anytime an object is created in your bucket\. Or, you can select one or more of the specific object\-creation actions to trigger event notifications\. These actions are **Put**, **Post**, **Copy**, and **CompleteMultiPartUpload**\.

   
+ **An object delete event** – You select **ObjectDelete \(All\)** when configuring your events in the console to enable notification for anytime an object is deleted\. Or, you can select **Delete** to trigger event notifications when an unversioned object is deleted or a versioned object is permanently deleted\. You select **Delete Marker Created** to trigger event notifications when a delete marker is created for a versioned object\. 

   
+ **Restore object events** – When configuring events in the console to enable notifications for the restoration of objects stored in the GLACIER storage class\. Select **Restore from Glacier initiated** to be notified of when the restore is initiated\. Select **Restore from Glacier completed** to be notified when restoration of an object is complete\. 

   
+ **A Reduced Redundancy Storage \(RRS\) object lost event** – You select **RRSObjectLost** to be notified when Amazon S3 detects that an object of the RRS storage class has been lost\.

   
+ **Replication events ** – You can choose to receive replication event notifications if you have replication with S3 Replication Time Control \(S3 RTC\) enabled\. For more information, see all the replication events and their descriptions in the [ Supported Event Types](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html#notification-how-to-event-types-and-destinations) section in the *Amazon Simple Storage Service Developer Guide*\.

   

Event notification messages can be sent to the following types of destinations:
+ **An Amazon Simple Notification Service \(Amazon SNS\) topic** – A web service that coordinates and manages the delivery or sending of messages to subscribing endpoints or clients\.

   
+ **An Amazon Simple Queue Service \(Amazon SQS\) queue** – Offers reliable and scalable hosted queues for storing messages as they travel between computer\.

   
+ **A Lambda function** – AWS Lambda is a compute service where you can upload your code and the service can run the code on your behalf using the AWS infrastructure\. You package up and upload your custom code to AWS Lambda when you create a Lambda function

   

## Enabling and Configuring Event Notifications<a name="enable-event-notifications-how-to"></a>

Before you can enable event notifications for your bucket you must set up one of these destination types\. For more information, see [How Do I Set Up a Destination to Receive Event Notifications?](setup-event-notification-destination.md)\.

**To enable and configure event notifications for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to enable events for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Under Advanced settings, choose **Events**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-box.png)

1. Choose **Add notification**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-add-notification.png)

1. In **Name**, type a descriptive name for your event configuration\. If you do not enter a name, a GUID is autogenerated and used for the name\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-enter-name.png)

1. Under **Events**, select one or more of the type of event occurrences that you want to receive notifications for\. When the event occurs a notification is sent to a destination that you choose in **Step 9**\. For a description of the event types, see [Amazon S3 Event Notification Types and Destinations](#enable-event-notifications-types)\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-add-event-types.png)

    For information about deleting versioned objects, see [Deleting Object Versions](https://docs.aws.amazon.com/AmazonS3/latest/dev/DeletingObjectVersions.html)\. For information about object versioning, see [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html)\.
**Note**  
When you delete the last object from a folder Amazon S3 can generate an object creation event\. The Amazon S3 console displays a folder under the following circumstances: 1\) when a zero byte object has a trailing slash \(/\) in its name \(in this case there is an actual Amazon S3 object of 0 bytes that represents a folder\), and 2\) if the object has a slash \(/\) within its name \(in this case there isn't an actual object representing the folder\)\. When there are multiple objects with the same prefix with a trailing slash \(/\) as part of their names, those objects are shown as being part of a folder\. The name of the folder is formed from the characters preceding the trailing slash \(/\)\. When you delete all the objects listed under that folder, there is no actual object available to represent the empty folder\. Under such circumstance the Amazon S3 console creates a zero byte object to represent that folder\. If you enabled event notification for creation of objects, the zero byte object creation action that is taken by the console will trigger an object creation event\. 

1. Type an object name **Prefix** and/or a **Suffix** to filter the event notifications by the prefix and/or suffix\. For example, you can set up a filter so that you are sent a notification only when files are added to an image folder \(for example, objects with the name prefix `images/`\)\. For more information, see [Configuring Notifications with Object Key Name Filtering](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html#notification-how-to-filtering)\.   
![\[Enter prefix for filtering events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/events-add-event-prefix.png)![\[Enter prefix for filtering events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)![\[Enter prefix for filtering events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)

1. Select the type of destination to have the event notifications sent to\. For a description of the destinations, see [Amazon S3 Event Notification Types and Destinations](#enable-event-notifications-types)\.  
![\[Events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/s3-bucket-properties-events-destination.png)![\[Events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)![\[Events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)

   1. If you select the **SNS Topic** destination type\. 

      1. In the **SNS topic** box, type the name or select from the menu, the Amazon SNS topic that will receive notifications from Amazon S3\. For information about the Amazon SNS topic format, see [SNS FAQ](https://aws.amazon.com/sns/faqs/#10)\.  
![\[Events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/s3-bucket-properties-events-sns.png)![\[Events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)![\[Events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)

      1. \(Optional\) You can also select **Add SNS topic ARN** from the menu and type the **ARN** of the SNS topic in **SNS topic ARN**\.  
![\[Events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/s3-bucket-properties-events-sns-arn.png)![\[Events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)![\[Events\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/)

   1. If you select the **SQS queue** destination type, do the following:

      1.  In **SQS queue**, type or choose a name from the menu of the Amazon SQS queue that you want to receive notifications from Amazon S3\. For information about Amazon SQS, see [What is Amazon Simple Queue Service?](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/Welcome.html) in the *Amazon Simple Queue Service Developer Guide*\.

      1. \(Optional\) You can also select **Add SQS topic ARN** from the menu and type the ARN of the SQS queue in **SQS queue ARN**\.

   1. If you select the **Lambda Function** destination type, do the following:

      1.  In **Lambda Function**, type or choose the name of the Lambda function that you want to receive notifications from Amazon S3\.

      1. If you don't have any Lambda functions in the region that contains your bucket, you'll be prompted to enter a Lambda function ARN\. In **Lambda Function ARN**, type the ARN of the Lambda function that you want to receive notifications from Amazon S3\.

      1. \(Optional\) You can also choose **Add Lambda function ARN** from the menu and type the ARN of the Lambda function in **Lambda function ARN**\.

      For information about using Lambda with Amazon S3, see [Using AWS Lambda: with Amazon S3](https://docs.aws.amazon.com/lambda/latest/dg/with-s3.html) in the *AWS Lambda Developer Guide*\.

1. Choose **Save**\. Amazon S3 will send a test message to the event notification destination\.

## More Info<a name="enable-event-notifications-moreinfo"></a>
+ [How Do I Restore an S3 Object That Has Been Archived?](restore-archived-objects.md)