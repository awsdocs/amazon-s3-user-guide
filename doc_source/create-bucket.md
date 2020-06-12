# How do I create an S3 Bucket?<a name="create-bucket"></a>

Before you can upload data to Amazon S3, you must create a bucket in one of the AWS Regions to store your data\. After you create a bucket, you can upload an unlimited number of data objects to the bucket\. 

The AWS account that creates the bucket owns it\. By default, you can create up to 100 buckets in each of your AWS accounts\. If you need additional buckets, you can increase your account bucket quota to a maximum of 1,000 buckets by submitting a service quota increase\. For information about how to increase your bucket quota, see [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *AWS General Reference*\. 

Buckets have configuration properties, including geographical Region, access settings for the objects in the bucket, and other metadata\. 

**To create a bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Choose **Create bucket**\.

   The **Create bucket** wizard opens\.

1. In **Bucket name**, enter a DNS\-compliant name for your bucket\.

   The bucket name must:
   + Be unique across all of Amazon S3\.
   + Be between 3 and 63 characters long\.
   + Not contain uppercase characters\.
   + Start with a lowercase letter or number\.

   After you create the bucket, you can't change its name\. For information about naming buckets, see [Rules for Bucket Naming](https://docs.aws.amazon.com/AmazonS3/latest/dev/BucketRestrictions.html#bucketnamingrules) in the *Amazon Simple Storage Service Developer Guide*\.
**Important**  
Avoid including sensitive information, such as account numbers, in the bucket name\. The bucket name is visible in the URLs that point to the objects in the bucket\.

1. In **Region**, choose the AWS Region where you want the bucket to reside\. 

   Choose a Region close to you to minimize latency and costs and address regulatory requirements\. Objects stored in a Region never leave that Region unless you explicitly transfer them to another Region\. For a list of Amazon S3 AWS Regions, see [AWS Service Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) in the *Amazon Web Services General Reference*\.

1. In **Bucket settings for Block Public Access**, choose the Block Public Access settings that you want to apply to the bucket\. 

   We recommend that you leave all settings enabled unless you know you need to turn one or more of them off for your use case, such as to host a public website\. Block public access settings that you enable for the bucket will also be enabled for all access points that you create on the bucket\. For more information about blocking public access, see [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. \(Optional\) If you want to enable S3 Object Lock:

   1. Choose **Advanced settings**, and read the message that appears\.
**Important**  
You can only enable S3 Object Lock for a bucket when you create it\. If you enable Object Lock for the bucket, you can't disable it later\. Enabling Object Lock also enables versioning for the bucket\. After you enable Object Lock for the bucket, you must configure the Object Lock settings before any objects in the bucket will be protected\. For more information about configuring protection for objects, see [How do I lock an Amazon S3 object?](object-lock.md)\.

   1. If you want to enable Object Lock, enter *enable* in the text box and choose **Confirm**\.

   For more information about the S3 Object Lock feature, see [Locking Objects Using Amazon S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. Choose **Create bucket**\.

## More info<a name="create-bucket-moreinfo"></a>
+ [How do I delete an S3 Bucket?](delete-bucket.md)
+ [How do I set ACL bucket permissions?](set-bucket-permissions.md)