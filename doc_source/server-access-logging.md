# How do I enable server access logging for an S3 bucket?<a name="server-access-logging"></a>

This topic describes how to enable server access logging for an Amazon S3 bucket using the AWS Management Console\. For information about how to enable logging programmatically and details about how logs are delivered, see [Server Access Logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) in the *Amazon Simple Storage Service Developer Guide*\.

By default, Amazon Simple Storage Service \(Amazon S3\) doesn't collect server access logs\. When you enable logging, Amazon S3 delivers access logs for a source bucket to a target bucket that you choose\. The target bucket must be in the same AWS Region as the source bucket and must not have a default retention period configuration\. 

Server access logging provides detailed records for the requests that are made to an S3 bucket\. Server access logs are useful for many applications\. For example, access log information can be useful in security and access audits\. It can also help you learn about your customer base and understand your Amazon S3 bill\. 

An access log record contains details about the requests that are made to a bucket\. This information can include the request type, the resources that are specified in the request, and the time and date that the request was processed\. For more information, see [Server Access Log Format](https://docs.aws.amazon.com/AmazonS3/latest/dev/LogFormat.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Important**  
There is no extra charge for enabling server access logging on an Amazon S3 bucket\. However, any log files that the system delivers to you will accrue the usual charges for storage\. \(You can delete the log files at any time\.\) We do not assess data transfer charges for log file delivery, but we do charge the normal data transfer rate for accessing the log files\.

**To enable server access logging for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to enable server access logging for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Choose **Server access logging**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/bucket-logging-box.png)

1. Choose **Enable Logging**\. For **Target**, choose the name of the bucket that you want to receive the log record objects\.  The target bucket must be in the same Region as the source bucket and must not have a default retention period configuration\.  
![\[Create bucket wizard set permissions options page.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/enable-bucket-logging.png)

1. \(Optional\) For **Target prefix**, type a key name prefix for log objects, so that all of the log object names begin with the same string\.

1. Choose **Save**\.

   You can view the logs in the target bucket\. If you specified a prefix, the prefix shows as a folder in the target bucket in the console\. After you enable server access logging, it might take a few hours before the logs are delivered to the target bucket\. For more information about how and when logs are delivered, see [Server Access Logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html#how-logs-delivered) in the *Amazon Simple Storage Service Developer Guide*\.

**More Info**  
 [How do I view the properties for an S3 Bucket?](view-bucket-properties.md)