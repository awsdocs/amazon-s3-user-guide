# How do I view replication metrics?<a name="viewing-replication-metrics"></a>

There are three types of Amazon CloudWatch metrics for Amazon S3: storage metrics, request metrics, and replication metrics\. *Replication* metrics are turned on automatically when you enable replication with S3 Replication Time Control \(S3 RTC\) using the AWS Management Console or the Amazon S3 API\. Replication metrics are available 15 minutes after you enable a replication rule with S3 Replication Time Control \(S3 RTC\) \(S3 RTC\)\.

Replication metrics track the rule IDs of the replication configuration\. A replication rule ID can be specific to a prefix, a tag, or a combination of both\. For more information about S3 Replication Time Control \(S3 RTC\), see [Replicating Objects Using S3 Replication Time Control \(S3 RTC\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-time-control.html) in the *Amazon Simple Storage Service Developer Guide*\.

For more information about CloudWatch metrics for Amazon S3, see [Monitoring Metrics with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudwatch-monitoring.html) in the *Amazon Simple Storage Service Developer Guide*\.

## Viewing replication metrics \(legacy Amazon S3 console experience\)<a name="replication-metrics"></a>

**Prerequisites**  
Enable a replication rule that has S3 RTC\.

**To view replication metrics**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the objects you want replication metrics for\.

1. Choose the **Management** tab, and then choose **Metrics**\.

1. Choose **Replication**\.

1. In the **Rule IDs** list in the left pane, select the rule IDs that you want\. If you have several rule IDs to choose from, you can search for the IDs that you want\.

1. After choosing the rule IDs that you want, choose **Display graphs** below the **Rule IDs** selection box\.

You can then view the replication metrics **Replication Latency \(in seconds\)**, **Operations pending replication**, and **Bytes pending replication** for the rules that you selected\. Amazon CloudWatch begins reporting replication metrics 15 minutes after you enable S3 RTC on the respective replication rule\. You can view replication metrics on the Amazon S3 or CloudWatch console\. For information, see [Replication metrics overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-time-control.html#using-replication-metrics) in the *Amazon Simple Storage Service Developer Guide*\.

## Viewing replication metrics \(new Amazon S3 console experience\)<a name="replication-metrics-new"></a>

**Note**  
We are in the process of releasing a new Amazon S3 console experience to customers\. These instructions describe the new experience\. If you don't see the new console now, don't worry\. It will soon be available to all customers\. For instructions using the previous console experience, expand **Viewing replication metrics \(legacy Amazon S3 console experience\)** on this page\.

**Prerequisites**  
Enable a replication rule that has S3 RTC\.

**To view replication metrics**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects you want replication metrics for\.

1. Choose the **Metrics** tab\.

1. Under **Replication metrics**, choose **Replication rules**\.

1. Choose **Display charts**\.

   Amazon S3 displays **Replication Latency \(in seconds\)**, **Operations pending replication** in charts\.

1. To view all replication metrics, including **Bytes pending replication**, **Replication Latency \(in seconds\)**, and **Operations pending replication** together on a separate page, choose **View 1 more chart**\.

You can then view the replication metrics **Replication Latency \(in seconds\)**, **Operations pending replication**, and **Bytes pending replication** for the rules that you selected\. Amazon CloudWatch begins reporting replication metrics 15 minutes after you enable S3 RTC on the respective replication rule\. You can view replication metrics on the Amazon S3 or CloudWatch console\. For information, see [Replication metrics overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-time-control.html#using-replication-metrics) in the *Amazon Simple Storage Service Developer Guide*\.