# How do I view the properties for an S3 bucket?<a name="view-bucket-properties"></a>

You can view and configure the properties for an Amazon S3 bucket, including settings for versioning, tags, default encryption, logging, notifications, and more\.

**To view the properties for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want to view the properties for\.

1. Choose **Properties**\.

1. On the **Properties** page, you can configure the following properties for the bucket\.
   + **Bucket Versioning** – Keep multiple versions of an object in one bucket by using versioning\. By default, versioning is disabled for a new bucket\. For information about enabling versioning, see [How do I enable or suspend versioning for an S3 bucket?](https://docs.aws.amazon.com/AmazonS3/latest/dev/enable-versioning.html)
   + **Tags** – With AWS cost allocation, you can use bucket tags to annotate billing for your use of a bucket\. A tag is a key\-value pair that represents a label that you assign to a bucket\. To add tags, choose **Tags**, and then choose **Add tag**\. For more information, see [Using cost allocation S3 bucket tags](https://docs.aws.amazon.com/AmazonS3/latest/dev/CostAllocTagging.html)\. 
   + **Default encryption** – Enabling default encryption provides you with automatic server\-side encryption\. Amazon S3 encrypts an object before saving it to a disk and decrypts the object when you download it\. For more information, see [Amazon S3 default encryption for S3 buckets](https://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html)\. 
   + **Server access logging** – Get detailed records for the requests that are made to your bucket with server access logging\. By default, Amazon S3 doesn't collect server access logs\. For information about enabling server access logging, see [How do I enable server access logging for an S3 bucket?](server-access-logging.md)
   + **AWS CloudTrail data events** – Use CloudTrail to log data events\. By default, trails don't log data events\. Additional charges apply for data events\. For more information, see [Logging Data Events for Trails](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-data-events-with-cloudtrail.html) in the *AWS CloudTrail User Guide*\.
   + **Event notifications** – Enable certain Amazon S3 bucket events to send notification messages to a destination whenever the events occur\. To enable events, choose **Create event notification**, and then specify the settings you want to use\. For more information, see [Enabling and configuring event notifications for an S3 Bucket](enable-event-notifications.md)
   + **Transfer acceleration** – Enable fast, easy, and secure transfers of files over long distances between your client and an S3 bucket\. For information about enabling transfer acceleration, see [How do I enable transfer acceleration for an S3 bucket?](enable-transfer-acceleration.md)
   + **Object Lock** – Use S3 Object Lock to prevent an object from being deleted or overwritten for a fixed amount of time or indefinitely\. For more information, see [Locking objects using S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html)\.
   + **Requester Pays** – Enable Requester Pays if you want the requester \(instead of the bucket owner\) to pay for requests and data transfers\. For more information, see [Requester Pays buckets](https://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html)\. 
   + **Static website hosting** – You can host a static website on Amazon S3\. To enable static website hosting, choose **Static website hosting**, and then specify the settings you want to use\. For more information, see [How do I configure an S3 bucket for static website hosting?](static-website-hosting.md)