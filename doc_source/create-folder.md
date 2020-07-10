# Creating a folder<a name="create-folder"></a>

This section describes how to use the Amazon S3 console to create a folder\.

**To create a folder**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to create a folder in\.  
![\[Choose the name of the bucket.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Create folder**\.  
![\[Choose Create folder button in the Amazon S3 console.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/create-folder.png)

1. Enter a name for the folder \(for example, **favorite\-pics**\)\. Choose the encryption setting for the folder object, and then choose **Save**\.  
![\[Type the name of the folder in the Amazon S3 console.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/type-folder-name.png)

1. If you don't want to use encryption with your folder, choose **None**\. 

1. If you want to encrypt your object using keys that are managed by Amazon S3, follow these steps:

   1. Choose **AES\-256**\. 

     For more information about using Amazon S3 server\-side encryption to encrypt your data, see [Protecting data with Amazon S3 managed encryption keys classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. If you want to encrypt your object using AWS KMS, follow these steps:

   1. Choose **AWS\-KMS**\.

   1. Choose an AWS KMS customer master key \(CMK\)\.

      The list shows [customer managed CMKs](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#customer-cmk) that you have created and your AWS managed CMK for Amazon S3\. For more information about creating a customer managed AWS KMS CMK, see [Creating Keys](https://docs.aws.amazon.com/kms/latest/developerguide/UsingServerSideEncryption.html) in the *AWS Key Management Service Developer Guide*\. 
**Important**  
To encrypt objects in the bucket, you can use only the CMKs that are enabled in the same AWS Region as the bucket\. Amazon S3 only supports *symmetric* CMKs and does not support *asymmetric* CMKs\. For more information, see [Using symmetric and asymmetric keys](https://docs.aws.amazon.com/kms/latest/developerguide/symmetric-asymmetric.html)\.  
The Amazon S3 console only lists 100 KMS CMKs per Region\. If you have more than 100 CMKs in the same Region, you can see only the first 100 CMKs in the S3 console\. To use anAWS KMS KMS CMK that is not listed in the console, choose **Custom KMS ARN**, and enter the KMS CMK ARN\.

1. Choose **Save**\.