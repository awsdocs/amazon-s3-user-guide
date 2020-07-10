# How do I configure an S3 bucket for static website hosting?<a name="static-website-hosting"></a>

You can host a static website on Amazon S3\. On a static website, individual webpages include static content\. A static website might also contain client\-side scripts\. By contrast, a dynamic website relies on server\-side processing, including server\-side scripts such as PHP, JSP, or ASP\.NET\. Amazon S3 does not support server\-side scripting\.

You can use the following quick procedures to configure an S3 bucket for static website hosting in the Amazon S3 console\. For more information and detailed walkthroughs, see [Hosting a Static Website on Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Topics**
+ [Step 1: Configure an Amazon S3 bucket for static website hosting](#configure-bucket-website-hosting)
+ [Step 2: Editing block public access settings](#set-permissions-static-website-access)
+ [Step 3: Adding a bucket policy](#add-bucket-policy-public-access)
+ [Step 4: Test your website endpoint](#test-your-website-endpoint)

## Step 1: Configure an Amazon S3 bucket for static website hosting<a name="configure-bucket-website-hosting"></a>

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to enable static website hosting for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Properties**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-properties-tab.png)

1. Choose **Static website hosting**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/static-website-hosting-box.png)

1. Choose **Use this bucket to host a website**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/website-endpoint.png)

1. In **Index document**, enter the name of the index document, typically `index.html`\. 

   When you configure a bucket for website hosting, you must specify an index document\. Amazon S3 returns this index document when requests are made to the root domain or any of the subfolders\. For more information, see [Configuring Index Document Support](https://docs.aws.amazon.com/AmazonS3/latest/dev/IndexDocumentSupport.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. \(Optional\) If you want to provide your own custom error document for 4XX class errors, in **Error Document**, enter the custom error document filename\. 

   If you do not specify a custom error document and an error occurs, Amazon S3 returns a default HTML error document\. For more information, see [Custom Error Document Support](https://docs.aws.amazon.com/AmazonS3/latest/dev/CustomErrorDocSupport.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. \(Optional\) If you want to specify advanced redirection rules, in the **Edit redirection rules** box, enter XML to describe the rules\.

   For example, you can conditionally route requests according to specific object key names or prefixes in the request\. For more information, see [Advanced Conditional Redirects](https://docs.aws.amazon.com/AmazonS3/latest/dev/how-to-page-redirect.html#advanced-conditional-redirects) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/static-website-hosting-enable.png)

1. Choose **Save**\.

1. Upload the index document to your bucket\.

   For step\-by\-step instructions on uploading an object to an S3 bucket, see [Uploading Files by Pointing and Clicking](upload-objects.md#upload-objects-by-file-selection)\. 

1. Upload other files for your website, including optional custom error documents\.

In the next section, you set the permissions required to access your bucket as a static website\.\.

## Step 2: Editing block public access settings<a name="set-permissions-static-website-access"></a>

By default, Amazon S3 blocks public access to your account and buckets\. If you want to use a bucket to host a static website, you can use these steps to edit your block public access settings\. 

**Warning**  
Before you complete this step, review [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) to ensure that you understand and accept the risks involved with allowing public access\. When you turn off block public access settings to make your bucket public, anyone on the internet can access your bucket\. We recommend that you block all public access to your buckets\.

1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Choose the name of the bucket that you have configured as a static website\.

1. Choose **Permissions**\.

1. Choose **Edit**\.

1. Clear **Block *all* public access**, and choose **Save**\.
**Warning**  
Before you complete this step, review [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) to ensure you understand and accept the risks involved with allowing public access\. When you turn off block public access settings to make your bucket public, anyone on the internet can access your bucket\. We recommend that you block all public access to your buckets\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/edit-public-access-clear.png)

1. In the confirmation box, enter **confirm**, and then choose **Confirm**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/edit-public-access-confirm.png)

   Under **S3 buckets**, the **Access** for your bucket updates to **Objects can be public**\. You can now add a bucket policy to make the objects in the bucket publicly readable\. If the **Access** still displays as **Bucket and objects not public**, you might have to [edit the block public access settings](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/block-public-access-account.html) for your account before adding a bucket policy\.

## Step 3: Adding a bucket policy<a name="add-bucket-policy-public-access"></a>

After you edit S3 Block Public Access settings, you can add a bucket policy to grant public read access to your bucket\. When you grant public read access, anyone on the internet can access your bucket\.

**Important**  
The following policy is an example only and allows full access to the contents of your bucket\. Before you proceed with this step, review [How can I secure the files in my Amazon S3 bucket?](https://aws.amazon.com/premiumsupport/knowledge-center/secure-s3-resources/) to ensure that you understand the best practices for securing the files in your S3 bucket and risks involved in granting public access\.

1. Under **Buckets**, choose the name of your bucket\.

1. Choose **Permissions**\.

1. Choose **Bucket Policy**\.

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

1. Update the `Resource` to include your bucket name\.

   In the preceding example bucket policy, *example\.com* is the bucket name\. To use this bucket policy with your own bucket, you must update this name to match your bucket name\.

1. Choose **Save**\.

   A warning appears indicating that the bucket has public access\. In **Bucket Policy**, a **Public** label appears\.

   If you see an error that says `Policy has invalid resource`, confirm that the bucket name in the bucket policy matches your bucket name\. For information about adding a bucket policy, see [How Do I Add an S3 Bucket Policy?](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/add-bucket-policy.html)

   If you get an **Error \- Access denied** warning and the **Bucket policy editor** does not allow you to save the bucket policy, check your account\-level and bucket\-level block public access settings to confirm that you allow public access to the bucket\.

## Step 4: Test your website endpoint<a name="test-your-website-endpoint"></a>

Once you configure your bucket as a static website and set permissions, you can access your website through an Amazon S3 website endpoint\. For more information, see [Website Endpoints](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteEndpoints.html) in the *Amazon Simple Storage Service Developer Guide*\. For a complete list of Amazon S3 website endpoints, see [Amazon S3 Website Endpoints](https://docs.aws.amazon.com/general/latest/gr/s3.html#s3_website_region_endpoints) in the *Amazon Web Services General Reference*\.