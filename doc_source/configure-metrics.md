# How do I configure request metrics for an S3 Bucket?<a name="configure-metrics"></a>

There are three types of Amazon CloudWatch metrics for Amazon S3:
+ *Storage metrics* are reported once per day and are provided to all customers at no additional cost\.
+ *Replication metrics* are available 15 minutes after enabling a replication rule with S3 Replication Time Control \(S3 RTC\)\. For more information, see [How do I view replication metrics?](viewing-replication-metrics.md)
+ *Request metrics* are available at 1\-minute intervals after some latency to process, and the metrics are billed at the standard CloudWatch rate\. 

For more information about CloudWatch metrics for Amazon S3, see [Monitoring Metrics with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudwatch-monitoring.html) in the *Amazon Simple Storage Service Developer Guide*\.

To get request metrics, you must opt into them by configuring them on the AWS Management Console or using the Amazon S3 API\.

**To configure request metrics on a bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the objects you want request metrics for\.  
![\[Console screenshot showing bucket name.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose the **Management** tab, and then choose **Metrics**\.  
![\[Console screenshot showing metrics button.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-metrics.png)

1. Choose **Requests**\.  
![\[Console screenshot showing requests tab.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-requests.png)

1. In the left pane, choose the edit icon next to the name of the bucket\.  
![\[Console screenshot showing bucket name with edit icon.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-metrics-edit.png)

1. Select the **Request metrics** check box\. This also enables data transfer metrics\.  
![\[Console screenshot showing bucket name with request metrics and data transfer metrics boxes checked.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-metrics-checkbox.png)

1. Choose **Save**\.

You have now created a metrics configuration for all the objects in an Amazon S3 bucket\. About 15 minutes after CloudWatch begins tracking these request metrics, you can see graphs for the metrics on the Amazon S3 or CloudWatch console\. 

You can also define a filter so that the metrics are only collected and reported on a subset of objects in the bucket\. For more information, see [How do I configure a request metrics filter?](configure-metrics-filter.md)