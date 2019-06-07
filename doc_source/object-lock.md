# How Do I Lock an Amazon S3 Object?<a name="object-lock"></a>

With Amazon S3 object lock, you can store objects in Amazon S3 using a *write\-once\-read\-many* \(WORM\) model\. You can use Amazon S3 object lock to prevent an object from being deleted or overwritten for a fixed amount of time or indefinitely\. For information about object locking using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Locking Objects Using Amazon S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html) in the *Amazon Simple Storage Service Developer Guide*\.

Before you lock any objects, you have to enable a bucket to use Amazon S3 object lock\. You enable object lock when you create a bucket\. After you enable Amazon S3 object lock on a bucket, you can lock objects in that bucket\. When you create a bucket with object lock enabled, you can't disable object lock or suspend versioning for that bucket\. 

For information about creating a bucket with Amazon S3 object lock enabled, see [How Do I Create an S3 Bucket?](create-bucket.md)\.

**To lock an Amazon S3 object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Console screenshot showing the chosen bucket in the bucket name list.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, choose the name of the object that you want to lock\.  
![\[Console screenshot showing the chosen object in the name list.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-name-select.png)

1. Choose **Properties**\.  
![\[Console screenshot showing the properties tab.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-properties.png)

1. Choose **Object lock**\.   
![\[Console screenshot showing the object lock property box.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-lock-box.png)

1. Choose a retention mode\. You can change the **Retain until date**\. You can also choose to enable a legal hold\. For more information, see [Amazon S3 Object Lock Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Console screenshot showing the object lock dialog box.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/enable-lock-on-object.png)

1. Choose **Save**\.

## More Info<a name="object-lock-moreinfo"></a>
+  [Setting Bucket and Object Access Permissions](set-permissions.md)