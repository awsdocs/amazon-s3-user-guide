# Uploading, Downloading, and Managing Objects<a name="upload-download-objects"></a>

Amazon S3 is cloud storage for the Internet\. To upload your data \(photos, videos, documents etc\.\), you first create a bucket in one of the AWS Regions\. You can then upload an unlimited number of data objects to the bucket\.

The data that you store in Amazon S3 consists of objects\. Every object resides within a bucket that you create in a specific AWS Region\. Every object that you store in Amazon S3 resides in a bucket\. 

Objects stored in a region never leave the region unless you explicitly transfer them to another region\. For example, objects stored in the EU \(Ireland\) region never leave it\. The objects stored in an AWS region physically remain in that region\. Amazon S3 does not keep copies of objects or move them to any other region\. However, you can access the objects from anywhere, as long as you have necessary permissions to do so\.

Before you can upload an object into Amazon S3, you must have write permissions to a bucket\.

Objects can be any file type: images, backups, data, movies, etc\. You can have an unlimited number of objects in a bucket\. The maximum size of file you can upload by using the Amazon S3 console is 80 GB\. To upload a file larger than 80 GB, use the AWS CLI, AWS SDK, or Amazon S3 REST API\. For more information, see [Uploading Objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/UploadingObjects.html) in the *Amazon Simple Storage Service Developer Guide*\. 

The following topics explain how to use the Amazon S3 console to upload, delete, and manage objects\.

**Topics**
+ [Uploading S3 Objects](upload-objects.md)
+ [Downloading S3 Objects](download-objects.md)
+ [Deleting Objects](delete-objects.md)
+ [Undeleting Objects](undelete-objects.md)
+ [Restoring Archived S3 Objects](restore-archived-objects.md)
+ [Locking S3 Objects](object-lock.md)
+ [Viewing an Overview of an Object](view-object-overview.md)
+ [Viewing Object Versions](view-object-versions.md)
+ [Viewing Object Properties](view-object-properties.md)
+ [Adding Encryption to an Object](add-object-encryption.md)
+ [Adding Metadata to an Object](add-object-metadata.md)
+ [Adding Tags to an Object](add-object-tags.md)
+ [Using Folders](using-folders.md)