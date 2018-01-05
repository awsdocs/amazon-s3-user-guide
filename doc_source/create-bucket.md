# How Do I Create an S3 Bucket?<a name="create-bucket"></a>

Before you can upload data to Amazon S3, you must create a bucket in one of the AWS Regions to store your data in\. After you create a bucket, you can upload an unlimited number of data objects to the bucket\. 

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

      For information about naming buckets, see [Rules for Bucket Naming](http://docs.aws.amazon.com/AmazonS3/latest/dev//BucketRestrictions.html#bucketnamingrules) in the *Amazon Simple Storage Service Developer Guide*\.

   1. For **Region**, choose the AWS Region where you want the bucket to reside\. Choose a Region close to you to minimize latency and costs, or to address regulatory requirements\. Objects stored in a Region never leave that Region unless you explicitly transfer them to another Region\. For a list of Amazon S3 AWS Regions, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) in the *Amazon Web Services General Reference*\.

   1. \(Optional\) If you have already set up a bucket that has the same settings that you want to use for the new bucket that you want to create, you can set it up quickly by choosing **Copy settings from an existing bucket**, and then choosing the bucket whose settings you want to copy\.

      The settings for the following bucket properties are copied: versioning, tags, and logging\.

   1. Do one of the following:

      + If you copied settings from another bucket, choose **Create**\. You're done, so skip the following steps\.

      + If not, choose **Next**\.  
![\[Name and region page in the Create bucket wizard.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-name-region.png)

1. On the **Set properties** page, you can configure the following properties for the bucket\. Or, you can configure these properties later, after you create the bucket\.

   1. **Versioning** – Versioning enables you to keep multiple versions of an object in one bucket\. Versioning is disabled for a new bucket by default\. For information on enabling versioning, see [How Do I Enable or Suspend Versioning for an S3 Bucket?](enable-versioning.md)\.

   1. **Server access logging** – Server access logging provides detailed records for the requests that are made to your bucket\. By default, Amazon S3 does not collect server access logs\. For information about enabling server access logging, see [How Do I Enable Server Access Logging for an S3 Bucket?](server-access-logging.md)\.

   1. **Tags** – With AWS cost allocation, you can use tags to annotate billing for your use of a bucket\. A tag is a key\-value pair that represents a label that you assign to a bucket\. To add tags, choose **Tags**, and then choose **Add tag**\. For more information, see [Using Cost Allocation Tags for S3 Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev//CostAllocTagging.html) in the *Amazon Simple Storage Service Developer Guide*\.

   1. **Object\-level logging** – Object\-level logging records object\-level API activity by using CloudTrail data events\. For information about enabling object\-level logging, see [How Do I Enable Object\-Level Logging for an S3 Bucket with AWS CloudTrail Data Events?](enable-cloudtrail-events.md)\.

   1. **Default encryption** – Amazon S3 default encryption provides a way to set the default encryption behavior for an S3 bucket\. You can set default encryption on a bucket so that all objects are encrypted when they are stored in the bucket\. For information about enabling default encryption, see [How Do I Enable Default Encryption for an S3 Bucket?](default-bucket-encryption.md)\.  
![\[Set properties page showing versioning, server access logging, tags, object-level
            logging and default encryption.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-set-properties.png)

1. Choose **Next**\.

1. On the **Set permissions** page, you manage the permissions that are set on the bucket that you are creating\. You can grant read access to your bucket to the general public \(everyone in the world\)\. Granting public read access is applicable to a small subset of use cases such as when buckets are used for websites\. We recommend that you do not change the default setting of **Do not grant public read access to this bucket**\. You can change permissions after you create the bucket\. For more information about setting bucket permissions, see [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md) 
**Warning**  
We highly recommend that you *do not* grant public read access to the bucket that you are creating\. Granting public read access permissions means that anyone in the world can access the objects in the bucket\. 

   When you're done configuring permissions on the bucket, choose **Next**\.  
![\[Set permissions page with default settings.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-bucket-set-permissions.png)

1. On the **Review** page, verify the settings\. If you want to change something, choose **Edit**\. If your current settings are correct, choose **Create bucket**\.

## More Info<a name="create-bucket-moreinfo"></a>

+ [How Do I Delete an S3 Bucket?](delete-bucket.md)

+ [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md)