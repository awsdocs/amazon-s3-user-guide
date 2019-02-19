# How Do I Lock an S3 Object?<a name="object-lock"></a>

Amazon S3 object lock enables you to store objects using a "Write Once Read Many" \(WORM\) model\. When using object lock you can prevent an object from being deleted or overwritten for a fixed amount of time or indefinitely\. For information about object locking using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Introduction to Amazon S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-object-lock.html) in the *Amazon Simple Storage Service Developer Guide*\.

Before you lock any objects, you have to enable a bucket to use Amazon S3 object lock\. You enable object lock when you create a bucket\. Once you enable object lock on a bucket you can lock objects in that bucket\. Once you create a bucket with object lock enabled, you can't disable object lock or suspend versioning for the bucket\. For information on creating a bucket with object lock enabled, see [How Do I Create an S3 Bucket?](create-bucket.md)\.

**To lock an S3 object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Console screenshot showing the chosen bucket in the bucket name list.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, choose the name of the object you want to lock\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-name-select.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-properties.png)

1. Choose **Object Lock**\.   
![\[Console screenshot object lock property box.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-lock-box.png)

1. Choose a retention mode\. You can change the **Retain until date**\. You can also choose to enable a legal hold\. For more information about retention modes and a legal hold, see [Amazon S3 Object Lock Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html) in the *Amazon Simple Storage Service Developer Guide*  
![\[Console screenshot enable object lock dialog.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/enable-lock-on-object.png)

1. Choose **Save**\.

## More Info<a name="object-lock-moreinfo"></a>
+  [Setting Bucket and Object Access Permissions](set-permissions.md)