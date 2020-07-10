# How do I download an object from an S3 bucket?<a name="download-objects"></a>

This section explains how to use the Amazon S3 console to download objects from an S3 bucket\.

Data transfer fees apply when you download objects\. For information about Amazon S3 features, and pricing, see [Amazon S3](https://aws.amazon.com/s3/)\.

**Important**  
If an object key name consists of a single period \(\.\), or two periods \(\.\.\), you can’t download the object using the Amazon S3 console\. To download an object with a key name of “\.” or “\.\.”, you must use the AWS CLI, AWS SDKs, or REST API\. For more information about naming objects, see [Object Key Naming Guidelines](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#object-key-guidelines) in the *Amazon Simple Storage Service Developer Guide*\.
You can download a single object per request using the Amazon S3 console\. To [download multiple objects, use the AWS CLI, AWS SDKs, or REST API](https://docs.aws.amazon.com/AmazonS3/latest/dev/GettingObjectsUsingAPIs.html)\.

**To download an object from an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to download an object from\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. You can download an object from an S3 bucket in any of the following ways:
   + In the **Name** list, select the check box next to the object you want to download, and then choose **Download** on the object description page that appears\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/download-select-box.png)
   + Choose the name of the object that you want to download\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-name-select.png)

     On the **Overview** page, choose **Download**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-overview-download.png)
   + Choose the name of the object that you want to download and then choose **Download as** on the **Overview** page\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-download-as.png)
   + Choose the name of the object that you want to download\. Choose **Latest version** and then choose the download icon\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-latest-version-download.png)

## Related topics<a name="download-objects-related-topics"></a>
+  [How do I upload files and folders to an S3 bucket?](upload-objects.md)