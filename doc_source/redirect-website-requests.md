# How do I redirect requests to an S3 bucket hosted website to another host?<a name="redirect-website-requests"></a>

For more detailed information about configuring a redirect in Amazon S3, see [Configuring a webpage redirect](https://docs.aws.amazon.com/AmazonS3/latest/dev/how-to-page-redirect.html) in the *Amazon Simple Storage Service Developer Guide*\.

You can redirect all requests for a website endpoint for a bucket to another host\. If you redirect all requests, any request made to the website endpoint is redirected to the specified host name\. 

For example, if your root domain is `example.com`, and you want to serve requests for both `http://example.com` and `http://www.example.com`, you can create two buckets named `example.com` and `www.example.com`\. Then, maintain the content in the `example.com` bucket, and configure the other `www.example.com` bucket to redirect all requests to the `example.com` bucket\. For more information, see [Configuring a Static Website Using a Custom Domain Name](https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html)\.

**To redirect requests for a bucket website endpoint**

1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Choose the name of the bucket that you have configured as a static website \(for example, `example.com`\)\.

1. Choose **Properties**\.

1. Choose **Static website hosting**\.

1. Choose **Redirect requests**\. 

1. In the **Target bucket or domain** box, enter the bucket or domain that you want to redirect to\.

   For example, if you are redirecting to a root domain address, you would enter **example\.com**\.

1. In the **Protocol** box, enter the protocol for the redirected requests \(**http** or **https**\)\.

   If you do not specify a protocol, the protocol of the original request is used\.

1. Choose **Save**\.