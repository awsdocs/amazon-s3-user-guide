# How Do I Enable Server Access Logging for an S3 Bucket?<a name="server-access-logging"></a>

Server access logging provides detailed records for the requests made to a bucket\. Server access logs are useful for many applications because they give bucket owners insight into the nature of requests made by clients not under their control\. By default, Amazon Simple Storage Service \(Amazon S3\) doesn't collect server access logs\. This topic describes how to enable logging for a bucket\. For more information, see [Server Access Logging](http://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) in the *Amazon Simple Storage Service Developer Guide*\.

When you enable logging, Amazon S3 delivers access logs to a target bucket that you choose\. An access log record contains details about the requests made to a bucket\. This can include the request type, the resources specified in the request, and the time and date the request was processed\. For more information, see [Server Access Log Format](http://docs.aws.amazon.com/AmazonS3/latest/dev/LogFormat.html) in the *Amazon Simple Storage Service Developer Guide*\.

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

1. Choose **Enable Logging**\. For **Target**, choose the name of the bucket that you want to receive the log record objects\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/enable-bucket-logging.png)

1. \(Optional\) For **Target prefix**, type a key name prefix for log objects, so that all of the log objects begin with the same string\.

1. Choose **Save**\.

**More Info**  
 [How Do I View the Properties for an S3 Bucket?](view-bucket-properties.md)