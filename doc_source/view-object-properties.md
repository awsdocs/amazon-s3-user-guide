# How do I view the properties of an object?<a name="view-object-properties"></a>

This section explains how to use the console to view the properties of an object\.

**To view the properties of an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the object\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, choose the name of the object you want to view the properties for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-name-select.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-properties-tab.png)

1. On the **Properties** page, you can configure the following properties for the object\.
**Note**  
If you change the properties; **Storage Class**, ** Enryption**, **Metadata**, a new object is created to replace the old one\. If S3 Versioning is enabled, a new version of the object is created, and the existing object becomes an older version\. The role that changes the property also becomes the owner of the new object or \(object version\)\.

   1. **Storage class** – Each object in Amazon S3 has a storage class associated with it\. The storage class that you choose to use depends on how frequently you access the object\. The default storage class for S3 objects is STANDARD\. You choose which storage class to use when you upload an object\. For more information about storage classes, see [Storage Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html) in the *Amazon Simple Storage Service Developer Guide*\.

      To change the storage class after you upload an object, choose **Storage class**\. Choose the storage class that you want, and then choose **Save**\.

   1. **Encryption** – You can encrypt your S3 objects\. For more information, see [How do I add encryption to an S3 object?](add-object-encryption.md)\. 

   1. **Metadata** – Each object in Amazon S3 has a set of name\-value pairs that represents its metadata\. For information on adding metadata to an S3 object, see [How do I add metadata to an S3 object?](add-object-metadata.md)\.

   1. **Tags** – You can add tags to an S3 object\. For more information, see [How do I add tags to an S3 object?](add-object-tags.md)\.