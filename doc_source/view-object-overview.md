# How Do I See an Overview of an Object?<a name="view-object-overview"></a>

This section explains how to use the Amazon S3 console to view the object overview panel\. This panel provides an overview of all the essential information for an object in one place\.

**To see the overview panel for an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the object\.  
![\[Bucket name list with a bucket selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, select the check box next to the name of the object for which you want an overview\.  
![\[Object name selected in the list and overview panel with object details and a
            download button.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/download-select-box.png)

1. To download the object, choose **Download** in the object overview panel\. To copy the path of the object to the clipboard, choose **Copy Path**\.  
![\[Object overview panel with Download and Copy path buttons.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-overview.png)

1. If versioning is enabled on the bucket, choose **Latest versions** to list the versions of the object\. You can then choose the download icon to download an object version, or choose the trash can icon to delete an object version\.   
![\[List of object versions that you can download or delete.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-overview-versions.png)
**Important**  
You can undelete an object only if it was deleted as the latest \(current\) version\. You can't undelete a previous version of an object that was deleted\. For more information, see [Object Versioning](http://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](http://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

## More Info<a name="view-object-overview-related-topics"></a>

+  [How Do I See the Versions of an S3 Object?](view-object-versions.md)