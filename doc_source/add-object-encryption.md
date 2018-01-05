# How Do I Add Encryption to an S3 Object?<a name="add-object-encryption"></a>

This topic describes how to set or change the type of encryption an object is using\. 

**To add encryption to an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the object\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, choose the name of the object that you want to add encryption to\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-name-select.png)

1. Choose **Properties**, and then choose **Encryption**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-properties-tab.png)

1. Select **AES\-256** or **AWS\-KMS**\.

   1. To encrypt your object using keys that are managed by Amazon S3, select **AES\-256**\. For more information about using Amazon S3 server\-side encryption to encrypt your data, see [Protecting Data with Amazon S3\-Managed Encryption Keys Classes](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-encryption-aes256.png)

   1. To encrypt your object using AWS Key Management Service \(AWS KMS\), choose **AWS\-KMS**, choose a master key from the list of the AWS KMS master keys that you have created, and then choose **Save**\.
**Note**  
To encrypt objects in the bucket, you can use only keys that are enabled in the same AWS Region as the bucket\. 

      For more information about creating an AWS KMS key, see [Creating Keys](http://docs.aws.amazon.com/kms/latest/developerguide/UsingServerSideEncryption.html) in the *AWS Key Management Service Developer Guide*\. For more information, see [Protecting Data with AWS KMS–Managed Key](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-encryption-kms-key.png)

      You can give an external account the ability to use an object that is protected by an AWS KMS key\. To do this, select **Custom KMS ARN** from the list, type the Amazon Resource Name \(ARN\) for the external account, and then choose **Save**\. Administrators of an external account that have usage permissions to an object protected by your AWS KMS key can further restrict access by creating a resource\-level AWS Identity and Access Management \(IAM\) policy\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-encryption-kms-select-custom-arn.png)  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-encryption-kms-custom-arn.png)

## More Info<a name="add-object-encryption-moreinfo"></a>

+  [How Do I View the Properties of an Object?](view-object-properties.md)

+  [Uploading, Downloading, and Managing Objects](upload-download-objects.md)