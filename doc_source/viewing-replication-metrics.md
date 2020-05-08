# How do I view replication metrics?<a name="viewing-replication-metrics"></a>

There are three types of Amazon CloudWatch metrics for Amazon S3: storage metrics, request metrics, and replication metrics\. *Replication* metrics are available 15 minutes after a replication rule with S3 Replication Time Control \(S3 RTC\) has been enabled\. Replication metrics are billed at the standard Amazon CloudWatch rate\. They are turned on automatically when you enable replication with S3 RTC using the AWS Management Console or the Amazon S3 API\.

Replication metrics track the rule IDs of the replication configuration\. A replication rule ID can be specific to a prefix, a tag, or a combination of both\. For more information about S3 Replication Time Control \(S3 RTC\), see [Replicating Objects Using S3 Replication Time Control \(S3 RTC\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-time-control.html) in the *Amazon Simple Storage Service Developer Guide*\.

For more information about CloudWatch metrics for Amazon S3, see [Monitoring Metrics with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonS3/latest/dev/cloudwatch-monitoring.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To view replication metrics**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the objects you want replication metrics for\.  
![\[Console screenshot showing bucket name.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose the **Management** tab, and then choose **Metrics**\.  
![\[Console screenshot showing metrics tab.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-metrics.png)

1. Choose **Replication**\.  


1. In the **Rule IDs** list in the left pane, select the rule IDs that you want\. If you have several rule IDs to choose from, you can search for the IDs that you want\.  
![\[Console screenshot showing rule IDs search box.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/select-replication-rule-id.png)

1. After choosing the rule IDs that you want, choose **Display graphs** below the **Rule IDs** selection box\.  
![\[Console screenshot showing the display graphs button.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-display-graphs.png)

You can then view the replication metrics **Replication Latency \(in seconds\)**, **Operations pending replication**, and **Bytes pending replication** for the rules that you selected\. Amazon CloudWatch begins reporting replication metrics 15 minutes after you enable S3 RTC on the respective replication rule\. You can view replication metrics on the Amazon S3 or CloudWatch console\. For information, see [Using Replication Metrics to Monitor Replication Configurations](https://docs.aws.amazon.com/AmazonS3/latest/dev/using-replication-metrics.html) in the *Amazon Simple Storage Service Developer Guide*\.