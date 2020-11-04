# How do I edit public access settings for S3 buckets?<a name="block-public-access-bucket"></a>

Amazon S3 Block Public Access prevents the application of any settings that allow public access to data within S3 buckets\. This section describes how to edit Block Public Access settings for one or more S3 buckets\. For information about blocking public access using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Topics**
+ [Editing public access settings for an S3 bucket](#block-public-access-bucket-one)
+ [More info](#block-public-access-bucket-moreinfo)

## Editing public access settings for an S3 bucket<a name="block-public-access-bucket-one"></a>

Follow these steps if you need to change the public access settings for a single S3 bucket\.

**To edit the Amazon S3 block public access settings for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want\.

1. Choose **Permissions**\.

1. Choose **Edit** to change the public access settings for the bucket\. For more information about the four Amazon S3 Block Public Access Settings, see [Block Public Access Settings](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html#access-control-block-public-access-options) in the Amazon Simple Storage Service Developer Guide\.

1. Choose the setting that you want to change, and then choose **Save changes**\.

1. When you're asked for confirmation, enter **confirm**\. Then choose **Confirm** to save your changes\.

You can change Amazon S3 Block Public Access settings when you create a bucket\. For more information, see [How do I create an S3 Bucket?](create-bucket.md)\. 

## More info<a name="block-public-access-bucket-moreinfo"></a>
+ [How do I block public access to S3 buckets?](block-public-access.md)
+ [How do I edit public access settings for all the S3 buckets in an AWS account?](block-public-access-account.md)
+  [Setting bucket and object access permissions](set-permissions.md)