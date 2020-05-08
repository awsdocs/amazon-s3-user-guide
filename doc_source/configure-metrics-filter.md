# How do I configure a request metrics filter?<a name="configure-metrics-filter"></a>

There are three types of Amazon CloudWatch metrics for Amazon S3: storage metrics, request metrics and replication\. Storage metrics are reported once per day and are provided to all customers at no additional cost\. Request metrics are available at 1 minute intervals after some latency to process, and metrics are billed at the standard CloudWatch rate\. To get request metrics, you must opt into them by configuring them in the console or with the Amazon S3 API\.

For more conceptual information about CloudWatch metrics for Amazon S3, see [Monitoring Metrics with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudwatch-monitoring.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To filter request metrics on a subset of objects in a bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that has the objects you want to get request metrics for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose the **Management** tab\. and then choose **Metrics**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-metrics.png)

1. Choose **Requests**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-requests.png)

1. From **Filters** in the left\-side pane, choose **Add**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-filter-add.png)

1. Provide a name for this metrics configuration\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-filter-name.png)

1. Provide one or more prefixes or tags, separated by commas, in **Prefix /tags that you want to monitor**\. From the drop down, select whether the value you provided is a tag or a prefix\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-filter-prefixtag.png)

1. Choose **Save**\.

You have now created a metrics configuration for request metrics on a subset of the objects in an Amazon S3 bucket\. About 15 minutes after CloudWatch begins tracking these request metrics, you can see graphs for the metrics in both the Amazon S3 or CloudWatch consoles\. You can also request metrics at the bucket level\. For information, see [How do I configure request metrics for an S3 Bucket?](configure-metrics.md)