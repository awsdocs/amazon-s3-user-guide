# How do I enable object\-level logging for an S3 bucket with AWS CloudTrail data events?<a name="enable-cloudtrail-events"></a>

This section describes how to enable an AWS CloudTrail trail to log data events for objects in an S3 bucket by using the Amazon S3 console\. CloudTrail supports logging Amazon S3 object\-level API operations such as `GetObject`, `DeleteObject`, and `PutObject`\. These events are called data events\. By default, CloudTrail trails don't log data events, but you can configure trails to log data events for S3 buckets that you specify, or to log data events for all the Amazon S3 buckets in your AWS account\. For more information, see [ Logging Amazon S3 API Calls Using AWS CloudTrail](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudtrail-logging)\. CloudTrail does not populate data events in the CloudTrail event history\. Additionally, not all bucket\-level actions are populated in the CloudTrail event history\. For more information, see [Using Amazon CloudWatch Logs filter patterns and Amazon Athena to query CloudTrail logs\. ](https://aws.amazon.com/premiumsupport/knowledge-center/find-cloudtrail-object-level-events/)

To configure a trail to log data events for an S3 bucket, you can use either the AWS CloudTrail console or the Amazon S3 console\. If you are configuring a trail to log data events for all the Amazon S3 buckets in your AWS account, it's easier to use the CloudTrail console\. For information about using the CloudTrail console to configure a trail to log S3 data events, see [ Data Events](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-management-and-data-events-with-cloudtrail.html#logging-data-events) in the *AWS CloudTrail User Guide*\. 

**Important**  
Additional charges apply for data events\. For more information, see [AWS CloudTrail Pricing](https://aws.amazon.com/cloudtrail/pricing/)\. 

The following procedure shows how to use the Amazon S3 console to enable a CloudTrail trail to log data events for an S3 bucket\.

**To enable CloudTrail data events logging for objects in an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket\.  
![\[Screenshot showing a bucket in the bucket name list.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[List of tabs in S3 console with the Properties tab selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Choose **Object\-level logging**\.  
![\[Object-level logging screen.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-level-logging-box.png)

1. Choose an existing CloudTrail trail in the drop\-down menu\. 

   The trail you select must be in the same AWS Region as your bucket, so the drop\-down list contains only trails that are in the same Region as the bucket or trails that were created for all Regions\. 

   If you need to create a trail, choose the **CloudTrail console** link to go to the CloudTrail console\. For information about how to create trails in the CloudTrail console, see [ Creating a Trail with the Console](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail-by-using-the-console.html) in the *AWS CloudTrail User Guide*\.   
![\[Choosing a CloudTrail trail in the Object level logging dialog box.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-cloudtrail.png)

1. Under **Events**, choose one of the following:
   + **Read** to specify that you want CloudTrail to log Amazon S3 read APIs such as `GetObject`\. 
   + **Write** to log Amazon S3 write APIs such as `PutObject`\. 
   + **Read** and **Write** to log both read and write object APIs\.

   For a list of supported data events that CloudTrail logs for Amazon S3 objects, see [ Amazon S3 Object\-Level Actions Tracked by CloudTrail Logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudtrail-logging.html#cloudtrail-object-level-tracking) in the *Amazon Simple Storage Service Developer Guide*\.   
![\[Object-level logging dialog box with read and write selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/select-cloudtrail-events.png)

1. Choose **Create** to enable object\-level logging for the bucket\.  
![\[Object-level logging dialog box dialog box displaying Enabled.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/cloudtrail-events-enabled.png)

   To disable object\-level logging for the bucket, you must go to the CloudTrail console and remove the bucket name from the trail's **Data events**\.
**Note**  
If you use the CloudTrail console or the Amazon S3 console to configure a trail to log data events for an S3 bucket, the Amazon S3 console shows that object\-level logging is enabled for the bucket\. 

For information about enabling object\-level logging when you create an S3 bucket, see [How do I create an S3 Bucket?](create-bucket.md)\.

## More info<a name="enable-cloudtrail-events-moreinfo"></a>
+ [How do I view the properties for an S3 Bucket?](view-bucket-properties.md)
+ [ Logging Amazon S3 API Calls By Using AWS CloudTrail](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudtrail-logging.html) in the *Amazon Simple Storage Service Developer Guide* 
+ [ Working with CloudTrail Log Files](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-working-with-log-files.html) in the *AWS CloudTrail User Guide*