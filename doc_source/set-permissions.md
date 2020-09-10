# Setting bucket and object access permissions<a name="set-permissions"></a>

This section explains how to use the Amazon Simple Storage Service \(Amazon S3\) console to grant access permissions to your buckets and objects\. It also explains how to use Amazon S3 block public access to prevent the application of any settings that allow public access to data within S3 buckets\. 

 Buckets and objects are Amazon S3 resources\.  You grant access permissions to your buckets and objects by using resource\-based access policies\. You can associate an access policy with a resource\. An access policy describes who has access to resources\. The resource owner is the AWS account that creates the resource\. For more information about resource ownership and access policies, see [Overview of Managing Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) in the *Amazon Simple Storage Service Developer Guide*\. 

*Bucket access permissions* specify which users are allowed access to the objects in a bucket and which types of access they have\. *Object access permissions* specify which users are allowed access to the object and which types of access they have\. For example, one user might have only read permission, while another might have read and write permissions\.

Bucket and object permissions are independent of each other\. An object does not inherit the permissions from its bucket\. For example, if you create a bucket and grant write access to a user, you can't access that user’s objects unless the user explicitly grants you access\. Bucket permissions generally allow a user to list information about a bucket and add and delete objects from a bucket\. Object permissions generally allow a user to download, replace or delete objects\.

**Note**  
You do not necessarily need to grant bucket permissions in order to grant object permissions, and vice versa\. For example, you can use the AWS console to grant a user update permissions on an object without granting that user permissions to the bucket containing that object\. However, if you were to grant permissions only to the object, and not the bucket, the grantee would not be able to use the AWS console to access the object\. \(They would not be able to view the object in the console because they would not be able to view the bucket containing the object\.\) The grantee instead would have to access the object programmatically, such as with the AWS CLI\.

 To grant access to your buckets and objects to other AWS accounts and to the general public, you use resource\-based access policies known as *access control lists* \(ACLs\)\. 

A *bucket policy* is a resource\-based AWS Identity and Access Management \(IAM\) policy that grants other AWS accounts or IAM users access to an S3 bucket\. Bucket policies supplement, and in many cases, replace ACL\-based access policies\.  For more information about using IAM with Amazon S3, see [Managing Access Permissions to Your Amazon S3 Resources](https://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html) in the *Amazon Simple Storage Service Developer Guide*\. 

For more in\-depth information about managing access permissions, see [Introduction to Managing Access Permissions to Your Amazon S3 Resources](https://docs.aws.amazon.com/AmazonS3/latest/dev/intro-managing-access-s3-resources.html) in the *Amazon Simple Storage Service Developer Guide*\.

This section also explains how to use the Amazon S3 console to add a cross\-origin resource sharing \(CORS\) configuration to an S3 bucket\. CORS allows client web applications that are loaded in one domain to interact with resources in another domain\.

**Topics**
+ [Blocking public access](block-public-access.md)
+ [Editing bucket public access settings](block-public-access-bucket.md)
+ [Editing account public access settings](block-public-access-account.md)
+ [Setting object permissions](set-object-permissions.md)
+ [Setting ACL bucket permissions](set-bucket-permissions.md)
+ [Adding a bucket policy](add-bucket-policy.md)
+ [Adding cross\-domain resource sharing with CORS](add-cors-configuration.md)
+ [Using Access Analyzer for S3](access-analyzer.md)