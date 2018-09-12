# How Do I Manage the Cross\-Region Replication Rules for an S3 Bucket?<a name="disable-crr"></a>

Cross\-region replication is the automatic, asynchronous copying of objects across buckets in different AWS Regions\. It replicates newly created objects, object updates, and object deletions from a source bucket to a destination bucket in a different Region\. 

You use the Amazon S3 console to add replication rules to the source bucket\. Replication rules define the source bucket objects to replicate and the destination bucket where the replicated objects are stored\. For more information about cross\-region replication, see [Cross\-Region Replication](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.htm) in the *Amazon Simple Storage Service Developer Guide*\.

You can manage replication rules on the **Replication** page\. You can add, view, enable, disable, and delete the replication rules\. For information about adding replication rules to a bucket, see [How Do I Add a Cross\-Region Replication \(CRR\) Rule to an S3 Bucket?](enable-crr.md)\.

**To manage the cross\-region replication rules for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Bucket name list with a bucket selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Management**, and then choose **Replication**\.  
![\[Management tab with Replication button selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-replication.png)

1. You change the replication rules in the following ways\.
   + To change settings that affect all the replication rules in the bucket, choose **Edit global settings**\.   
![\[Replication page with Edit global settings highlighted\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-edit.png)

     You can change the scope of the objects to be copied, the destination bucket, and the IAM role\. If needed, you can copy the required bucket policy for cross\-account destination buckets\. 

     You can set the scope to **All contents** \(for all objects in the bucket\) or **Only objects with a specific prefix**\. If the scope is **All contents**, there can be only one rule\. When you choose a different scope, the Replication wizard starts to help you make the change\. For information about using the wizard, see [How Do I Add a Cross\-Region Replication \(CRR\) Rule to an S3 Bucket?](enable-crr.md)\.  
![\[Changing the scope of the objects being copied\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-global-edit.png)
   + To change a replication rule, select the rule and choose **Edit**, which starts the Replication wizard to help you make the change\. For information about using the wizard, see [How Do I Add a Cross\-Region Replication \(CRR\) Rule to an S3 Bucket?](enable-crr.md)\.  
![\[Selecting a rule to edit in the list\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-rule-edit.png)
   + To enable or disable a replication rule, select the rule, choose **More**, and in the drop\-down list, choose **Enable rule** or **Disable rule**\. You can also disable, enable, or delete all the rules in the bucket from the **More** drop\-down list\.  
![\[More drop-down list with Disable rule selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-rule-disable.png)

## More Info<a name="disable-crr-moreinfo"></a>
+ [How Do I Add a Cross\-Region Replication \(CRR\) Rule to an S3 Bucket?](enable-crr.md)
+ [Cross\-Region Replication](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) in the *Amazon Simple Storage Service Developer Guide*