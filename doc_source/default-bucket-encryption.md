# How do I enable default encryption for an Amazon S3 bucket?<a name="default-bucket-encryption"></a>

Amazon S3 default encryption provides a way to set the default encryption behavior for an Amazon S3 bucket\. You can set default encryption on a bucket so that all objects are encrypted when they are stored in the bucket\. The objects are encrypted using server\-side encryption with either Amazon S3 managed keys \(SSE\-S3\) or AWS Key Management Service \(AWS KMS\) customer master keys \(CMKs\)\. 

When you configure default encryption using AWS KMS, you can also configure an S3 Bucket Key for your bucket\. For more information, see [Reducing the cost of AWS KMS server side encryption with Amazon S3 Bucket Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-key.html) in the *Amazon Simple Storage Service Developer Guide*\.

When you use server\-side encryption, Amazon S3 encrypts an object before saving it to disk in its data centers and decrypts it when you download the objects\. For more information about protecting data using server\-side encryption and encryption key management, see [Protecting Data Using Server\-Side Encryption](https://docs.aws.amazon.com/AmazonS3/latest/dev/serv-side-encryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

Default encryption works with all existing and new Amazon S3 buckets\. Without default encryption, to encrypt all objects stored in a bucket, you must include encryption information with every object storage request\. You must also set up an Amazon S3 bucket policy to reject storage requests that don't include encryption information\. 

There are no new charges for using default encryption for S3 buckets\. Requests to configure the default encryption feature incur standard Amazon S3 request charges\. For information about pricing, see [Amazon S3 pricing](https://aws.amazon.com/s3/pricing/)\. For SSE\-KMS CMK storage, AWS KMS charges apply and are listed at [AWS KMS pricing](https://aws.amazon.com/kms/pricing/)\. 

**To enable default encryption on an Amazon S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want\. 

1. Choose **Properties**\.

1. Under **Default encryption**, choose **Edit**\.

1. To enable or disable server\-side encryption, choose **Enable** or **Disable**\.

1. To enable server\-side encryption using an Amazon S3\-managed key, under **Encryption key type**, choose **Amazon S3 key \(SSE\-S3\)**\.

   For more information about using Amazon S3 server\-side encryption to encrypt your data, see [Protecting Data with Amazon S3\-Managed Encryption Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.
**Important**  
You might need to update your bucket policy when enabling default encryption\. For more information, see [Moving to Default Encryption from Using Bucket Policies for Encryption Enforcement](https://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html#bucket-encryption-update-bucket-policy) in the *Amazon Simple Storage Service Developer Guide*\.

1. To enable server\-side encryption using an AWS KMS CMK, follow these steps:

   1. Under **Encryption key type**, choose **AWS Key Management Service key \(SSE\-KMS\)**\.
**Important**  
If you use the AWS KMS option for your default encryption configuration, you are subject to the RPS \(requests per second\) limits of AWS KMS\. For more information about AWS KMS quotas and how to request a quota increase, see [Quotas](https://docs.aws.amazon.com/kms/latest/developerguide/limits.html)\. 

   1. Under **AWS KMS key** choose one of the following:
      + **AWS managed key \(aws/s3\)**
      + **Choose from your KMS master keys**, and choose your **KMS master key**\.
      + **Enter KMS master key ARN**, and enter your AWS KMS key ARN\.
**Important**  
You can only use KMS CMKs that are enabled in the same AWS Region as the bucket\. When you choose **Choose from your KMS master keys**, the S3 console only lists 100 KMS CMKs per Region\. If you have more than 100 CMKs in the same Region, you can only see the first 100 CMKs in the S3 console\. To use a KMS CMK that is not listed in the console, choose **Custom KMS ARN**, and enter the KMS CMK ARN\.  
When you use an AWS KMS CMK for server\-side encryption in Amazon S3, you must choose a symmetric CMK\. Amazon S3 only supports symmetric CMKs and not asymmetric CMKs\. For more information, see [Using symmetric and asymmetric keys](https://docs.aws.amazon.com/kms/latest/developerguide/symmetric-asymmetric.html) in the *AWS Key Management Service Developer Guide*\.

      For more information about creating an AWS KMS CMK, see [Creating Keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\. For more information about using AWS KMS with Amazon S3, see [Protecting Data with Keys Stored in AWS KMS](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingKMSEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. To use an S3 Bucket Key for your bucket, under **Bucket Key**, choose **Enable**\.

   When you configure your bucket to use default encryption with SSE\-KMS, you can also enable an S3 Bucket Key for your bucket\. S3 Bucket Keys decrease request traffic from Amazon S3 to AWS KMS and lower the cost of encryption\. For more information, see [Reducing the cost of AWS KMS server side encryption with Amazon S3 Bucket Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-key.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. Choose **Save changes**\.

## More info<a name="default-bucket-encryption-moreinfo"></a>
+ [Amazon S3 Default Encryption for S3 Buckets](https://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html) in the *Amazon Simple Storage Service Developer Guide*
+ [How do I add encryption to an S3 object?](add-object-encryption.md)