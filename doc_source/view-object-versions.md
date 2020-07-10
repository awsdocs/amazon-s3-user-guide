# How do I see the versions of an S3 object?<a name="view-object-versions"></a>

This section explains how to use the Amazon S3 console to see the different versions of an object\.

A versioning\-enabled bucket can have many versions of the same object:, one current \(latest\) version and zero or more noncurrent \(previous\) versions\. Amazon S3 assigns each object a unique version ID\. For information about enabling versioning, see [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)\. 

If a bucket is versioning\-enabled, Amazon S3 creates another version of an object under the following conditions: 
+ If you upload an object that has the same name as an object that already exists in the bucket, Amazon S3 creates another version of the object instead of replacing the existing object\. 
+ If you update any object properties after you upload the object to the bucket, such as changing the storage details or other metadata , Amazon S3 creates a new object version in the bucket\. 

For more information about versioning support in Amazon S3, see [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To see multiple versions of an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the object\.  
![\[Bucket name list with a bucket selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. To see a list of the versions of the objects in the bucket, choose **Show**\. For each object version, the console shows a unique version ID, the date and time the object version was created, and other properties\. \(Objects stored in your bucket before you set the versioning state have a version ID of **null**\.\)

    To list the objects without the versions, choose **Hide**\.  
![\[Hide and Show version buttons and list of object versions\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-show-versions-list.png)

You also can view, download, and delete object versions in the object overview panel\. For more information, see [How do I see an overview of an object?](view-object-overview.md)\.

**Important**  
You can undelete an object only if it was deleted as the latest \(current\) version\. You can't undelete a previous version of an object that was deleted\. For more information, see [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

## More info<a name="view-object-versions-related-topics"></a>
+  [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)
+ [How do I create a lifecycle policy for an S3 Bucket?](create-lifecycle.md)