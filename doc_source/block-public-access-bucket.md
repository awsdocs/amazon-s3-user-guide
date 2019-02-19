# How Do I Edit Public Access Settings for S3 Buckets?<a name="block-public-access-bucket"></a>

Amazon S3 block public access prevents the application of any settings that allow public access to data within S3 buckets\. This section describes how to edit block public access settings for one or more S3 buckets\. For information about blocking public access using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Topics**
+ [Editing Public Access Settings for an S3 Bucket](#block-public-access-bucket-one)
+ [Editing Public Access Settings for Multiple S3 Buckets](#block-public-access-bucket-multiple)
+ [More Info](#block-public-access-bucket-moreinfo)

## Editing Public Access Settings for an S3 Bucket<a name="block-public-access-bucket-one"></a>

Follow these steps if you need to change the public access settings for a single S3 bucket\.

**To edit the block public access settings for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Console screenshot showing the chosen bucket in the bucket name list.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Permissions**\.  
![\[Console screenshot showing the permissions tab and the public access settings button.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-public-access.png)

1. Choose **Edit** to change the public access settings for the bucket\.  
![\[Console screenshot showing the edit link in the upper right corner.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/public-access-bucket-edit.png)

1. Choose the setting that you want to change, and then choose **Save**\. For details about each setting, pause on the **i** icons\.   
![\[Console screenshot showing all the public access settings and the save button.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/public-access-bucket-edit-2.png)

   Before you save your changes, you can choose **Refresh** to restore the settings to what they were before you started making changes\. 

1. When you're asked for confirmation, enter **confirm**\. Then choose **Confirm** to save your changes\.

## Editing Public Access Settings for Multiple S3 Buckets<a name="block-public-access-bucket-multiple"></a>

Follow these steps if you need to change the public access settings for more than one S3 bucket\.

**To edit the block public access settings for multiple S3 buckets**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the buckets that you want, and then choose **Edit public access settings**\.  
![\[Console screenshot showing multiple buckets selected and the edit public access settings button.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-edit-public-access-2.png)

1. Choose the setting that you want to change, and then choose **Save**\. For details about each block public access setting, pause on the **i** icons\.   
![\[Console screenshot showing the public access settings for multiple buckets.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/edit-public-access-multiple.png)

1. When you're asked for confirmation, enter **confirm**\. Then choose **Confirm** to save your changes\.

You can change block public access settings when you create a bucket\. For more information, see [How Do I Create an S3 Bucket?](create-bucket.md)\. 

## More Info<a name="block-public-access-bucket-moreinfo"></a>
+ [How Do I Block Public Access to S3 Buckets?](block-public-access.md)
+ [How Do I Edit Public Access Settings for All the S3 Buckets in an AWS Account?](block-public-access-account.md)
+  [Setting Bucket and Object Access Permissions](set-permissions.md)