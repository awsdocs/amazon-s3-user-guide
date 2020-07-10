# Uploading, downloading, and managing objects<a name="upload-download-objects"></a>

To upload your data \(photos, videos, documents etc\.\) to Amazon S3, you must first create an S3 bucket in one of the AWS Regions\. You can then upload an unlimited number of data objects to the bucket\.

The data that you store in Amazon S3 consists of objects\. Every object resides within a bucket that you create in a specific AWS Region\. Every object that you store in Amazon S3 resides in a bucket\. 

Objects stored in a region never leave the region unless you explicitly transfer them to another region\. For example, objects stored in the Europe \(Ireland\) region never leave it\. The objects stored in an AWS region physically remain in that region\. Amazon S3 does not keep copies of objects or move them to any other region\. However, you can access the objects from anywhere, as long as you have necessary permissions to do so\.

Before you can upload an object into Amazon S3, you must have write permissions to a bucket\.

Objects can be any file type: images, backups, data, movies, etc\. You can have an unlimited number of objects in a bucket\. The maximum size of file you can upload by using the Amazon S3 console is 160 GB\. To upload a file larger than 160 GB, use the AWS CLI, AWS SDK, or Amazon S3 REST API\. For more information, see [Uploading Objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/UploadingObjects.html) in the *Amazon Simple Storage Service Developer Guide*\.

The following topics explain how to use the Amazon S3 console to upload, delete, and manage objects\.

**Note**  
If you rename an object, or change any of the properties; **Storage Class**, ** Enryption**, **Metadata**, a new object is created to replace the old one\. If S3 Versioning is enabled, a new version of the object is created, and the existing object becomes an older version\. The role that changes the property also becomes the owner of the new object or \(object version\)\.

**Topics**
+ [Uploading S3 objects](upload-objects.md)
+ [Copying an object](copy-object.md)
+ [Moving an object](move-object.md)
+ [Downloading S3 objects](download-objects.md)
+ [Deleting objects](delete-objects.md)
+ [Undeleting objects](undelete-objects.md)
+ [Restoring archived S3 objects](restore-archived-objects.md)
+ [Locking Amazon S3 objects](object-lock.md)
+ [Viewing an overview of an object](view-object-overview.md)
+ [Viewing object versions](view-object-versions.md)
+ [Viewing object properties](view-object-properties.md)
+ [Adding encryption to an object](add-object-encryption.md)
+ [Adding metadata to an object](add-object-metadata.md)
+ [Adding tags to an object](add-object-tags.md)
+ [Using folders](using-folders.md)