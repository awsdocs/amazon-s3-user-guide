# How Do I Configure an S3 Bucket for Static Website Hosting?<a name="static-website-hosting"></a>

You can host a static website on Amazon S3\. On a static website, individual webpages include static content, and they might also contain client\-side scripts\. By contrast, a dynamic website relies on server\-side processing, including server\-side scripts such as PHP, JSP, or ASP\.NET\. Amazon S3 does not support server\-side scripting\.

The following is a quick procedure to configure an Amazon S3 bucket for static website hosting in the Amazon S3 console\. If you’re looking for more in\-depth information, and walkthroughs on using a custom domain name for your static website or speeding up your website, see [Hosting a Static Website on Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To configure an S3 bucket for static website hosting**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to enable static website hosting for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Choose **Static website hosting**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/static-website-hosting-box.png)

1. Choose **Use this bucket to host a website**\. 

   After you enable your bucket for static website hosting, web browsers can access all of your content through the Amazon S3 website endpoint for your bucket\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/website-endpoint.png)

   1. In **Index document**, enter the name of the index document, which is typically `index.html`\. 

      When you configure a bucket for website hosting, you must specify an index document\. Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders\. For more information, see [Configuring a Bucket for Website Hosting](https://docs.aws.amazon.com/AmazonS3/latest/dev/HowDoIWebsiteConfiguration.html) in the *Amazon Simple Storage Service Developer Guide*\.

   1. \(Optional\) For 4XX class errors, you can optionally provide your own custom error document that provides additional guidance for your users\. 

      For **Error Document**, enter the name of the file that contains the custom error document\. If an error occurs, Amazon S3 returns an HTML error document\. For more information, see [Custom Error Document Support](https://docs.aws.amazon.com/AmazonS3/latest/dev/CustomErrorDocSupport.html) in the *Amazon Simple Storage Service Developer Guide*\.

   1. \(Optional\) If you want to specify advanced redirection rules, in the **Edit redirection rules** text area, use XML to describe the rules\.

       For example, you can conditionally route requests according to specific object key names or prefixes in the request\. For more information, see [Configuring a Bucket for Website Hosting](https://docs.aws.amazon.com/AmazonS3/latest/dev/HowDoIWebsiteConfiguration.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/static-website-hosting-enable.png)

1. Choose **Save**\.

1. To disable block public access for the bucket, follow these steps:

   1. Select the bucket, and choose **Edit public access settings**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/edit-public-access-settings.png)

   1. Clear **Block *all* public access**, and choose **Save**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/edit-public-access-clear.png)

   1. To confirm your changes, enter **confirm**, and then choose **Confirm**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/edit-public-access-confirm.png)

1. To grant public read access for your website, add a bucket policy to the website bucket that grants public read access to the bucket\.

   1. Copy the following bucket policy, and paste it in the **Bucket policy editor**\.

   1. Update the Resource to include your bucket name\.

      In the example below, *example\-bucket* is the bucket\. To use this bucket policy with your own bucket, you must update this name to match your bucket\.

      ```
      {
          "Version": "2012-10-17",
          "Statement": [
              {
                  "Sid": "PublicReadGetObject",
                  "Effect": "Allow",
                  "Principal": "*",
                  "Action": [
                      "s3:GetObject"
                  ],
                  "Resource": [
                      "arn:aws:s3:::example-bucket/*"
                  ]
              }
          ]
      }
      ```

   1. Choose **Save**\.

   For information about adding a bucket policy, see [How Do I Add an S3 Bucket Policy?](add-bucket-policy.md) For more information about website permissions, see [Permissions Required for Website Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteAccessPermissionsReqd.html) in the *Amazon Simple Storage Service Developer Guide*\. 

**Note**  
If you choose **Disable website hosting**, Amazon S3 removes the website configuration from the bucket, so that the bucket is no longer accessible from the website endpoint\. However, the bucket is still available at the REST endpoint\. For a list of Amazon S3 endpoints, see [Amazon S3 Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region) in the *Amazon Web Services General Reference*\.