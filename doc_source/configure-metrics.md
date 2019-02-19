# How Do I Configure Request Metrics for an S3 Bucket?<a name="configure-metrics"></a>

There are two types of Amazon CloudWatch \(CloudWatch\) metrics for Amazon S3: storage metrics and request metrics\. Storage metrics are reported once per day and are provided to all customers at no additional cost\. Request metrics are available at 1\-minute intervals after some latency to process, and metrics are billed at the standard CloudWatch rate\. To get request metrics, you must opt into them by configuring them in the console or with the Amazon S3 API\.

For more conceptual information about CloudWatch metrics for Amazon S3, see [Monitoring Metrics with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudwatch-monitoring.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To configure request metrics on a bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that has the objects you want to get request metrics for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose the **Management** tab, and then choose **Metrics**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-metrics.png)

1. Choose **Requests**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-requests.png)

1. From the name of your bucket in the left\-side pane, choose the edit icon\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-metrics-edit.png)

1. Choose the **Request metrics** check box\. This also enables Data Transfer metrics\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-metrics-checkbox.png)

1. Choose **Save**\.

You have now created a metrics configuration for all the objects in an Amazon S3 bucket\. About 15 minutes after CloudWatch begins tracking these request metrics, you can see graphs for the metrics in both the Amazon S3 or CloudWatch consoles\. You can also define a filter so the metrics are only collected and reported on a subset of objects in the bucket\. For more information, see [How Do I Configure a Request Metrics Filter?](configure-metrics-filter.md)\.