# How do I redirect requests to an S3 bucket hosted website to another host?<a name="redirect-website-requests"></a>

For more detailed information about configuring a redirect in Amazon S3, see [Configuring a webpage redirect](https://docs.aws.amazon.com/AmazonS3/latest/dev/how-to-page-redirect.html) in the *Amazon Simple Storage Service Developer Guide*\.

You can redirect all requests for a website endpoint for a bucket to another host\. If you redirect all requests, any request made to the website endpoint is redirected to the specified host name\. 

For example, if your root domain is `example.com`, and you want to serve requests for both `http://example.com` and `http://www.example.com`, you can create two buckets named `example.com` and `www.example.com`\. Then, maintain the content in the `example.com` bucket, and configure the other `www.example.com` bucket to redirect all requests to the `example.com` bucket\. For more information, see [Configuring a Static Website Using a Custom Domain Name](https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html)\.

**To redirect requests for a bucket website endpoint**

1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Under **Buckets**, choose the name of the bucket that you want to redirect requests from \(for example, `www.example.com`\)\.

1. Choose **Properties**\.

1. Under **Static website hosting**, choose **Edit**\.

1. Choose **Redirect requests for an object**\. 

1. In the **Host name** box, enter the website endpoint for your bucket or your custom domain\.

   For example, if you are redirecting to a root domain address, you would enter **example\.com**\.

1. For **Protocol**, choose the protocol for the redirected requests \(**none**,**http**, or **https**\)\.

   If you do not specify a protocol, the default option is **none**\.

1. Choose **Save changes**\.