# Uploading, Downloading, and Managing Objects<a name="upload-download-objects"></a>

Amazon S3 is cloud storage for the Internet\. To upload your data \(photos, videos, documents etc\.\), you first create a bucket in one of the AWS Regions\. You can then upload an unlimited number of data objects to the bucket\.

The data that you store in Amazon S3 consists of objects\. Every object resides within a bucket that you create in a specific AWS Region\. Every object that you store in Amazon S3 resides in a bucket\. 

Objects stored in a region never leave the region unless you explicitly transfer them to another region\. For example, objects stored in the EU \(Ireland\) region never leave it\. The objects stored in an AWS region physically remain in that region\. Amazon S3 does not keep copies of objects or move them to any other region\. However, you can access the objects from anywhere, as long as you have necessary permissions to do so\.

Before you can upload an object into Amazon S3, you must have write permissions to a bucket\.

Objects can be any file type: images, backups, data, movies, etc\. The maximum size of file you can upload by using the Amazon S3 console is 78GB\.  You can have an unlimited number of objects in a bucket\.

The following topics explain how to use the Amazon S3 console to upload, delete, and manage objects\.

