# Configuring an S3 Bucket Key<a name="enable-bucket-key"></a>

When you configure server\-side encryption using AWS Key Management Service \(SSE\-KMS\), you can use an S3 Bucket Key for SSE\-KMS on new objects\. S3 Bucket Keys decrease the request traffic from Amazon S3 to AWS KMS and reduce the cost of SSE\-KMS\. For more information, see [Reducing the cost of AWS KMS server side encryption with Amazon S3 Bucket Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-key.html) in the *Amazon Simple Storage Service Developer Guide*\.

In the S3 console, you can enable or disable an S3 Bucket Key for a new or existing bucket\. Objects in the S3 console inherit their S3 Bucket Key setting from the bucket configuration\. When you enable an S3 Bucket Key for your bucket, new objects that you upload to the bucket use an S3 Bucket Key for server\-side encryption using AWS KMS\. 

In the S3 console, you cannot configure an S3 Bucket Key for an object\. You can only enable or disable an S3 Bucket Key for your buckets\. To enable an S3 Bucket Key for an object as part of a Put or Copy operation, see [Configuring an S3 Bucket Key at the object level using the REST API, AWS SDKs, and AWS CLI](https://docs.aws.amazon.com/AmazonS3/latest/dev/configuring-bucket-key-object.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Uploading, copying, or modifying objects in buckets that have an S3 Bucket Key enabled**  
If you upload, modify, or copy an object in a bucket that has an S3 Bucket Key enabled, the S3 Bucket Key settings for that object might be updated to align with bucket configuration\.

If an object already has an S3 Bucket Key enabled, the S3 Bucket Key settings for that object don't change when you copy or modify the object\. However, if you modify or copy an object that doesn’t have an S3 Bucket Key enabled, and the destination bucket has an S3 Bucket Key configuration, the object inherits the destination bucket's S3 Bucket Key settings\. For example, if your source object doesn't have an S3 Bucket Key enabled but the destination bucket has S3 Bucket Key enabled, an S3 Bucket Key will be enabled for the object\.

**To enable an S3 Bucket Key when you create a new bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Choose **Create bucket**\. 

1. Enter your bucket name, and choose your AWS Region\. 

1. Under **Default encryption**, choose **Enable**\.

1. Under **Encryption type**, choose **AWS Key Management Service key \(SSE\-KMS\)**\.

1. Choose an AWS KMS key:
   + Choose **AWS managed key \(aws/s3\)**\. 
   + Choose **Customer managed key**, and choose a symmetric customer managed CMK in the same Region as your bucket\. 

1. Under **Bucket Key**, choose **Enable**\. 

1. Choose **Create bucket**\. 

   Amazon S3 creates your bucket with an S3 Bucket Key enabled\. New objects that you upload to the bucket will use an S3 Bucket Key\. To disable an S3 Bucket Key, follow the previous steps, and choose **disable**\.

**To enable an S3 Bucket Key for an existing bucket**

1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the bucket that you want to enable an S3 Bucket Key for\.

1. Choose **Properties**\.

1. Under **Default encryption**, choose **Edit**\.

1. Under **Default encryption**, choose **Enable**\.

1. Under **Encryption type**, choose **AWS Key Management Service key \(SSE\-KMS\)**\.

1. Choose an AWS KMS key:
   + Choose **AWS managed key \(aws/s3\)**\. 
   + Choose **Customer managed key**, and choose a symmetric customer managed CMK in the same Region as your bucket\. 

1. Under **Bucket Key**, choose **Enable**\.

1. Choose **Save changes**\.

   Amazon S3 enables an S3 Bucket Key for new objects added to your bucket\. Existing objects don't use the S3 Bucket Key\. To disable an S3 Bucket Key, follow the previous steps, and choose **Disable**\.

## Viewing an S3 Bucket Key setting<a name="bucket-key-settings"></a>

In the S3 console, you can view the S3 Bucket Key settings for your bucket or object\. S3 Bucket Key settings are inherited from the bucket configuration unless the source objects already has an S3 Bucket Key configured\.

To view S3 Bucket Key settings for a bucket or an object that has inherited S3 Bucket Key settings from the bucket configuration, you need permission to perform the `s3:GetEncryptionConfiguration` action\. For more information, see [GetBucketEncryption](https://docs.aws.amazon.com/AmazonS3/latest/API/API_GetBucketEncryption.html) in the *Amazon Simple Storage Service API Reference*\. 

Objects and folders in the same bucket can have different S3 Bucket Key settings\. For example, if you upload an object using the REST API and enable an S3 Bucket Key for the object, the object retains its S3 Bucket Key setting in the destination bucket, even if S3 Bucket Key is disabled in the destination bucket\. As another example, if you enable an S3 Bucket Key for an existing bucket, objects that are already in the bucket do not use an S3 Bucket Key\. However, new objects have an S3 Bucket Key enabled\. 

**To view bucket\-level an S3 Bucket Key setting**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the bucket that you want to enable an S3 Bucket Key for\.

1. Choose **Properties**\.

1. In the **Default encryption** section, under **Bucket Key**, you see the S3 Bucket Key setting for your bucket\.

   If you can’t see the S3 Bucket Key setting, you might not have permission to perform the `s3:GetEncryptionConfiguration` action\. For more information, see [GetBucketEncryption](https://docs.aws.amazon.com/AmazonS3/latest/API/API_GetBucketEncryption.html) in the *Amazon Simple Storage Service API Reference*\. 

**To view the S3 Bucket Key setting for your object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the bucket that you want to enable an S3 Bucket Key for\. 

1. In the **Objects** list, choose your object name\.

1. On the **Details** tab, under **Server\-side encryption settings**, choose **Edit**\. 

   Under **Bucket Key**, you see the S3 Bucket Key setting for your object but you cannot edit it\. 