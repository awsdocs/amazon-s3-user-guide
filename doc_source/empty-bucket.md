# How do I empty an S3 Bucket?<a name="empty-bucket"></a>

You can empty a bucket, which deletes all of the objects in the bucket without deleting the bucket\. When you empty a bucket with versioning enabled, all versions of all the objects in the bucket are deleted\. For more information, see [Managing Objects in a Versioning\-Enabled Bucket](https://docs.aws.amazon.com/AmazonS3/latest/dev/manage-objects-versioned-bucket.html) and [Deleting/Emptying a Bucket](https://docs.aws.amazon.com/AmazonS3/latest/dev/delete-or-empty-bucket.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To empty an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, select the option next to the name of the bucket that you want to empty and then choose **Empty**\.

1. On the **Empty bucket** page, confirm that you want to empty the bucket by entering the bucket name into the text field, and then choose **Empty**\.

1. \(Optional\) Monitor the progress of the bucket emptying process on the **Empty bucket: Status** page\.