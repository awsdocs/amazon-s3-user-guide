# How do I lock an Amazon S3 object?<a name="object-lock"></a>

With S3 Object Lock, you can store objects in Amazon S3 using a *write\-once\-read\-many* \(WORM\) model\. You can use S3 Object Lock to prevent an object from being deleted or overwritten for a fixed amount of time or indefinitely\. For information about object locking using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Locking Objects Using Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) in the *Amazon Simple Storage Service Developer Guide*\.

Before you lock any objects, you have to enable a bucket to use S3 Object Lock\. You enable Object Lock when you create a bucket\. After you enable Object Lock on a bucket, you can lock objects in that bucket\. When you create a bucket with Object Lock enabled, you can't disable Object Lock or suspend versioning for that bucket\. 

For information about creating a bucket with S3 Object Lock enabled, see [How do I create an S3 Bucket?](create-bucket.md)\.

**To lock an Amazon S3 object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want\.

1. In the **Objects** list, choose the name of the object that you want to lock\.

1. Choose **Properties**\.

1. Choose **Object Lock**\. 

1. Choose a retention mode\. You can change the **Retain until date**\. You can also choose to enable a **Legal hold**\. For more information, see [S3 Object Lock Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. Choose **Save**\.

## More info<a name="object-lock-moreinfo"></a>
+  [Setting bucket and object access permissions](set-permissions.md)