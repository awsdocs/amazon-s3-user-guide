# How Do I Undelete a Deleted S3 Object?<a name="undelete-objects"></a>

This section explains how to use the Amazon S3 console to recover \(undelete\) deleted objects\.

To be able to undelete a deleted object, you must have had versioning enabled on the bucket that contains the object before the object was deleted\. For information about enabling versioning, see [How Do I Enable or Suspend Versioning for an S3 Bucket?](enable-versioning.md)\.

When you delete an object in a versioning\-enabled bucket, all versions remain in the bucket and Amazon S3 creates a delete marker for the object\. To undelete the object, you must delete this delete marker\. For more information about versioning and delete markers, see [Object Versioning](http://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To recover deleted objects from an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. To see a list of the versions of the objects in the bucket, choose **Show**\. You'll be able to see the delete markers for deleted objects\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-show-versions.png)

1. To undelete an object, you must delete the delete marker\. Select the check box next to the delete marker of the object to recover, and then choose **delete** from the **More** menu\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/select-delete-marker.png)

1. Choose **Hide**, you'll see the undeleted object listed\.

## More Info<a name="undelete-objects-related-topics"></a>

+  [How Do I See the Versions of an S3 Object?](view-object-versions.md)

+  [How Do I Enable or Suspend Versioning for an S3 Bucket?](enable-versioning.md)

+  [Using Versioning](http://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*