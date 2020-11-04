# How do I create a request metrics filter for all the objects in my S3 bucket?<a name="configure-metrics"></a>

There are three types of Amazon CloudWatch metrics for Amazon S3: storage metrics, request metrics, and replication metrics\. Storage metrics are reported once per day and are provided to all customers at no additional cost\. Request metrics are available at one\-minute intervals after some latency to process\. Request metrics are billed at the standard CloudWatch rate\. You must opt into request metrics by configuring them in the console or using the Amazon S3 API\.

For more information about CloudWatch metrics for Amazon S3, see [Monitoring metrics with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudwatch-monitoring.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To create a request metrics filter**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects you want request metrics for\.

1. Choose the **Metrics** tab\.

1. Under **Bucket metrics**, choose **View additional charts**\.

1. Choose the **Request metrics** tab\.

1. Choose **Create filter**\.

1. In the **Filter name** box, enter your filter name\. 

   Names can only contain letters, numbers, periods, dashes, and underscores\. We recommend using the name `EntireBucket` for a filter that applies to all objects\.

1. Under **Choose a filter scope**, choose **This filter applies to all objects in the bucket**\.

   You can also define a filter so that the metrics are only collected and reported on a subset of objects in the bucket\. For more information, see [How do I create a request metrics filter that limits scope by object tag or prefix?](configure-metrics-filter.md)

1. Choose **Create filter**\.

1. On the **Request metrics** tab, under **Filters**, choose the filter that you just created\.

   After about 15 minutes, CloudWatch begins tracking these request metrics\. You can see them on the **Request metrics** tab\. You can see graphs for the metrics on the Amazon S3 or CloudWatch console\. Request metrics are billed at the standard CloudWatch rate\. For more information, see [Amazon CloudWatch pricing](http://aws.amazon.com/cloudwatch/pricing/)\. 