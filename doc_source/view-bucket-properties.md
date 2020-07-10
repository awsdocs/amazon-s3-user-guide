# How do I view the properties for an S3 Bucket?<a name="view-bucket-properties"></a>

This topic explains how to view the properties for an S3 bucket\.

**To view the properties for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to view the properties for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. On the **Properties** page, you can configure the following properties for the bucket\.

   1. **Versioning** – Versioning enables you to keep multiple versions of an object in one bucket\. By default, versioning is disabled for a new bucket\. For information about enabling versioning, see [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)\.

   1. **Server access logging** – Server access logging provides detailed records for the requests that are made to your bucket\. By default, Amazon S3 does not collect server access logs\. For information about enabling server access logging, see [How do I enable server access logging for an S3 bucket?](server-access-logging.md)\.

   1. **Static website hosting** – You can host a static website on Amazon S3\. To enable static website hosting, choose **Static website hosting** and then specify the settings you want to use\. For more information, see [How do I configure an S3 bucket for static website hosting?](static-website-hosting.md)\.

   1. **Object\-level logging** – Object\-level logging records object\-level API activity by using CloudTrail data events\. For information about enabling object\-level logging, see [How do I enable object\-level logging for an S3 bucket with AWS CloudTrail data events?](enable-cloudtrail-events.md)\.

   1. **Tags** – With AWS cost allocation, you can use bucket tags to annotate billing for your use of a bucket\. A tag is a key\-value pair that represents a label that you assign to a bucket\. To add tags, choose **Tags**, and then choose **Add tag**\. For more information, see [Using Cost Allocation Tags for S3 Buckets](https://docs.aws.amazon.com/AmazonS3/latest/dev/CostAllocTagging.html) in the *Amazon Simple Storage Service Developer Guide*\. 

   1. **Transfer acceleration** – Amazon S3 Transfer Acceleration enables fast, easy, and secure transfers of files over long distances between your client and an S3 bucket\. For information about enabling transfer acceleration, see [How do I enable transfer acceleration for an S3 bucket?](enable-transfer-acceleration.md)\.

   1. **Events** – You can enable certain Amazon S3 bucket events to send a notification message to a destination whenever the events occur\. To enable events, choose **Events** and then specify the settings you want to use\. For more information, see [How do I enable and configure event notifications for an S3 Bucket?](enable-event-notifications.md)\. 

   1. **Requester Pays** – You can enable Requester Pays so that the requester \(instead of the bucket owner\) pays for requests and data transfers\. For more information, see [Requester Pays Buckets](https://docs.aws.amazon.com/AmazonS3/latest/dev/RequesterPaysBuckets.html) in the *Amazon Simple Storage Service Developer Guide*\. 