# How do I set permissions on an object?<a name="set-object-permissions"></a>

This section explains how to use the Amazon Simple Storage Service \(Amazon S3\) console to manage access permissions for an Amazon S3 object by using access control lists \(ACLs\)\. ACLs are resource\-based access policies that grant access permissions to buckets and objects\. For more information about managing access permissions with resource\-based policies, see [Overview of Managing Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

Bucket and object permissions are independent of each other\. An object does not inherit the permissions from its bucket\. For example, if you create a bucket and grant write access to a user, you can't access that user’s objects unless the user explicitly grants you access\.

You can grant permissions to other AWS accounts or predefined groups\. The user or group that you grant permissions to is called the *grantee*\. By default, the owner, which is the AWS account that created the bucket, has full permissions\.

Each permission you grant for a user or a group adds an entry in the ACL that is associated with the object\. The ACL lists grants, which identify the grantee and the permission granted\. For more information about ACLs, see [Managing Access with ACLs](https://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To set permissions for an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects for which you want to set permissions\.

1. Choose the **Permissions** tab that appears in the list of tabs under the **Bucket overview** section\. 

1. To edit *Block Public Access settings*, choose **Edit** to block or allow public access to this bucket and its access points\. For more information, see [Blocking public access](block-public-access.md)\.

1. To edit *Bucket policy*, choose **Edit** to edit the JSON bucket policy that provides access to objects stored in this bucket\. This policy only applies to objects owned by your account\.

   Alternatively, if you have an existing bucket policy, you can choose **Delete** to delete an existing bucket policy\. For more information, see [Adding a bucket policy](add-bucket-policy.md)\.

1. To edit *Object ownership*, choose **Edit** to assume ownership of new objects uploaded to this bucket\. For more information, see [](add-object-ownership.md)\.

1. To edit the *Access control list \(ACL\)*, choose **Edit** to update permissions \(list, read, and write\) to grantee groups such as *Bucket owner* \(your AWS account\), *Everyone*, *Authenticated users *\(anyone with an AWS account\), or *S3 log delivery group*\.

   1. The *Bucket owner* refers to your AWS account, and not an AWS Identity and Access Management \(IAM\) user\. For more information about the root user, see [AWS Account Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html) in the *IAM User Guide*\.

   1. To grant access to your object to *Everyone*, choose **Everyone**\. Granting public access permissions means that anyone in the world can access the object\.
**Warning**  
Use caution when granting the **Everyone** group anonymous access to your Amazon S3 objects\. When you grant access to this group, anyone in the world can access your object\. If you need to grant access to everyone, we highly recommend that you only grant permissions to **Read objects**\.
We highly recommend that you *do not* grant the **Everyone** group write object permissions\. Doing so allows anyone to overwrite the ACL permissions for the object\.

   1. To grant permissions to an AWS user from a different AWS account, enter the canonical ID of the AWS user that you want to grant object permissions to\. For information about finding a canonical ID, see [AWS Account Identifiers](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) in the *Amazon Web Services General Reference*\. You can add as many as 99 users\.

   1. To specify the *S3 log delivery group*, provide the name of the target bucket where you want Amazon S3 to save the access logs as objects\.

   For more information, see [Setting ACL bucket permissions](set-bucket-permissions.md) and [How to enable server access logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html#server-access-logging-overview) in the *Amazon Simple Storage Service Developer Guide*\.

1. To edit *Cross\-origin resource sharing \(CORS\)*, choose **Edit** to create a CORS configuration, which is an XML document that defines how client web applications that are loaded in one domain interact with resources in a different domain\. For more information, see [Adding cross\-domain resource sharing with CORS](add-cors-configuration.md)\.

1. After editing any of the settings in the previous steps, choose **Save changes** when you are finished\.

**Note**  
This action applies permissions to all specified objects\. When applying permissions to folders, wait for the save operation to finish before adding new objects\.

You can also set object permissions when you upload objects\. For more information about setting permissions when uploading objects, see [Uploading S3 objects](upload-objects.md)\.

## More Info<a name="set-object-permissions-moreinfo"></a>
+  [Setting bucket and object access permissions](set-permissions.md)
+ [How do I set ACL bucket permissions?](set-bucket-permissions.md)