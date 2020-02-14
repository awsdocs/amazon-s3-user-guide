# How Do I Create an S3 Bucket?<a name="create-bucket"></a>

Before you can upload data to Amazon S3, you must create a bucket in one of the AWS Regions to store your data in\. After you create a bucket, you can upload an unlimited number of data objects to the bucket\. 

The AWS account that creates the bucket owns it\. By default, you can create up to 100 buckets in each of your AWS accounts\. If you need additional buckets, you can increase your account bucket quota to a maximum of 1,000 buckets by submitting a service quota increase\. For information about how to increase your bucket quota, see [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *AWS General Reference*\. 

Buckets have configuration properties, including geographical Region, access settings for the objects in the bucket, and other metadata\. 

**Topics**
+ [Step 1: Choose a Bucket Name and Region](#step-one-choose-bucket-name-region)
+ [Step 2: Configure Options](#step-two-configure-bucket-options)
+ [Step 3: Set Permissions](#step-three-set-bucket-permissions)
+ [Step 4: Review](#step-four-review-bucket-settings)
+ [More Info](#create-bucket-moreinfo)

## Step 1: Choose a Bucket Name and Region<a name="step-one-choose-bucket-name-region"></a>

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Choose **Create bucket**\.  
![\[Create bucket button in the S3 console.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket.png)

   The **Create bucket** wizard opens to the **Name and region** page\.  
![\[Name and Region page in the Create bucket wizard.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-name-region.png)

1. In **Bucket name**, enter a DNS\-compliant name for your bucket\.

   The bucket name must:
   + Be unique across all of Amazon S3\.
   + Be between 3 and 63 characters long\.
   + Be without uppercase characters\.
   + Start with a lowercase letter or number\.

   The bucket name is visible in the URL that points to the objects in the bucket\. After you create the bucket, you cannot change the name\. For information about naming buckets, see [Rules for Bucket Naming](https://docs.aws.amazon.com/AmazonS3/latest/dev/BucketRestrictions.html#bucketnamingrules) in the *Amazon Simple Storage Service Developer Guide*\.

1. In **Region**, choose the AWS Region where you want the bucket to reside\. 

   Choose a Region close to you to minimize latency and costs and address regulatory requirements\. Objects stored in a Region never leave that Region unless you explicitly transfer them to another Region\. For a list of Amazon S3 AWS Regions, see [AWS Service Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) in the *Amazon Web Services General Reference*\.

1. \(Optional\) If you want to copy settings from an existing bucket to use for your new bucket, take the following steps:

   1. Choose **Copy settings from an existing bucket**\.

   1. Choose the bucket name\.

   1. To create your new bucket and exit **Create bucket**, choose **Create**\.

   Amazon S3 creates your new bucket, copying the settings for versioning, tags, and logging from the existing bucket that you selected\. You can skip the remaining steps\.

1. \(Optional\) If you want to choose the settings for your new bucket, choose **Next**\.

   The **Configure options** page opens, where you can configure your bucket properties\. You can configure properties and Amazon CloudWatch metrics during or after bucket creation\.   
![\[Configure options page in the Create bucket wizard.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-configure-options.png)

## Step 2: Configure Options<a name="step-two-configure-bucket-options"></a>

1. To enable object versioning for the bucket, select **Keep all versions of an object in the same bucket**\. 

   For more information about enabling versioning, see [How Do I Enable or Suspend Versioning for an S3 Bucket?](enable-versioning.md)

1. To enable server access logging on the bucket, select **Log requests for access to your bucket**\.

   Server access logging provides detailed records for the requests that are made to your bucket\.  For more information about enabling server access logging, see [How Do I Enable Server Access Logging for an S3 Bucket?](server-access-logging.md)

1. To add a cost allocation bucket tag, follow these steps:

   1. Enter a **Key** and a **Value**\.

   1. To add another tag, choose **Add another**\. 

   You can use cost allocation bucket tags to annotate billing for your use of a bucket\. Each tag is a key\-value pair that represents a label that you assign to a bucket\. For more information about cost allocation tags, see [Using Cost Allocation S3 Bucket Tags](https://docs.aws.amazon.com/AmazonS3/latest/dev/CostAllocTagging.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. To enable object\-level logging with AWS CloudTrail, select **Record object\-level API activity by using CloudTrail for an additional cost**\. 

   For more information about enabling object\-level logging, see [How Do I Enable Object\-Level Logging for an S3 Bucket with AWS CloudTrail Data Events?](enable-cloudtrail-events.md)

1. To enable default encryption for the bucket, select **Automatically encrypt objects when they are stored in S3**\. 

   You can enable default encryption for a bucket so that all objects are encrypted when they are stored in the bucket\. For more information about enabling default encryption, see [How Do I Enable Default Encryption for an Amazon S3 Bucket?](default-bucket-encryption.md)

1. To allow objects in the bucket to be locked, follow these steps: 

   1. Choose **Advanced settings**\.

   1. Choose **Permanently allow objects in this bucket to be locked**\.

   Object lock requires that you enable versioning on the bucket\. For more information about object locking, see [Introduction to Amazon S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. To configure CloudWatch request metrics for the bucket, select **Monitor requests in your bucket for an additional cost**\.

    For more information about CloudWatch request metrics, see [How Do I Configure Request Metrics for an S3 Bucket?](configure-metrics.md)

1. Choose **Next**\.

   The **Set permissions** page opens, where you can manage the permissions on the bucket that you are creating\. You can set permissions during or after bucket creation\.  
![\[Set permissions page in the Create bucket wizard.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-set-permissions.png)

## Step 3: Set Permissions<a name="step-three-set-bucket-permissions"></a>

1. Under **Block public access \(bucket settings\)**, we recommend that you do not change the default settings\. 

   You can change the permissions after you create the bucket\. For more information about setting bucket permissions, see [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md) If you intend to use the bucket to host a static website, you can edit the block public access settings after you create it\. For more information, see [How Do I Configure an S3 Bucket for Static Website Hosting?](static-website-hosting.md) 
**Warning**  
We highly recommend that you keep the default access settings for blocking public access to the bucket that you are creating\. Public access means that anyone in the world can access the objects in the bucket\. 

1. If you want to use the bucket to store Amazon S3 server access logs, in **Manage system permissions**, choose **Grant Amazon S3 Log Delivery group write access to this bucket**\. 

   For more information about server access logs, see [How Do I Enable Server Access Logging for an S3 Bucket?](server-access-logging.md)

1. Choose **Next**\.

   The **Review** page opens, where you can review your bucket configuration before creating the bucket\.  
![\[Review page in the Create bucket wizard.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-review.png)

## Step 4: Review<a name="step-four-review-bucket-settings"></a>

1. On the **Review** page, verify the settings\. 

1. If you want to change the **Name and region**, **Options**, or **Permissions**, choose **Edit**, and modify the settings as needed\.

1. When your current settings are correct, choose **Create bucket**\.

## More Info<a name="create-bucket-moreinfo"></a>
+ [How Do I Delete an S3 Bucket?](delete-bucket.md)
+ [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md)