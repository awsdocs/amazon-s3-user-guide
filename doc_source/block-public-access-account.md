# How Do I Edit Public Access Settings for All the S3 Buckets in an AWS Account?<a name="block-public-access-account"></a>

Amazon S3 block public access prevents the application of any settings that allow public access to data within S3 buckets\. This section describes how to edit block public access settings for all the S3 buckets in your AWS account\. For information about blocking public using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To edit block public access settings for all the S3 buckets in an AWS account**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Choose **Public access settings for this account**\.  
![\[Console screenshot showing the public access settings located under buckets.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-public-access-account.png)

1. Choose **Edit** to change the block public access settings for all the buckets in your AWS account\.  
![\[Console screenshot showing the edit link in upper right corner.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/block-public-access-account-edit.png)

1. Choose the settings you want to change, and then choose **Save**\. For details about each setting, pause on the **i** icons\.   
![\[Console screenshot showing the information icons next to each public access setting.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/block-public-access-account-edit-2.png)

   Before you save your changes, you can choose **Refresh** to restore the settings to what they were before you started making changes\. 

1. When you're asked for confirmation, enter **confirm**\. Then choose **Confirm** to save your changes\.

## More Info<a name="block-public-access-account-moreinfo"></a>
+ [How Do I Block Public Access to S3 Buckets?](block-public-access.md)
+ [How Do I Edit Public Access Settings for S3 Buckets?](block-public-access-bucket.md)
+ [Setting Bucket and Object Access Permissions](set-permissions.md)