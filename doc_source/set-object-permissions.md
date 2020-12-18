# How do I set permissions on an object?<a name="set-object-permissions"></a>

This section explains how to use the Amazon Simple Storage Service \(Amazon S3\) console to manage access permissions for an Amazon S3 object by using access control lists \(ACLs\)\. ACLs are resource\-based access policies that grant access permissions to buckets and objects\. For more information about managing access permissions with resource\-based policies, see [Overview of Managing Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

Bucket and object permissions are independent of each other\. An object does not inherit the permissions from its bucket\. For example, if you create a bucket and grant write access to a user, you can't access that user’s objects unless the user explicitly grants you access\.

You can grant permissions to other AWS accounts or predefined groups\. The user or group that you grant permissions to is called the *grantee*\. By default, the owner, which is the AWS account that created the bucket, has full permissions\.

Each permission you grant for a user or a group adds an entry in the ACL that is associated with the object\. The ACL lists grants, which identify the grantee and the permission granted\. For more information about ACLs, see [Managing Access with ACLs](https://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To set permissions for an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects for which you want to set permissions using ACLs\.

1. In the **Objects** list, choose the name of the object\.

1. Under **Access control list \(ACL\)**, choose **Edit**\.

1. To update ACL permissions \(list, read, and write\) to grantee groups such as *Object owner*, *Everyone \(public access\)*, and *Authenticated users group *\(anyone with an AWS account\), under **Objects** and **Object ACL**, select the check boxes for the **Read** and **Write** ACL permissions that you want to grant\.
**Warning**  
Use caution when granting the **Everyone** group anonymous access to your Amazon S3 objects\. When you grant access to this group, anyone in the world can access your object\. If you need to grant access to everyone, we highly recommend that you only grant permissions to **Read** objects\.
We highly recommend that you *do not* grant the **Everyone** group write object permissions\. Doing so allows anyone to overwrite the ACL permissions for the object\.

1. To grant permissions to a different AWS account, follow these steps:

   1. Choose **Add grantee**\.

   1. Enter the canonical ID of the AWS account that you want to grant object permissions to\. 

      For information about finding a canonical ID, see [AWS Account Identifiers](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) in the *Amazon Web Services General Reference*\. You can add as many as 99 users\.

   1. Select the ACL permissions that you want to grant to the other AWS account\.

1. Choose **Save changes**\.

**Note**  
This action applies permissions to all specified objects\. When applying permissions to folders, wait for the save operation to finish before adding new objects\.

You can also set object permissions when you upload objects\. For more information about setting permissions when uploading objects, see [Uploading S3 objects](upload-objects.md)\.

## More Info<a name="set-object-permissions-moreinfo"></a>
+  [Setting bucket and object access permissions](set-permissions.md)
+ [How do I set ACL bucket permissions?](set-bucket-permissions.md)

