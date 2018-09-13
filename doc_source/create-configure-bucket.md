# Creating and Configuring an S3 Bucket<a name="create-configure-bucket"></a>

Amazon S3 is cloud storage for the Internet\. To upload your data \(photos, videos, documents etc\.\), you first create a bucket in one of the AWS Regions\. You can then upload your data objects to the bucket\.

Every object you store in Amazon S3 resides in a bucket\. You can use buckets to group related objects in the same way that you use a directory to group files in a file system\. 

Amazon S3 creates buckets in the AWS Region that you specify\. You can choose any AWS Region that is geographically close to you to optimize latency, minimize costs, or address regulatory requirements\. For example, if you reside in Europe, you might find it advantageous to create buckets in the EU \(Ireland\) or EU \(Frankfurt\) regions\. For a list of Amazon S3 AWS Regions, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) in the *Amazon Web Services General Reference*\.

You are not charged for creating a bucket\. You are only charged for storing objects in the bucket and for transferring objects out of the bucket\. For more information about pricing, see [Amazon Simple Storage Service \(S3\) FAQs](https://aws.amazon.com/s3/faqs/)\.

Amazon S3 bucket names are globally unique, regardless of the AWS Region in which you create the bucket\. You specify the name at the time you create the bucket\. For bucket naming guidelines, see [Bucket Restrictions and Limitations](http://docs.aws.amazon.com/AmazonS3/latest/dev/BucketRestrictions.html) in the *Amazon Simple Storage Service Developer Guide*\.

The following topics explain how to use the Amazon S3 console to create, delete, and manage buckets\.

**Topics**
+ [Creating a Bucket](create-bucket.md)
+ [Deleting a Bucket](delete-bucket.md)
+ [Emptying a Bucket](empty-bucket.md)
+ [Viewing Bucket Properties](view-bucket-properties.md)
+ [Enabling or Disabling Versioning](enable-versioning.md)
+ [Enabling Default Encryption](default-bucket-encryption.md)
+ [Enabling Server Access Logging](server-access-logging.md)
+ [Enabling Object\-Level Logging](enable-cloudtrail-events.md)
+ [Configuring Static Website Hosting](static-website-hosting.md)
+ [Redirecting Website Requests](redirect-website-requests.md)
+ [Advanced Settings](setup-advanced-bucket-properties.md)