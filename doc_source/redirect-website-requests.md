# How Do I Redirect Requests to an S3 Bucket Hosted Website to Another Host?<a name="redirect-website-requests"></a>

You can redirect all requests to your S3 bucket hosted static website to another host\. 

**To redirect all requests to an S3 bucket's website endpoint to another host**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to redirect all requests from\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Choose **Static website hosting**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/static-website-hosting-box.png)

1. Choose **Redirect requests**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/static-website-hosting-redirect-requests.png)

   1. For **Target bucket or domain**, type the name of the bucket or the domain name where you want requests to be redirected\. To redirect requests to another bucket, type the name of the target bucket\. For example, if you are redirecting to a root domain address, you would type **www\.example\.com**\. For more information, see [Configure a Bucket for Website Hosting](https://docs.aws.amazon.com/AmazonS3/latest/dev/HowDoIWebsiteConfiguration.html) in the *Amazon Simple Storage Service Developer Guide*\.

   1. For **Protocol**, type the protocol \(http, https\) for the redirected requests\. If no protocol is specified, the protocol of the original request is used\. If you redirect all requests, any request made to the bucket's website endpoint will be redirected to the specified host name\. 

1. Choose **Save**\.