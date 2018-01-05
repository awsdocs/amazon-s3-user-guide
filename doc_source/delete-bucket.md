# How Do I Delete an S3 Bucket?<a name="delete-bucket"></a>

You can delete a bucket and all of the objects contained in the bucket\. You can also delete an empty bucket\. When you delete a bucket with versioning enabled, all versions of all the objects in the bucket are deleted\. For more information, see [Managing Objects in a Versioning\-Enabled Bucket](http://docs.aws.amazon.com/AmazonS3/latest/dev/manage-objects-versioned-bucket.html) and [Deleting/Emptying a Bucket](http://docs.aws.amazon.com/AmazonS3/latest/dev/delete-or-empty-bucket.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Important**  
If you want to continue to use the same bucket name, don't delete the bucket\. We recommend that you empty the bucket and keep it\. After a bucket is deleted, the name becomes available to reuse, but the name might not be available for you to reuse for various reasons\. For example, it might take some time before the name can be reused and some other account could create a bucket with that name before you do\.

**To delete an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the bucket icon next to the name of the bucket that you want to delete and then choose **Delete bucket**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/delete-bucket.png)

1. In the **Delete bucket** dialog box, type the name of the bucket that you want to delete for confirmation and then choose **Confirm**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/delete-bucket-confirm.png)