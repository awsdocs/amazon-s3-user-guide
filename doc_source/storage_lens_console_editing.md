# Updating an Amazon S3 Storage Lens dashboard<a name="storage_lens_console_editing"></a>

**To update an S3 Storage Lens dashboard**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the navigation pane, choose **S3 Storage Lens**\.

1. Choose the dashboard that you want to edit, and then choose **Edit** at the top of the list\.
**Note**  
You can't change the following:  
The dashboard name 
The home Region
The dashboard scope of the default dashboard, which is scoped to your entire account's storage\.

1. On the dashboard configuration page, in the **General** section, you can update and add tags to your dashboard\.

   You can use tags to manage permissions for your dashboard and to track costs for S3 Storage Lens\. For more information, see [Controlling access using resource tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) in the *IAM User Guide* and [AWS\-Generated Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/aws-tags.html) in the *AWS Billing and Cost Management User Guide*\.
**Note**  
You can add up to 50 tags to your dashboard configuration\.

1.  In the **Dashboard scope** section, do the following:

   1.  Update the Regions and buckets that you want S3 Storage Lens to include or exclude in the dashboard\. 
**Note**  
You can either include or exclude Regions and buckets\. This option is limited to Regions only when creating organization\-level dashboards across member accounts in your organization\. 

     Update the buckets in your selected Regions that you want S3 Storage Lens to include or exclude\. You can either include or exclude buckets, but not both\. This option is not present when creating organization\-level dashboards\.

1.  In the **Metrics selection** section, update the type of metrics that you want to aggregate for this dashboard\. 

   You can choose **Free Metrics** to include usage metrics aggregated at the bucket level with 14\-day retention\. 

   For an additional charge, you can choose **Advanced Metrics and Recommendations**\. This includes usage metrics aggregated at the prefix\-level, activity metrics aggregated by bucket, 15\-month data retention, and contextual recommendations that help you further optimize storage costs and apply data protection best practices\. For more information, see [Amazon S3 pricing](http://aws.amazon.com/s3/pricing/)\.

   If you chose to enable Advanced Metrics and Recommendations, you can choose additional options as follows: 

   1. The option to enable activity metrics is included with the advanced metrics and recommendations\. This option helps you track requests and errors for objects in your dashboard scope\.

   1. Choose **Enable prefix aggregation** if you want to aggregate your **usage** metrics at the prefix level so that you can receive detailed insights for your top prefixes in each bucket\.

   1. If you chose **prefix aggregation**, you must choose the minimum prefix threshold size that S3 Storage Lens will collect for this dashboard\. For example, a prefix threshold of 5 percent indicates that prefixes that make up 5 percent or greater in size of the storage of the bucket will be aggregated\. 

   1. You must also choose the prefix depth\. This option indicates the max number of levels up to which the prefixes are evaluated\. Prefix depth must be less than 10\.

   1. Enter a prefix delimiter character\. This is the value that is used to identify each prefix level\. The default value in Amazon S3 for this is the **/** character, but your storage structure might use other delimiter characters\.

   You can then view the metrics included for this dashboard\.

1.  In the **Metrics Export** section, do the following:

   1. Choose **Enable** if you want to create a metrics export that will be placed daily in a destination bucket of your choice\. The metrics export is in CSV or Apache Parquet format and represents the same scope of data as your S3 Storage Lens dashboard data, without the recommendations\.

   1.  If enabled, choose the output format of your daily metrics export\. You can choose between **CSV** or **Apache Parquet**\. Parquet is an open source file format for Hadoop that stores nested data in a flat columnar format\.

   1. Update the destination S3 bucket of your metrics export\. You can choose between a bucket in the current account for the S3 Storage Lens dashboard, or choose another AWS account if you have the destination bucket permissions and the destination bucket owner account ID\.

   1. Update the destination \(format: `s3://bucket/prefix`\) of the destination S3 bucket\. The bucket address must be in S3 format in the home Region of your S3 Storage Lens dashboard\. 
**Note**  
Amazon S3 will update the permissions policy on the destination bucket to allow S3 to place data in that bucket\. 
 The S3 console will show you the explicit destination bucket permission that will be added by Amazon S3 to the destination bucket policy in the destination bucket permission box\. 
If your metrics export destination S3 bucket has server\-side encryption already enabled, all export files placed there must also have server\-side encryption enabled\. 

   1. If you chose to enable server\-side encryption for your dashboard, you must choose an encryption key type\. You can choose between an [Amazon S3 key](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) \(SSE\-S3\) and an [AWS Key Management Service \(AWS KMS\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingKMSEncryption.html) key \(SSE\-KMS\)\.

   1.  If you chose an AWS KMS key, you must choose from your KMS master keys or enter a master key Amazon Resource Name \(ARN\)\.