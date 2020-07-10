# How do I enable or suspend versioning for an S3 bucket?<a name="enable-versioning"></a>

Versioning enables you to keep multiple versions of an object in one bucket\. This section describes how to enable object versioning on a bucket\. For more information about versioning support in Amazon S3, see [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To enable or disable versioning on an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to enable versioning for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Choose **Versioning**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-versioning.png)

1. Choose **Enable versioning** or **Suspend versioning**, and then choose **Save**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/enable-or-disable-versioning.png)

**Note**  
You can use AWS Multi\-Factor Authentication \(MFA\) with versioning\. When you use MFA with versioning, you must provide your AWS account’s access keys and a valid code from the account’s MFA device in order to permanently delete an object version or suspend or reactivate versioning\. To use MFA with versioning, you enable `MFA Delete`\. However, you cannot enable `MFA Delete` using the AWS Management Console\. You must use the AWS CLI or API\. For more information, see [MFA Delete](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html#MultiFactorAuthenticationDelete)\.