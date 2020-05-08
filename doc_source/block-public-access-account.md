# How do I edit public access settings for all the S3 buckets in an AWS account?<a name="block-public-access-account"></a>

Amazon S3 block public access prevents the application of any settings that allow public access to data within S3 buckets\. This section describes how to edit block public access settings for all the S3 buckets in your AWS account\. For information about blocking public using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To edit block public access settings for all the S3 buckets in an AWS account**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Choose **Block public access \(account settings\)**\.  
![\[Console screenshot showing the public access settings located under buckets.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-public-access-account.png)

1. Choose **Edit** to change the block public access settings for all the buckets in your AWS account\.  
![\[Console screenshot showing the edit link in upper right corner.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/block-public-access-account-edit.png)

1. Choose the settings that you want to change, and then choose **Save**\.

1. When you're asked for confirmation, enter **confirm**\. Then choose **Confirm** to save your changes\.

## More info<a name="block-public-access-account-moreinfo"></a>
+ [How do I block public access to S3 buckets?](block-public-access.md)
+ [How do I edit public access settings for S3 buckets?](block-public-access-bucket.md)
+ [Setting bucket and object access permissions](set-permissions.md)