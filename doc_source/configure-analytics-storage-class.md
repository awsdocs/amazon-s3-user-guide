# How Do I Configure Storage Class Analysis?<a name="configure-analytics-storage-class"></a>

By using the Amazon S3 analytics storage class analysis tool, you can analyze storage access patterns to help you decide when to transition the right data to the right storage class\. Storage class analysis observes data access patterns to help you determine when to transition less frequently accessed STANDARD storage to the STANDARD\_IA \(IA, for infrequent access\) storage class\. For more information about STANDARD\_IA, see the [Amazon S3 FAQ](https://aws.amazon.com/s3/faqs/#sia) and [Storage Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Important**  
Storage class analysis does not give recommendations for transitions to the ONEZONE\_IA or S3 Glacier storage classes\.

For more information about analytics, see [Amazon S3 Analytics – Storage Class Analysis](https://docs.aws.amazon.com/AmazonS3/latest/dev/analytics-storage-class.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To configure storage class analysis**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket for which you want to configure storage class analysis\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose the **Management** tab, and then choose **Analytics**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab.png)

1. Choose **Add**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/storage-class-analysis-add-filter.png)

1. Type a name for the filter\. If you want to analyze the whole bucket, leave the **Prefix / tags **field empty\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/storage-class-analysis-filter.png)

1. In the **Prefix / tags ** field, type text for the prefix or tag for the objects that you want to analyze, or choose from the dropdown list that appears when you start typing\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/storage-class-analysis-prefix.png)

1. If you chose **tag**, enter a value for the tag\. You can enter one prefix and multiple tags\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/storage-class-analysis-tag.png)

1. Optionally, you can choose **Export data** to export analysis reports to a comma\-separated values \(\.csv\) flat file\. Choose a destination bucket where the file can be stored\. You can type a prefix for the destination bucket\. The destination bucket must be in the same AWS Region as the bucket for which you are setting up the analysis\. The destination bucket can be in a different AWS account\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/storage-class-analysis-export.png)

1. Choose **Save**\.

 Amazon S3 creates a bucket policy on the destination bucket that grants Amazon S3 write permission\. This allow it to write the export data to the bucket\. 

 If an error occurs when you try to create the bucket policy, you'll be given instructions on how to fix it\. For example, if you chose a destination bucket in another AWS account and do not have permissions to read and write to the bucket policy, you'll see the following message\. You must have the destination bucket owner add the displayed bucket policy to the destination bucket\. If the policy is not added to the destination bucket you won’t get the export data because Amazon S3 doesn’t have permission to write to the destination bucket\. If the source bucket is owned by a different account than that of the current user, then the correct account ID of the source bucket must be substituted in the policy\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/analytics-bucket-policy.png)

For information about the exported data and how the filter works, see [Amazon S3 Analytics – Storage Class Analysis](https://docs.aws.amazon.com/AmazonS3/latest/dev/analytics-storage-class.html) in the *Amazon Simple Storage Service Developer Guide*\.

**More Info**  
 [Storage management](storage-management.md)