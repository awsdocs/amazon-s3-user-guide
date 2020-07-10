# How do I add metadata to an S3 object?<a name="add-object-metadata"></a>

Each object in Amazon Simple Storage Service \(Amazon S3\) has a set of name\-value pairs that provides metadata about the object\. *Metadata* is additional information about the object\. Some metadata is set by Amazon S3 when you upload the object, for example,`Date` and `Content-Length`\. You can also set some metadata when you upload the object, or you can add it later\. This section explains how to use the Amazon S3 console to add metadata to an S3 object\.

Object metadata is a set of name\-value \(key\-value\) pairs\. For example, the metadata for content length, `Content-Length`, is the name \(key\) and the size of the object in bytes \(value\)\. For more information about object metadata, see [Object Metadata](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#object-metadata) in the *Amazon Simple Storage Service Developer Guide*\.

There are two kinds of metadata for an S3 object, Amazon S3 system metadata and user\-defined metadata:
+ **System metadata**–There are two categories of system metadata\. Metadata such as the `Last-Modified` date is controlled by the system\. Only Amazon S3 can modify the value\. There is also system metadata that you control, for example, the storage class configured for the object\. 
+ **User\-defined metadata**–You can define your own custom metadata, called user\-defined metadata\. You can assign user\-defined metadata to an object when you upload the object or after the object has been uploaded\. User\-defined metadata is stored with the object and is returned when you download the object\. Amazon S3 does not process user\-defined metadata\. 

The following topics describe how to add metadata to an object using the Amazon S3 console\.

**Note**  
If you change an object's metadata, a new object will be created and will replace the old one\. If S3 Versioning is enabled, a new version of the object is created, and the existing object becomes an older version\. The role that changes the property also becomes the owner of the new object or \(object version\)\.

**Topics**
+ [Adding system\-defined metadata](#add-object-metadata-system)
+ [Adding user\-defined metadata](#add-object-metadata-user-defined)

## Adding system\-defined metadata to an S3 object<a name="add-object-metadata-system"></a>

You can configure some system metadata for an S3 object\. For a list of system\-defined metadata and whether you can modify their values, see [System\-Defined Metadata](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#SysMetadata) in the *Amazon Simple Storage Service Developer Guide*\.

**To add system metadata to an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the object\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, choose the name of the object that you want to add metadata to\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-name-select.png)

1. Choose **Properties**, and then choose **Metadata**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-properties-tab.png)

1. Choose **Add Metadata**, and then choose a key from the **Select a key** menu\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-metadata.png)

1. Depending on which key you chose, choose a value from the **Select a value** menu or type a value\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-metadata-value.png)

1. Choose **Save**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-metadata-save.png)

## Adding user\-defined metadata to an S3 object<a name="add-object-metadata-user-defined"></a>

You can assign user\-defined metadata to an object\. User\-defined metadata must begin with the prefix "`x-amz-meta-`", otherwise Amazon S3 will not set the key value pair as you define it\. You define custom metadata by adding a name that you choose to the `x-amz-meta-` key\. This creates a custom key\. For example, if you add the custom name `alt-name`, the metadata key would be `x-amz-meta-alt-name`\. 

User\-defined metadata can be as large as 2 KB\. Both keys and their values must conform to US\-ASCII standards\. For more information, see [User\-Defined Metadata](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#UserMetadata) in the *Amazon Simple Storage Service Developer Guide*\.

**To add user\-defined metadata to an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the object\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, choose the name of the object that you want to add metadata to\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-name-select.png)

1. Choose **Properties**, and then choose **Metadata**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-properties-tab.png)

1. Choose **Add Metadata**, and then choose the `x-amz-meta-` key from the **Select a key** menu\. Any metadata starting with the prefix `x-amz-meta-` is user\-defined metadata\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-metadata-user-defined.png)

1. Type a custom name following the `x-amz-meta-` key\. For example, for the custom name `alt-name`, the metadata key would be `x-amz-meta-alt-name`\. Enter a value for the custom key, and then choose **Save**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/add-metadata-user-defined-value.png)

### <a name="add-object-metadata-user-defined-moreinfo"></a>
+  [How do I view the properties of an object?](view-object-properties.md)
+  [Uploading, downloading, and managing objects](upload-download-objects.md)