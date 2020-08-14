# How do I undelete a deleted S3 object?<a name="undelete-objects"></a>

This section explains how to use the Amazon S3 console to recover \(undelete\) deleted objects\.

To be able to undelete a deleted object, you must have had versioning enabled on the bucket that contains the object before the object was deleted\. For information about enabling versioning, see [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)\.

When you delete an object in a versioning\-enabled bucket, all versions remain in the bucket and Amazon S3 creates a delete marker for the object\. To undelete the object, you must delete this delete marker\. For more information about versioning and delete markers, see [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To recover deleted objects from an S3 bucket**

The following steps describe how to recover deleted objects that are not folders from your S3 bucket including objects that are within those folders\. 

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.

1. To see a list of the **versions** of the objects in the bucket, select **Show**\. You'll be able to see the delete markers for deleted objects\. 

1. To undelete an object, you must delete the delete marker\. Select the check box next to the **delete marker** of the object to recover, and then choose **delete** from the **Actions** menu\.

1. Then, choose **Hide** and you'll see the undeleted object listed\.

**Note**  
You can't use the Amazon S3 console to undelete folders\. You must use the AWS CLI or SDK\. For examples, see [ How can I retrieve an Amazon S3 object that was deleted in a versioning\-enabled bucket?](http://aws.amazon.com/premiumsupport/knowledge-center/s3-undelete-configuration/) 

## More info<a name="undelete-objects-related-topics"></a>
+  [How do I see the versions of an S3 object?](view-object-versions.md)
+  [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)
+  [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*