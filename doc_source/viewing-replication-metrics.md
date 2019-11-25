# Viewing Replication Metrics<a name="viewing-replication-metrics"></a>

There are three types of Amazon CloudWatch metrics for Amazon S3: storage metrics, request metrics and replication\. Replication metrics are available 15 minutes after a replication rule with S3 Replication Time Control \(S3 RTC\) has been enabled\. Replication metrics are billed at the standard Amazon CloudWatch rate\. Replication metrics are enabled automatically when you enable replication with S3 RTC on your with the console or with the Amazon S3 API\.

Replication metrics track the rule IDs of the replication configuration\. A replication rule ID may be specific to a prefix or tags or a combination of both\. For more information on S3 Replication Time Control \(S3 RTC\), see  in the *Amazon Simple Storage Service Developer Guide*\.

For more information about CloudWatch metrics for Amazon S3, see [Monitoring Metrics with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudwatch-monitoring.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To view replication metrics**

1. Sign in to the AWS Management Console 

1. In the **Bucket name** list, choose the name of the bucket that has the objects you want to get request metrics for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose the **Management** tab\. and then choose **Metrics**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-metrics.png)

1. Choose **Replication**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-replication-metrics.png)

1. From **Rule IDs** drop down in the left\-side pane, select the *rule ID\(s\)* you want\. If you have several rule IDs to choose from, you can also search for the one\(s\) you want\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/select-replication-rule-id.png)

1. Once you have selected the *rule IDs* you want, clik the **Display graphs** button below the Rule IDs selection box \.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-display-graphs.png)

You will then be able to view the replication metrics **Replication Latency\(in seconds\)**, **Operations pending replication** and, **Bytes pending replication** for the rules that you selected\. Amazon CloudWatch begins showing reporting replication metrics 15 minutes after S3 Replication Time Control \(S3 RTC\) on the respective replication rule\. You can view replication metrics on Amazon S3 or CloudWatch consoles\. For information, see  in the Amazon Simple Storage Service Developer Guide 