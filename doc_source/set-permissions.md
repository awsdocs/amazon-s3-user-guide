# Setting Bucket and Object Access Permissions<a name="set-permissions"></a>

The topics in this section explain how to use the Amazon S3 console to grant access permissions to your buckets and objects by using resource\-based access policies\. An access policy describes who has access to resources\. You can associate an access policy with a resource\.

 Buckets and objects are Amazon Simple Storage Service \(Amazon S3\) resources\. By default, all Amazon S3 resources are private, which means that only the resource owner can access the resource\. The resource owner is the AWS account that creates the resource\. For more information about resource ownership and access policies, see [Overview of Managing Access](http://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) in the *Amazon Simple Storage Service Developer Guide*\. 

*Bucket access permissions* specify which users are allowed access to the objects in a bucket and which types of access they have\. *Object access permissions* specify which users are allowed access to the object and which types of access they have\. For example, one user might have only read permission, while another might have read and write permissions\.

Bucket and object permissions are independent of each other\. An object does not inherit the permissions from its bucket\. For example, if you create a bucket and grant write access to a user, you will not be able to access that user’s objects unless the user explicitly grants you access\.

 To grant access to your buckets and objects to other AWS accounts and to the general public, you use resource\-based access policies called access control lists \(ACLs\)\. 

A *bucket policy* is a resource\-based AWS Identity and Access Management \(IAM\) policy that grants other AWS accounts or IAM users access to an S3 bucket\. Bucket policies supplement, and in many cases, replace ACL\-based access policies\.  For more information on using IAM with Amazon S3, see [Managing Access Permissions to Your Amazon S3 Resources](http://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html) in the *Amazon Simple Storage Service Developer Guide*\.  

For more in\-depth information about managing access permissions, see [Introduction to Managing Access Permissions to Your Amazon S3 Resources](http://docs.aws.amazon.com/AmazonS3/latest/dev/intro-managing-access-s3-resources.html) in the *Amazon Simple Storage Service Developer Guide*\.

This section also explains how to use the Amazon S3 console to add a cross\-origin resource sharing \(CORS\) configuration to an S3 bucket\. CORS allows client web applications that are loaded in one domain to interact with resources in another domain\.

