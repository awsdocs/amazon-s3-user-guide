# Enabling and configuring event notifications for an S3 Bucket<a name="enable-event-notifications"></a>

You can enable certain Amazon S3 events to send a notification message to a destination whenever the events occur\. This section explains how to use the Amazon S3 console to enable event notifications\. For information about using event notifications with the AWS SDKs and the Amazon S3 REST APIs, see [Configuring Amazon S3 Event Notifications](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html) in the *Amazon Simple Storage Service Developer Guide*\. 

**Topics**
+ [Event notification types](#enable-event-notifications-types)
+ [Enabling and configuring event notifications](#enable-event-notifications-how-to)

## Event notification types<a name="enable-event-notifications-types"></a>

When you configure event notifications for a bucket, you must specify the type of events for which you want to receive notifications\. For a complete list of event types, see [Supported Event Types](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html#supported-notification-event-types) section in the *Amazon Simple Storage Service Developer Guide*\. 

In the Amazon S3 console, you have the following options for configuring event notifications\. You can choose a single option or multiple options\.
+ **Object creation**
  + **All object create events** – Receive a notification when an object is created in your bucket by any of the following object creation actions: **Put**, **Post**, **Copy**, and **Multipart upload completed**\.
  +  **Put**, **Post**, **Copy**, and **Multipart upload completed** – Receive a notification for one of these specific object creation actions\.
+ **Object deletion**
  + **All object delete events** – Receive a notification any time an object in your bucket is deleted\.
  + **Delete marker created** – Receive a notification when a delete marker is created for a versioned object\.

     For information about deleting versioned objects, see [Deleting Object Versions](https://docs.aws.amazon.com/AmazonS3/latest/dev/DeletingObjectVersions.html)\. For information about object versioning, see [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html)\.
+ **Object restoration from S3 Glacier or S3 Glacier Deep Archive storage class** 
  + **Restore initiated** – Receive a notification for *Initiation* of object restoration\.
  + **Restore completed** – Receive a notification for *Completion* of object restoration\.
+ **Reduced Redundancy Storage \(RRS\) object lost events**
  + **Object in RSS Lost** – Receive a notification that an object of the RRS storage class has been lost
+ **Objects eligible for replication using Amazon S3 Replication Time Control**
  + **Replication time missed threshold** – Receive a notification that an object exceeded the 15\-minute threshold for replication\.
  + **Replication time completed after threshold** – Receive a notification that an object replicated after the 15\-minute threshold\.
  + **Replication time not tracked** – Receive a notification that an object that was eligible for replication is no longer being tracked by replication metrics\.
  + **Replication time failed** – Receive a notification that an object failed to replicate\.

**Note**  
When you delete the last object from a folder, Amazon S3 can generate an object creation event\. When there are multiple objects with the same prefix with a trailing slash \(/\) as part of their names, those objects are shown as being part of a folder in the Amazon S3 console\. The name of the folder is formed from the characters preceding the trailing slash \(/\)\.   
When you delete all the objects listed under that folder, no actual object is available to represent the empty folder\. Under such circumstances, the Amazon S3 console creates a zero\-byte object to represent that folder\. If you enabled event notification for the creation of objects, the zero\-byte object creation action that is taken by the console triggers an object creation event\.  
The Amazon S3 console displays a folder under the following circumstances:  
When a zero\-byte object has a trailing slash \(/\) in its name\. In this case, there is an actual Amazon S3 object of 0 bytes that represents a folder\.
If the object has a slash \(/\) within its name\. In this case, there isn't an actual object representing the folder\.

## Enabling and configuring event notifications<a name="enable-event-notifications-how-to"></a>

Before you can enable event notifications for your bucket, you must set up one of the destination types\. For more information, see [Setting a destination to receive Amazon S3 event notifications](setup-event-notification-destination.md)

**To enable and configure event notifications for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want to enable events for\.

1. Navigate to the **Event Notifications** section and choose **Create event notification**\.

1. In the **General configuration** section, specify descriptive event name for your event notification\. Optionally, you can also specify a prefix and a suffix to limit the notifications to objects with keys ending in the specified characters\.

   1. Enter a description for the **Event name**\.

      If you don't enter a name, a Globally Unique Identifier \(GUID\) will be generated and used for the name\. 

   1. To optionally filter event notifications by prefix, enter a **Prefix**\. 

      For example, you can set up a prefix filter so that you receive notifications only when files are added to a specific folder \(for example, `images/`\)\. 

   1. To optionally filter event notifications by suffix, enter a **Suffix**\. 

      For more information, see [Configuring Notifications with Object Key Name Filtering](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html#notification-how-to-filtering)\. 

1. In the **Event types** section, select one or more event types for which you want to receive notifications\. 

   For a listing of the event types, see [Event notification types](#enable-event-notifications-types)\.

1. In the **Destination** section, choose the event notification destination\. 
**Note**  
Before you can publish event notifications, you must grant the Amazon S3 principal the necessary permissions to call the relevant API to publish notifications to a Lambda function, SNS topic, or SQS queue\.

   1. Select the destination type: **Lambda Function**, **SNS Topic**, or **SQS Queue**\.

   1. After you choose your destination type, choose a function, topic, or queue from the dropdown list\.

   1. Alternatively, if you would prefer to specify an Amazon Resource Name \(ARN\), select **Enter ARN** and enter the ARN\.

   For more information, see [Setting a destination to receive Amazon S3 event notifications](setup-event-notification-destination.md)\.

1. Choose **Save changes** and Amazon S3 sends a test message to the event notification destination\.

For more information, see [Configuring Amazon S3 event notifications](https://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html) in the *Amazon Simple Storage Service Developer Guide\.*