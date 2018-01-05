# How Do I Enable Default Encryption for an S3 Bucket?<a name="default-bucket-encryption"></a>

Amazon S3 default encryption provides a way to set the default encryption behavior for an S3 bucket\. You can set default encryption on a bucket so that all objects are encrypted when they are stored in the bucket\. The objects are encrypted using server\-side encryption with either Amazon S3\-managed keys \(SSE\-S3\) or AWS KMS\-managed keys \(SSE\-KMS\)\. 

When you use server\-side encryption, Amazon S3 encrypts an object before saving it to disk in its data centers and decrypts it when you download the objects\. For more information about protecting data using server\-side encryption and encryption key management, see [Protecting Data Using Server\-Side Encryption](http://docs.aws.amazon.com/AmazonS3/latest/dev/serv-side-encryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

Default encryption works with all existing and new S3 buckets\. Without default encryption, to encrypt all objects stored in a bucket, you must include encryption information with every object storage request\. You must also set up an S3 bucket policy to reject storage requests that don't include encryption information\. 

There are no new charges for using default encryption for S3 buckets\. Requests to configure the default encryption feature incur standard Amazon S3 request charges\. For information about pricing, see [Amazon S3 Pricing](https://aws.amazon.com/s3/pricing/)\. For SSE\-KMS encryption key storage, AWS Key Management Service \(AWS KMS\) charges apply and are listed at [AWS KMS Pricing](https://aws.amazon.com/kms/pricing/)\. 

**To enable default encryption on an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Screenshot of bucket name list with a bucket name highlighted.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Screenshot of page tabs with the Properties tab chosen.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Choose **Default encryption**\.  
![\[Screenshot of the default encryption option.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-default-encryption.png)

1. Choose **AES\-256** or **AWS\-KMS**\.

   1. To use keys that are managed by Amazon S3 for default encryption, choose **AES\-256**\. For more information about using Amazon S3 server\-side encryption to encrypt your data, see [Protecting Data with Amazon S3\-Managed Encryption Keys](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Default encryption screen with AES-256 chosen.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-default-encryption-aes256.png)
**Important**  
You might need to update your bucket policy when enabling default encryption\. For more information, see [Moving to Default Encryption from Using Bucket Policies for Encryption Enforcement](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html#bucket-encryption-update-bucket-policy) in the *Amazon Simple Storage Service Developer Guide*\.

   1. To use keys that are managed by AWS KMS for default encryption, choose **AWS\-KMS**, and then choose a master key from the list of the AWS KMS master keys that you have created\. Type the Amazon Resource Name \(ARN\) of the AWS KMS key to use\. You can find the ARN for your AWS KMS key in the IAM console, under **Encryption keys**\. Or, you can choose a key name from the drop\-down list\.  
![\[Default encryption screen with AWS-KMS chosen, and a drop-down list with key
                names.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-default-encryption-kms-key.png)
**Important**  
If you use the AWS KMS option for your default encryption configuration, you are subject to the RPS \(requests per second\) limits of AWS KMS\. For more information about AWS KMS limits and how to request a limit increase, see [AWS KMS limits](http://docs.aws.amazon.com/kms/latest/developerguide/limits.html)\. 

      For more information about creating an AWS KMS key, see [Creating Keys](http://docs.aws.amazon.com/kms/latest/developerguide/UsingServerSideEncryption.html) in the *AWS Key Management Service Developer Guide*\. For more information about using AWS KMS with Amazon S3, see [Protecting Data with AWS KMS–Managed Keys](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingKMSEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. Choose **Save**\.

## More Info<a name="default-bucket-encryption-moreinfo"></a>

+ [Amazon S3 Default Encryption for S3 Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) in the *Amazon Simple Storage Service Developer Guide*

+ [How Do I Add Encryption to an S3 Object?](add-object-encryption.md)