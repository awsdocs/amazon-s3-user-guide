# Editing object metadata<a name="add-object-metadata"></a>

This section explains how to use the Amazon S3 console to edit metadata of existing S3 objects\. Each object in Amazon S3 can have a set of key\-value pairs that provides *metadata*, which is additional information about the object\. Some metadata is set by Amazon S3 when you upload the object\. For example, `Content-Length` is the *key* \(name\) and the *value* is the size of the object in bytes\. 

You can also set some metadata when you upload the object and later edit it as your needs change\. For example, you may have a set of objects that you initially store in the `STANDARD` storage class\. Over time you may no longer need this data to be highly available and change the storage class to `GLACIER` by editing the value of the `x-amz-storage-class` key from `STANDARD` to `GLACIER`\.

There are two kinds of metadata for an S3 object, Amazon S3 *system\-defined* metadata and *user\-defined *metadata:
+ **System\-defined metadata**–Within system metadata, there are two categories\. 
  + Metadata such as the `Last-Modified` date is controlled by the system and only Amazon S3 can modify the value\.
  + There is also system metadata that you can modify, for example, the storage class for the object or the encryption type\.
+ **User\-defined metadata**–You can define your own custom metadata, called user\-defined metadata, that you assign to an object when you upload the object or after the object has been uploaded\. User\-defined metadata is stored with the object and is returned when you download the object\. Amazon S3 does not process user\-defined metadata\. 

The following topics describe how to edit metadata of an object using the Amazon S3 console\.

**Topics**
+ [Editing system\-defined metadata](#add-object-metadata-system)
+ [Editing user\-defined metadata](#add-object-metadata-user-defined)

**Note**  
This action creates a *copy* of the object with updated settings and the last\-modified date\. If S3 Versioning is enabled, a new version of the object is created, and the existing object becomes an older version\. The IAM role that changes the property also becomes the owner of the new object or \(object version\)\.
Editing metadata updates values for existing key names\.
Objects encrypted with customer\-provided encryption keys \(SSE\-C\) cannot be copied using the console and must use the AWS CLI, AWS SDK, or the Amazon S3 REST API,

**Warning**  
When editing metadata of folders, wait for the Edit metadata operation to finish before adding new objects to the folder\. Otherwise, new objects might be edited as well\.
Objects encrypted with customer\-provided encryption keys \(SSE\-C\) cannot be copied using the console and must use the AWS CLI, AWS SDK, or the Amazon S3 REST API,

For more information about object metadata including naming guidelines and limits, see [Object Metadata](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#object-metadata) in the *Amazon Simple Storage Service Developer Guide*\.

## Editing system\-defined metadata<a name="add-object-metadata-system"></a>

You can configure some, but not all, system metadata for an S3 object\. For a list of system\-defined metadata and whether you can modify their values, see [System\-Defined Metadata](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#SysMetadata) in the *Amazon Simple Storage Service Developer Guide*\.

**To edit system\-defined metadata of an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects with metadata that you want to edit\.

   You can also optionally navigate to a folder\.

1. In the **Objects** list, select the checkbox beside the object names\.

1. In the **Actions** menu, choose **Edit metadata**\.

1. Review the objects listed, and choose **Add metadata**\.

1. For metadata **Type**, choose **System\-defined**\.

1. Specify a unique **Key** and the metadata **Value**\.

1. To edit additional metadata, choose **Add metadata**\. You can also choose **Remove** to remove a set of Type\-Key\-Values\.

1. Choose **Save changes**\.

   Amazon S3 edits the metadata of the specified objects\.

## Editing user\-defined metadata<a name="add-object-metadata-user-defined"></a>

You can edit user\-defined metadata of an object by combining the metadata prefix, `x-amz-meta-`, and a name you choose to create a custom key\. For example, if you add the custom name `alt-name`, the metadata key would be `x-amz-meta-alt-name`\. User\-defined metadata can be as large as 2 KB total\. To calculate the total size of user\-defined metadata, sum the number of bytes in the UTF\-8 encoding for each key and value\. Both keys and their values must conform to US\-ASCII standards\. For more information, see [User\-Defined Metadata](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#UserMetadata) in the *Amazon Simple Storage Service Developer Guide*\.

**To edit user\-defined metadata of an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket with objects that you want to add metadata to\.

   You can also optionally navigate to a folder\.

1. In the **Objects** list, select the check box next to the names of the objects that you want to add metadata to\.

1. In the **Actions** menu, choose **Edit metadata**\.

1. Review the objects listed, and choose **Add metadata**\.

1. For metadata **Type**, choose **User\-defined**\.

1. Enter a unique, custom **Key** following `x-amz-meta-`\. Also enter a metadata **Value**\.

1. To add additional metadata, choose **Add metadata**\. You can also choose **Remove** to remove a set of Type\-Key\-Values\. 

1. Choose **Save changes**\.

   Amazon S3 edits the metadata of the specified objects\.

### More info<a name="add-object-metadata-user-defined-moreinfo"></a>
+  [How do I view the properties of an object?](view-object-properties.md)
+  [Uploading, downloading, and managing objects](upload-download-objects.md)