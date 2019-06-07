# How Do I Create an S3 Bucket?<a name="create-bucket"></a>

Before you can upload data to Amazon S3, you must create a bucket in one of the AWS Regions to store your data in\. After you create a bucket, you can upload an unlimited number of data objects to the bucket\. 

A bucket is owned by the AWS account that created it\. By default, you can create up to 100 buckets in each of your AWS accounts\. If you need additional buckets, you can increase your account bucket limit to a maximum of 1,000 buckets by submitting a service limit increase\. For information about how to increase your bucket limit, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *AWS General Reference*\. 

Buckets have configuration properties, including their geographical region, who has access to the objects in the bucket, and other metadata\. 

**To create an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Choose **Create bucket**\.  
![\[Create bucket button in the S3 console.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket.png)

1. On the **Name and region** page, type a name for your bucket and choose the AWS Region where you want the bucket to reside\. Complete the fields on this page as follows:

   1. For **Bucket name**, type a unique DNS\-compliant name for your new bucket\. Follow these naming guidelines: 
      + The name must be unique across all existing bucket names in Amazon S3\. 
      + The name must not contain uppercase characters\.
      + The name must start with a lowercase letter or number\.
      + The name must be between 3 and 63 characters long\.
      + After you create the bucket you cannot change the name, so choose wisely\. 
      + Choose a bucket name that reflects the objects in the bucket because the bucket name is visible in the URL that points to the objects that you're going to put in your bucket\.

      For information about naming buckets, see [Rules for Bucket Naming](https://docs.aws.amazon.com/AmazonS3/latest/dev//BucketRestrictions.html#bucketnamingrules) in the *Amazon Simple Storage Service Developer Guide*\.

   1. For **Region**, choose the AWS Region where you want the bucket to reside\. Choose a Region close to you to minimize latency and costs, or to address regulatory requirements\. Objects stored in a Region never leave that Region unless you explicitly transfer them to another Region\. For a list of Amazon S3 AWS Regions, see [Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) in the *Amazon Web Services General Reference*\.

   1. \(Optional\) If you have already set up a bucket that has the same settings that you want to use for the new bucket that you want to create, you can set it up quickly by choosing **Copy settings from an existing bucket**, and then choosing the bucket whose settings you want to copy\.

      The settings for the following bucket properties are copied: versioning, tags, and logging\.

   1. Do one of the following:
      + If you copied settings from another bucket, choose **Create**\. You're done, so skip the following steps\.
      + If not, choose **Next**\.  
![\[Name and region page in the Create bucket wizard.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-name-region.png)

1. On the **Configure options** page, you can configure the following properties and Amazon CloudWatch metrics for the bucket\. Or, you can configure these properties and CloudWatch metrics later, after you create the bucket\.

   1. 

****Versioning****

      Select **Keep all versions of an object in the same bucket\.** to enable object versioning for the bucket\. For more information on enabling versioning, see [How Do I Enable or Suspend Versioning for an S3 Bucket?](enable-versioning.md)\.

   1. 

****Server access logging****

      Select **Log requests for access to your bucket\.** to enable server access logging on the bucket\. Server access logging provides detailed records for the requests that are made to your bucket\.  For more information about enabling server access logging, see [How Do I Enable Server Access Logging for an S3 Bucket?](server-access-logging.md)\.  
![\[The create bucket wizard configure options page showing versioning and server access logging check boxes.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-set-properties-1.png)

   1. 

****Tags****

      You can use cost allocation bucket tags to annotate billing for your use of a bucket\. Each tag is a key\-value pair that represents a label that you assign to a bucket\.

      To add a tag, enter a *Key* and a *Value*\. Choose **Add another** to add another tag\. For more information about cost allocation tags, see [Using Cost Allocation S3 Bucket Tags](https://docs.aws.amazon.com/AmazonS3/latest/dev//CostAllocTagging.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[The create bucket wizard configure options page showing cost allocation bucket tags fields.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-set-properties-2.png)

   1. 

****Object\-level logging****

      Select **Record object\-level API activity by using CloudTrail for an additional cost** to enable object\-level logging with CloudTrail\. For more information about enabling object\-level logging, see [How Do I Enable Object\-Level Logging for an S3 Bucket with AWS CloudTrail Data Events?](enable-cloudtrail-events.md)\.

   1. 

****Default encryption****

      Select **Automatically encrypt objects when they are stored in S3** to enable default encryption for the bucket\. You can enable default encryption for a bucket so that all objects are encrypted when they are stored in the bucket\. For more information about enabling default encryption, see [How Do I Enable Default Encryption for an S3 Bucket?](default-bucket-encryption.md)\.  
![\[The create bucket wizard configure options page showing object-level logging and default encryption check boxes.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-set-properties-3.png)

   1. 

****Object lock****

      Select **Permanently allow objects in this bucket to be locked** if you want to be able to lock objects in the bucket\. Object lock requires that you enable versioning on the bucket\. For more information about object locking, see [Introduction to Amazon S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) in the *Amazon Simple Storage Service Developer Guide*  
![\[Configure options page showing the object locking check box.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-object-lock.png)

   1. 

****CloudWatch request metrics****

      Select **Monitor requests in your bucket for an additional cost\.** to configure CloudWatch request metrics for the bucket\. For more information about CloudWatch request metrics, see [How Do I Configure Request Metrics for an S3 Bucket?](configure-metrics.md)\.  
![\[Configure options page showing the CloudWatch metrics check box.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-config-management.png)

1. Choose **Next**\.

1. On the **Set permissions** page, you manage the permissions that are set on the bucket that you are creating\. 

   Under **Block public access \(bucket settings\)**, we recommend that you do not change the default settings that are listed under **Block all public access**\. You can change the permissions after you create the bucket\. For more information about setting bucket permissions, see [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md)\. 
**Warning**  
We highly recommend that you keep the default access settings for blocking public access to the bucket that you are creating\. Public access means that anyone in the world can access the objects in the bucket\. 

   If you intend to use the bucket to store Amazon S3 server access logs, in the **Manage system permissions** list, choose **Grant Amazon S3 Log Delivery group write access to this bucket**\. For more information about server access logs, see [How Do I Enable Server Access Logging for an S3 Bucket?](server-access-logging.md)\.   
![\[Set permissions page with default settings.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-set-permissions.png)

   When you're done configuring permissions on the bucket, choose **Next**\.

1. On the **Review** page, verify the settings\. If you want to change something, choose **Edit**\. If your current settings are correct, choose **Create bucket**\.

## More Info<a name="create-bucket-moreinfo"></a>
+ [How Do I Delete an S3 Bucket?](delete-bucket.md)
+ [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md)