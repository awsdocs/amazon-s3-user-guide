# How do I add encryption to an S3 object?<a name="add-object-encryption"></a>

This topic describes how to set or change the type of encryption an object using the Amazon S3 console\.

**Note**  
If you change an object's encryption, a new object is created to replace the old one\. If S3 Versioning is enabled, a new version of the object is created, and the existing object becomes an older version\. The role that changes the property also becomes the owner of the new object or \(object version\)\. 

**To add or change encryption for an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the object\.

1. In the **Objects** list, choose the name of the object that you want to add or change encryption for\.

   The **Object overview** opens, displaying the properties for your object\.

1. Under **Server\-side encryption settings**, choose **Edit**\.

   The **Edit server\-side encryption** page opens

1. To enable server\-side encryption for your object, under **Server\-side encryption**, choose **Enable**\.

1. To enable server\-side encryption using an Amazon S3\-managed key, under **Encryption key type**, choose **Amazon S3 key \(SSE\-S3\)**\.

   For more information about using Amazon S3 server\-side encryption to encrypt your data, see [Protecting Data with Amazon S3\-Managed Encryption Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. To enable server\-side encryption using an AWS KMS CMK, follow these steps:

   1. Under **Encryption key type**, choose **AWS Key Management Service key \(SSE\-KMS\)**\.
**Important**  
If you use the AWS KMS option for your default encryption configuration, you are subject to the RPS \(requests per second\) limits of AWS KMS\. For more information about AWS KMS limits and how to request a limit increase, see [AWS KMS limits](https://docs.aws.amazon.com/kms/latest/developerguide/limits.html)\. 

   1. Under **AWS KMS key** choose one of the following:
      + **AWS managed key \(aws/s3\)**
      + **Choose from your KMS master keys**, and choose your **KMS master key**\.
      + **Enter KMS master key ARN**, and enter your AWS KMS key ARN\.
**Important**  
You can only use KMS CMKs that are enabled in the same AWS Region as the bucket\. When you choose **Choose from your KMS master keys**, the S3 console only lists 100 KMS CMKs per Region\. If you have more than 100 CMKs in the same Region, you can only see the first 100 CMKs in the S3 console\. To use a KMS CMK that is not listed in the console, choose **Custom KMS ARN**, and enter the KMS CMK ARN\.  
When you use an AWS KMS CMK for server\-side encryption in Amazon S3, you must choose a CMK that is enabled in the same Region as your bucket\. Additionally, Amazon S3 only supports symmetric CMKs and not asymmetric CMKs\. For more information, see [Using Symmetric and Asymmetric Keys](https://docs.aws.amazon.com/kms/latest/developerguide/symmetric-asymmetric.html) in the *AWS Key Management Service Developer Guide*\.

      For more information about creating an AWS KMS CMK, see [Creating Keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\. For more information about using AWS KMS with Amazon S3, see [Protecting Data with Keys Stored in AWS KMS](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingKMSEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. Choose **Save changes**\.

**Note**  
This action applies encryption to all specified objects\. When encrypting folders, wait for the save operation to finish before adding new objects to the folder\.

## More info<a name="add-object-encryption-moreinfo"></a>
+  [How do I enable default encryption for an Amazon S3 bucket?](default-bucket-encryption.md)
+ [Amazon S3 default encryption for S3 buckets](https://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) in the *Amazon Simple Storage Service Developer Guide*
+  [How do I view the properties of an object?](view-object-properties.md)
+  [Uploading, downloading, and managing objects](upload-download-objects.md)