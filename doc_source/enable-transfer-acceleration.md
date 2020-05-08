# How do I enable transfer acceleration for an S3 bucket?<a name="enable-transfer-acceleration"></a>

Amazon Simple Storage Service \(Amazon S3\) transfer acceleration enables fast, easy, and secure transfers of files between your client and an S3 bucket over long distances\. This topic describes how to enable Amazon S3 transfer acceleration for a bucket\. For more information, see [Amazon S3 Transfer Acceleration](https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To enable transfer acceleration for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to enable transfer acceleration for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Choose **Transfer acceleration**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/transfer-acceleration-box.png)

1. Choose **Enabled**, and then choose **Save**\.

   **Endpoint** displays the endpoint domain name that you use to access accelerated data transfers to and from the bucket that is enabled for transfer acceleration\. If you suspend transfer acceleration, the accelerate endpoint no longer works\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/enable-transfer-acceleration.png)

1. \(Optional\) If you want to run the [ Amazon S3 Transfer Acceleration Speed Comparison tool,](https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html#transfer-acceleration-why-use) which compares accelerated and non\-accelerated upload speeds starting with the Region in which the transfer acceleration bucket is enabled, choose the **Want to compare your data transfer speed by region?** option\. The Speed Comparison tool uses multipart uploads to transfer a file from your browser to various AWS Regions with and without using Amazon S3 transfer acceleration\.

**More Info**  
 [How do I view the properties for an S3 Bucket?](view-bucket-properties.md)