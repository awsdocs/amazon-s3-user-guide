# How do I configure an S3 bucket for static website hosting?<a name="static-website-hosting"></a>

You can host a static website on Amazon S3\. On a static website, individual webpages include static content\. A static website might also contain client\-side scripts\. By contrast, a dynamic website relies on server\-side processing, including server\-side scripts such as PHP, JSP, or ASP\.NET\. Amazon S3 does not support server\-side scripting\.

You can use the following quick procedures to configure an S3 bucket for static website hosting in the Amazon S3 console\. For more information, see [Hosting a Static Website on Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html) in the *Amazon Simple Storage Service Developer Guide*\. For information about configuring a static website with a custom domain, see [Configuring a static website using a custom domain registered with Route 53](https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Topics**
+ [Step 1: Configuring a bucket for static website hosting](#configure-bucket-website-hosting)
+ [Step 2: Editing S3 Block Public Access settings](#set-permissions-static-website-access)
+ [Step 3: Adding a bucket policy](#add-bucket-policy-public-access)
+ [Step 4: Testing your website endpoint](#test-your-website-endpoint)

## Step 1: Configuring a bucket for static website hosting<a name="configure-bucket-website-hosting"></a>

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want to use to host a static website\.

1. Choose **Properties**\.

1. Under **Static website hosting**, choose **Edit**\.

1. Choose **Use this bucket to host a website**\. 

1. Under **Static website hosting**, choose **Enable**\.

1. In **Index document**, enter the file name of the index document, typically `index.html`\. 

   The index document name is case sensitive and must exactly match the file name of the HTML index document that you plan to upload to your S3 bucket\. When you configure a bucket for website hosting, you must specify an index document\. Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders\. For more information, see [Configuring an index document](https://docs.aws.amazon.com/AmazonS3/latest/dev/IndexDocumentSupport.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. \(Optional\) If you want to provide your own custom error document for 4XX class errors, in **Error document**, enter the custom error document file name\. 

   The error document name is case sensitive and must exactly match the file name of the HTML error document that you plan to upload to your S3 bucket\. If you don't specify a custom error document and an error occurs, Amazon S3 returns a default HTML error document\. For more information, see [Configuring a custom error document](https://docs.aws.amazon.com/AmazonS3/latest/dev/CustomErrorDocSupport.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. \(Optional\) If you want to specify advanced redirection rules, in **Redirection rules**, enter XML to describe the rules\.

   For example, you can conditionally route requests according to specific object key names or prefixes in the request\. For more information, see [Configuring advanced conditional redirects](https://docs.aws.amazon.com/AmazonS3/latest/dev/how-to-page-redirect.html#advanced-conditional-redirects) in the *Amazon Simple Storage Service Developer Guide*\.

1. Choose **Save changes**\.

   Amazon S3 enables static website hosting for your bucket\. At the bottom of the page, under **Static website hosting**, you see the website endpoint for your bucket\.

1. Upload the index document to your bucket\.

   For step\-by\-step instructions on uploading an object to an S3 bucket, see [Uploading Files by Pointing and Clicking](upload-objects.md#upload-objects-by-file-selection)\. 

1. Upload other files for your website, including optional custom error documents\.

In the next section, you set the permissions required to access your bucket as a static website\.

## Step 2: Editing S3 Block Public Access settings<a name="set-permissions-static-website-access"></a>

By default, Amazon S3 blocks public access to your account and buckets\. If you want to use a bucket to host a static website, you can use these steps to edit your block public access settings\. 

**Warning**  
Before you complete this step, review [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) to ensure that you understand and accept the risks involved with allowing public access\. When you turn off block public access settings to make your bucket public, anyone on the internet can access your bucket\. We recommend that you block all public access to your buckets\.

1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Choose the name of the bucket that you have configured as a static website\.

1. Choose **Permissions**\.

1. Under **Block public access \(bucket settings\)**, choose **Edit**\.

1. Clear **Block *all* public access**, and choose **Save changes**\.
**Warning**  
Before you complete this step, review [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) to ensure you understand and accept the risks involved with allowing public access\. When you turn off block public access settings to make your bucket public, anyone on the internet can access your bucket\. We recommend that you block all public access to your buckets\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/edit-public-access-clear.png)

   Amazon S3 turns off Block Public Access settings for your bucket\. To create a public, static website, you might also have to [edit the Block Public Access settings](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/block-public-access-account.html) for your account before adding a bucket policy\. If account settings for Block Public Access are currently turned on, you see a note under **Block public access \(bucket settings\)**\.

## Step 3: Adding a bucket policy<a name="add-bucket-policy-public-access"></a>

After you edit S3 Block Public Access settings, you can add a bucket policy to grant public read access to your bucket\. When you grant public read access, anyone on the internet can access your bucket\.

**Important**  
The following policy is an example only and allows full access to the contents of your bucket\. Before you proceed with this step, review [How can I secure the files in my Amazon S3 bucket?](https://aws.amazon.com/premiumsupport/knowledge-center/secure-s3-resources/) to ensure that you understand the best practices for securing the files in your S3 bucket and risks involved in granting public access\.

1. Under **Buckets**, choose the name of your bucket\.

1. Choose **Permissions**\.

1. Under **Bucket Policy**, choose **Edit**\.

1. To grant public read access for your website, copy the following bucket policy, and paste it in the **Bucket policy editor**\.

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
                   "arn:aws:s3:::example.com/*"
               ]
           }
       ]
   }
   ```

1. Update the `Resource` to your bucket name\.

   In the preceding example bucket policy, *example\.com* is the bucket name\. To use this bucket policy with your own bucket, you must update this name to match your bucket name\.

1. Choose **Save changes**\.

   A message appears indicating that the bucket policy has been successfully added\.

   If you see an error that says `Policy has invalid resource`, confirm that the bucket name in the bucket policy matches your bucket name\. For information about adding a bucket policy, see [How do I add an S3 bucket policy?](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/add-bucket-policy.html)

   If you get an error message and cannot save the bucket policy, check your account and bucket Block Public Access settings to confirm that you allow public access to the bucket\.

After you edit S3 Block Public Access settings, you can add a bucket policy to grant public read access to your bucket\. When you grant public read access, anyone on the internet can access your bucket\.

**Important**  
The following policy is an example only and allows full access to the contents of your bucket\. Before you proceed with this step, review [How can I secure the files in my Amazon S3 bucket?](https://aws.amazon.com/premiumsupport/knowledge-center/secure-s3-resources/) to ensure that you understand the best practices for securing the files in your S3 bucket and risks involved in granting public access\.

## Step 4: Testing your website endpoint<a name="test-your-website-endpoint"></a>

After you configure your bucket as a static website and set permissions, you can access your website through an Amazon S3 website endpoint\. For more information, see [Website endpoints](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteEndpoints.html) in the *Amazon Simple Storage Service Developer Guide*\. For a complete list of Amazon S3 website endpoints, see [Amazon S3 Website Endpoints](https://docs.aws.amazon.com/general/latest/gr/s3.html#s3_website_region_endpoints) in the *Amazon Web Services General Reference*\.

1. Under **Buckets**, choose the name of your bucket\.

1. Choose **Properties**\.

1. At the bottom of the page, under **Static website hosting**, choose your **Bucket website endpoint**\.

   Your index document opens in a separate browser window\.