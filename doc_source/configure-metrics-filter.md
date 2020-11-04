# How do I create a request metrics filter that limits scope by object tag or prefix?<a name="configure-metrics-filter"></a>

There are three types of Amazon CloudWatch metrics for Amazon S3: storage metrics, request metrics, and replication metrics\. Storage metrics are reported once per day and are provided to all customers at no additional cost\. Request metrics are available at one\-minute intervals after some latency to process\. Request metrics are billed at the standard CloudWatch rate\. You must opt into request metrics by configuring them in the console or using the Amazon S3 API\.

For more information about CloudWatch metrics for Amazon S3, see [Monitoring metrics with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudwatch-monitoring.html) in the *Amazon Simple Storage Service Developer Guide*\. 

**To filter request metrics on a subset of objects in a bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects you want request metrics for\.

1. Choose the **Metrics** tab\.

1. Under **Bucket metrics**, choose **View additional charts**\.

1. Choose the **Request metrics** tab\.

1. Choose **Create filter**\.

1. In the **Filter name** box, enter your filter name\. 

   Names can only contain letters, numbers, periods, dashes, and underscores\.

1. Under **Choose a filter scope**, choose **Limit the scope of this filter using prefix and tags**\.

1. \(Optional\) In the **Prefix** box, enter a prefix to limit the scope of the filter to a single path\.

1. \(Optional\) Under **Tags**, enter a tag **Key** and **Value**\.

1. Choose **Create filter**\.

   Amazon S3 creates a filter that uses the tags or prefixes you specified\.

1. On the **Request metrics** tab, under **Filters**, choose the filter that you just created\.

   You have now created a filter that limits the request metrics scope by object tags and prefixes\. About 15 minutes after CloudWatch begins tracking these request metrics, you can see charts for the metrics on both the Amazon S3 and CloudWatch consoles\. Request metrics are billed at the standard CloudWatch rate\. For more information, see [Amazon CloudWatch pricing](http://aws.amazon.com/cloudwatch/pricing/)\. 

   You can also configure request metrics at the bucket level\. For information, see [How do I create a request metrics filter for all the objects in my S3 bucket?](configure-metrics.md)