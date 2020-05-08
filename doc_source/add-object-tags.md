# How do I add tags to an S3 object?<a name="add-object-tags"></a>

Object tagging gives you a way to categorize storage\. This topic explains how to use the console to add tags to an S3 object after the object has been uploaded\. For information about adding tags to an object when the object is being uploaded, see [How do I upload files and folders to an S3 bucket?](upload-objects.md)\. 

Each tag is a key\-value pair that adheres to the following rules:
+ You can associate up to 10 tags with an object\. Tags associated with an object must have unique tag keys\.
+ A tag key can be up to 128 Unicode characters in length and tag values can be up to 255 Unicode characters in length\.
+ Key and tag values are case sensitive\. 

 For more information about object tags, see [Object Tagging](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To add tags to an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the object\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, choose the name of the object you want to add tags to\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-name-select.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-properties-tab.png)

1. Choose **Tags** and then choose **Add Tag**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-tags.png)

1. Each tag is a key\-value pair\. Type a **Key** and a **Value**\. Then choose **Add Tag** to add another tag or choose **Save**\. 

   You can enter up to 10 tags for an object\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/enter-object-tags.png)

## More info<a name="add-object-tags-moreinfo"></a>
+  [How do I view the properties of an object?](view-object-properties.md)
+  [Uploading, downloading, and managing objects](upload-download-objects.md)