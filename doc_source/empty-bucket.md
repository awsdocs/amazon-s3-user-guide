# How Do I Empty an S3 Bucket?<a name="empty-bucket"></a>

You can empty a bucket, which deletes all of the objects in the bucket without deleting the bucket\. When you empty a bucket with versioning enabled, all versions of all the objects in the bucket are deleted\. For more information, see [Managing Objects in a Versioning\-Enabled Bucket](http://docs.aws.amazon.com/AmazonS3/latest/dev/manage-objects-versioned-bucket.html) and [Deleting/Emptying a Bucket](http://docs.aws.amazon.com/AmazonS3/latest/dev/delete-or-empty-bucket.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To empty an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the bucket icon next to the name of the bucket that you want to delete and then choose **Empty bucket**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/empty-bucket.png)

1. In the **Empty bucket** dialog box, type the name of the bucket you want to empty for confirmation and then choose **Confirm**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/empty-bucket-confirm.png)