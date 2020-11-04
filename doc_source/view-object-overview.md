# How do I see an overview of an object?<a name="view-object-overview"></a>

This section explains how to use the Amazon S3 console to view the object overview panel\. This panel provides an overview of all the essential information for an object in one place\.

**To see the overview panel for an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the object\.

1. In the **Name** list, select the name of the object for which you want an overview\.

1. To download the object, choose **Download** in the object overview panel\. To copy the path of the object to the clipboard, choose **Copy Path**\.

1. If versioning is enabled on the bucket, choose **Latest versions** to list the versions of the object\. You can then choose the download icon to download an object version, or choose the trash can icon to delete an object version\. 
**Important**  
You can undelete an object only if it was deleted as the latest \(current\) version\. You can't undelete a previous version of an object that was deleted\. For more information, see [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

## More info<a name="view-object-overview-related-topics"></a>
+  [How do I see the versions of an S3 object?](view-object-versions.md)