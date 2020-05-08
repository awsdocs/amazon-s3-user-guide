# How do I add cross\-domain resource sharing with CORS?<a name="add-cors-configuration"></a>

This section explains how to use the Amazon S3 console to add a cross\-origin resource sharing \(CORS\) configuration to an S3 bucket\. CORS allows client web applications that are loaded in one domain to interact with resources in another domain\. 

To configure your bucket to allow cross\-origin requests, you add CORS configuration to the bucket\. A CORS configuration is an XML document that defines rules that identify the origins that you will allow to access your bucket, the operations \(HTTP methods\) supported for each origin, and other operation\-specific information\. For more information about CORS and examples, see [Cross\-Origin Resource Sharing \(CORS\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html) in the *Amazon Simple Storage Service Developer Guide*\.

When you enable CORS on the bucket, the access control lists \(ACLs\) and other access permission policies continue to apply\.

**To add a CORS configuration to an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to create a bucket policy for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Permissions**, and then choose **CORS configuration**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-permissions-cors.png)

1. In the **CORS configuration editor** text box, type or copy and paste a new CORS configuration, or edit an existing configuration\. The CORS configuration is an XML file\. The text that you type in the editor must be valid XML\. For more information, see [How Do I Configure CORS on My Bucket?](https://docs.aws.amazon.com/AmazonS3/latest/dev/cors.html#how-do-i-enable-cors)

1. Choose **Save**\.
**Note**  
Amazon S3 displays the Amazon Resource Name \(ARN\) for the bucket next to the **CORS configuration editor** title\. For more information about ARNs, see [Amazon Resource Names \(ARNs\) and AWS Service Namespaces](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) in the *Amazon Web Services General Reference*\.

## More info<a name="add-cors-configuration-moreinfo"></a>
+  [Setting bucket and object access permissions](set-permissions.md)
+ [How do I set ACL bucket permissions?](set-bucket-permissions.md)
+ [How do I add an S3 Bucket policy?](add-bucket-policy.md)