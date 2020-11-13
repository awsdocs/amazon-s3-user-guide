# Editing object tags<a name="add-object-tags"></a>

Object tagging gives you a way to categorize storage\. This topic explains how to use the console to add tags to an S3 object after the object has been uploaded\. For information about adding tags to an object when the object is being uploaded, see [How do I upload files and folders to an S3 bucket?](upload-objects.md)\. 

Each tag is a key\-value pair that adheres to the following rules:
+ You can associate up to 10 tags with an object\. Tags associated with an object must have unique tag keys\.
+ A tag key can be up to 128 Unicode characters in length and tag values can be up to 256 Unicode characters in length\.
+ Key and tag values are case sensitive\. 

For more information about object tags, see [Object Tagging](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html) in the *Amazon Simple Storage Service Developer Guide*\. For more information about tag restrictions, see [User\-Defined Tag Restrictions](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/allocation-tag-restrictions.html) in the *AWS Billing and Cost Management User Guide*\. 

**To add tags to an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects that you want to add tags to\.

   You can also optionally navigate to a folder\.

1. In the **Objects** list, select the checkbox next to the names of the objects that you want to add tags to\.

1. In the **Actions** menu, choose **Edit tags**\.

1. Review the objects listed, and choose **Add tags**\.

1. Each object tag is a key\-value pair\. Enter a **Key** and a **Value**\. To add another tag, choose **Add Tag**\. 

   You can enter up to 10 tags for an object\.

1. Choose **Save changes**\.

   Amazon S3 adds the tags to the specified objects\.

For more information, see also [How do I view the properties of an object?](view-object-properties.md) and [Uploading, downloading, and managing objects](upload-download-objects.md) in this guide\. 