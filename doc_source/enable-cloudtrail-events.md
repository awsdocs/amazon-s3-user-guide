# How do I enable object\-level logging for an S3 bucket with AWS CloudTrail data events?<a name="enable-cloudtrail-events"></a>

This section describes how to enable an AWS CloudTrail trail to log data events for objects in an S3 bucket by using the Amazon S3 console\. CloudTrail supports logging Amazon S3 object\-level API operations such as `GetObject`, `DeleteObject`, and `PutObject`\. These events are called data events\. By default, CloudTrail trails don't log data events, but you can configure trails to log data events for S3 buckets that you specify, or to log data events for all the Amazon S3 buckets in your AWS account\. For more information, see [ Logging Amazon S3 API Calls Using AWS CloudTrail](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudtrail-logging)\. CloudTrail does not populate data events in the CloudTrail event history\. Additionally, not all bucket\-level actions are populated in the CloudTrail event history\. For more information, see [Using Amazon CloudWatch Logs filter patterns and Amazon Athena to query CloudTrail logs\. ](https://aws.amazon.com/premiumsupport/knowledge-center/find-cloudtrail-object-level-events/)

To configure a trail to log data events for an S3 bucket, you can use either the AWS CloudTrail console or the Amazon S3 console\. If you are configuring a trail to log data events for all the Amazon S3 buckets in your AWS account, it's easier to use the CloudTrail console\. For information about using the CloudTrail console to configure a trail to log S3 data events, see [ Data Events](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-management-and-data-events-with-cloudtrail.html#logging-data-events) in the *AWS CloudTrail User Guide*\. 

**Important**  
Additional charges apply for data events\. For more information, see [AWS CloudTrail Pricing](https://aws.amazon.com/cloudtrail/pricing/)\. 

The following procedure shows how to use the Amazon S3 console to enable a CloudTrail trail to log data events for an S3 bucket\.

**To enable CloudTrail data events logging for objects in an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket\.

1. Choose **Properties**\.

1. Under **AWS CloudTrail data events**, choose **Configure in CloudTrail**\. For information about how to create trails in the CloudTrail console, see [ Creating a Trail with the Console](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail-by-using-the-console.html) in the *AWS CloudTrail User Guide*\. 

1. To disable object\-level logging for the bucket, you must go to the CloudTrail console and remove the bucket name from the trail's **Data events**\.
**Note**  
If you use the CloudTrail console or the Amazon S3 console to configure a trail to log data events for an S3 bucket, the Amazon S3 console shows that object\-level logging is enabled for the bucket\. 

For information about enabling object\-level logging when you create an S3 bucket, see [How do I create an S3 Bucket?](create-bucket.md)\.

## More info<a name="enable-cloudtrail-events-moreinfo"></a>
+ [How do I view the properties for an S3 bucket?](view-bucket-properties.md)
+ [ Logging Amazon S3 API Calls By Using AWS CloudTrail](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudtrail-logging.html) in the *Amazon Simple Storage Service Developer Guide* 
+ [ Working with CloudTrail Log Files](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-working-with-log-files.html) in the *AWS CloudTrail User Guide*