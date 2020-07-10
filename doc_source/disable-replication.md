# How do I manage the replication rules for an S3 Bucket?<a name="disable-replication"></a>

Replication is the automatic, asynchronous copying of objects across buckets in the same or different AWS Regions\. It replicates newly created objects and object updates from a source bucket to a specified destination bucket\. 

You use the Amazon S3 console to add replication rules to the source bucket\. Replication rules define the source bucket objects to replicate and the destination bucket where the replicated objects are stored\. For more information about replication, see [Replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.htm) in the *Amazon Simple Storage Service Developer Guide*\.

You can manage replication rules on the **Replication** page\. You can add, view, enable, disable, delete, and change the priority of the replication rules\. For information about adding replication rules to a bucket, see [How do I add a replication rule to an S3 bucket?](enable-replication.md)\.

**To manage the replication rules for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Bucket name list with a bucket selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Management**, and then choose **Replication**\.  
![\[Management tab with Replication button selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-replication.png)

1. You change the replication rules in the following ways\.
   + To change settings that affect all the replication rules in the bucket, choose **Edit global settings**\.   
![\[Replication page with Edit global settings highlighted\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-edit.png)

     You can change the destination bucket, and the IAM role\. If needed, you can copy the required bucket policy for cross\-account destination buckets\.   
![\[Editing global rule settings\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-global-edit.png)
   + To change a replication rule, select the rule and choose **Edit**, which starts the Replication wizard to help you make the change\. For information about using the wizard, see [How do I add a replication rule to an S3 bucket?](enable-replication.md)\.  
![\[Selecting a rule to edit in the list\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-rule-edit.png)
   + To enable or disable a replication rule, select the rule, choose **More**, and in the drop\-down list, choose **Enable rule** or **Disable rule**\. You can also disable, enable, or delete all the rules in the bucket from the **More** drop\-down list\.  
![\[More drop-down list with Disable rule selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-rule-disable.png)
   + To change the rule priorities, choose **Edit priorities**\. You can then change the priority for each rule under the **Priority** column heading\. Choose **Save **to save your changes\.

     You set rule priorities to avoid conflicts caused by objects that are included in the scope of more than one rule\. In the case of overlapping rules, Amazon S3 uses the rule priority to determine which rule to apply\. The higher the number, the higher the priority\. For more information about rule priority, see [Replication Configuration Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-add-config.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[More drop-down list with Disable rule selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-rule-priority.png)

## More info<a name="disable-replication-moreinfo"></a>
+ [How do I add a replication rule to an S3 bucket?](enable-replication.md)
+ [Replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.html) in the *Amazon Simple Storage Service Developer Guide*