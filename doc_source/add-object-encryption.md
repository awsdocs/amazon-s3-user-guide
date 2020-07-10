# How do I add encryption to an S3 object?<a name="add-object-encryption"></a>

This topic describes how to set or change the type of encryption an object using the Amazon S3 console\.

**Note**  
If you change an object's encryption, a new object is created to replace the old one\. If S3 Versioning is enabled, a new version of the object is created, and the existing object becomes an older version\. The role that changes the property also becomes the owner of the new object or \(object version\)\. 

**To add or change encryption for an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the object\.

1. In the **Name** list, choose the name of the object that you want to add or change encryption for\.

1. Choose **Properties**, and then choose **Encryption**\.

   The **Encryption** dialog box opens, giving you three choices for object encryption:
   + **None**‐ No object encryption\.
   + **AES\-256** ‐ Server\-side encryption with Amazon S3 managed keys \(SSE\-S3\)\.
   + **AWS‐KMS** ‐ Server\-side encryption with AWS Key Management Service \(AWS KMS\) customer master keys \(SSE\-KMS\)\.

1. If you want to remove encryption from an object that already has encryption settings, choose **None** and then choose **Save**\.   
![\[Console screenshot of the encryption dialog box with the none option selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/remove-encryption-none.png)

1. If you want to encrypt your object using keys that are managed by Amazon S3, follow these steps:

   1. Choose**AES\-256**\. 

      For more information about using Amazon S3 server\-side encryption to encrypt your data, see [Protecting Data with Amazon S3\-Managed Encryption Keys Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

   1. Choose **Save**\.  
![\[Console screenshot of the encryption dialog box with the AES-256 option selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-encryption-aes256.png)

1. If you want to encrypt your object using AWS KMS, follow these steps:

   1. Choose **AWS\-KMS**\.

   1. Choose an AWS KMS customer master key \(CMK\)\.

      The list shows [customer managed CMKs](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#customer-cmk) that you have created and your AWS managed CMK for Amazon S3\. For more information about creating a customer managed AWS KMS CMK, see [Creating Keys](https://docs.aws.amazon.com/kms/latest/developerguide/UsingServerSideEncryption.html) in the *AWS Key Management Service Developer Guide*\. 
**Important**  
The Amazon S3 console lists only 100 AWS KMS CMKs per AWS Region\. If you have more than 100 CMKs in the same Region, you can see only the first 100 CMKs in the S3 console\. To use a KMS CMK that is not listed in the console, choose **Custom KMS ARN**, and enter the KMS CMK ARN\.

   1. Choose **Save**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-encryption-kms-key.png)
**Important**  
To encrypt objects in the bucket, you can use only CMKs that are enabled in the same AWS Region as the bucket\. Amazon S3 only supports symmetric CMKs\. Amazon S3 does not support asymmetric CMKs\. For more information, see [Using Symmetric and Asymmetric Keys](https://docs.aws.amazon.com/kms/latest/developerguide/symmetric-asymmetric.html)\.

1. To give an external account the ability to use an object that is protected by an AWS KMS CMK, follow these steps: 

   1. Choose **AWS\-KMS**\.

   1. Enter the Amazon Resource Name \(ARN\) for the external account\.

   1. Choose **Save**\.

      Administrators of an external account that have usage permissions to an object protected by your AWS KMS CMK can further restrict access by creating a resource\-level AWS Identity and Access Management \(IAM\) policy\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-encryption-kms-select-custom-arn.png)

## More info<a name="add-object-encryption-moreinfo"></a>
+  [How do I enable default encryption for an Amazon S3 bucket?](default-bucket-encryption.md)
+ [Amazon S3 default encryption for S3 buckets](https://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) in the *Amazon Simple Storage Service Developer Guide*
+  [How do I view the properties of an object?](view-object-properties.md)
+  [Uploading, downloading, and managing objects](upload-download-objects.md)