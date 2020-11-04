# How do I enable transfer acceleration for an S3 bucket?<a name="enable-transfer-acceleration"></a>

Amazon Simple Storage Service \(Amazon S3\) transfer acceleration enables fast, easy, and secure file transfers between your client and an S3 bucket over long distances\. This topic describes how to enable Amazon S3 transfer acceleration for a bucket\. For more information, see [Amazon S3 Transfer Acceleration](https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Note**  
If you want to compare accelerated and non\-accelerated upload speeds, open the [ Amazon S3 Transfer Acceleration Speed Comparison tool](https://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html)\.  
The Speed Comparison tool uses multipart upload to transfer a file from your browser to various AWS Regions with and without Amazon S3 transfer acceleration\. You can compare the upload speed for direct uploads and transfer accelerated uploads by Region\. 

**To enable transfer acceleration for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want to enable transfer acceleration for\.

1. Choose **Properties**\.

1. Under **Transfer acceleration**, choose **Edit**\.

1. Choose **Enable**, and choose **Save changes**\.

   Amazon S3 enables transfer acceleration for your bucket and displays the **Properties** tab for your bucket\. Under **Transfer acceleration**, **Accelerated endpoint** displays the transfer acceleration endpoint for your bucket\. You use this endpoint to access accelerated data transfers to and from your bucket\. If you suspend transfer acceleration, the accelerate endpoint no longer works\.