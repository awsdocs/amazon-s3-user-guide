# How do I edit public access settings for S3 buckets?<a name="block-public-access-bucket"></a>

Amazon S3 Block Public Access prevents the application of any settings that allow public access to data within S3 buckets\. This section describes how to edit Block Public Access settings for one or more S3 buckets\. For information about blocking public access using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Topics**
+ [Editing public access settings for an S3 bucket](#block-public-access-bucket-one)
+ [Editing public access settings for multiple S3 buckets](#block-public-access-bucket-multiple)
+ [More info](#block-public-access-bucket-moreinfo)

## Editing public access settings for an S3 bucket<a name="block-public-access-bucket-one"></a>

Follow these steps if you need to change the public access settings for a single S3 bucket\.

**To edit the Amazon S3 block public access settings for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Console screenshot showing the chosen bucket in the bucket name list.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Permissions**\.

1. Choose **Edit** to change the public access settings for the bucket\. For more information about the four Amazon S3 Block Public Access Settings, see [Block Public Access Settings](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html#access-control-block-public-access-options) in the Amazon Simple Storage Service Developer Guide\.  
![\[Console screenshot showing the edit link in the upper right corner.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/public-access-bucket-edit.png)

1. Choose the setting that you want to change, and then choose **Save**\.

1. When you're asked for confirmation, enter **confirm**\. Then choose **Confirm** to save your changes\.

## Editing public access settings for multiple S3 buckets<a name="block-public-access-bucket-multiple"></a>

Follow these steps if you need to change the public access settings for more than one S3 bucket\.

**To edit the Amazon S3 block public access settings for multiple S3 buckets**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the buckets that you want, and then choose **Edit public access settings**\.  
![\[Console screenshot showing multiple buckets selected and the edit public access settings button.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-edit-public-access-2.png)

1. Choose the setting that you want to change, and then choose **Save**\.   
![\[Console screenshot showing the public access settings for multiple buckets.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/edit-public-access-multiple.png)

1. When you're asked for confirmation, enter **confirm**\. Then choose **Confirm** to save your changes\.

You can change Amazon S3 Block Public Access settings when you create a bucket\. For more information, see [How do I create an S3 Bucket?](create-bucket.md)\. 

## More info<a name="block-public-access-bucket-moreinfo"></a>
+ [How do I block public access to S3 buckets?](block-public-access.md)
+ [How do I edit public access settings for all the S3 buckets in an AWS account?](block-public-access-account.md)
+  [Setting bucket and object access permissions](set-permissions.md)