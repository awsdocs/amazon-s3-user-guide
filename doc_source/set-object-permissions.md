# How do I set permissions on an object?<a name="set-object-permissions"></a>

This section explains how to use the Amazon Simple Storage Service \(Amazon S3\) console to manage access permissions for an Amazon S3 object by using access control lists \(ACLs\)\. ACLs are resource\-based access policies that grant access permissions to buckets and objects\. For more information about managing access permissions with resource\-based policies, see [Overview of Managing Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

Bucket and object permissions are independent of each other\. An object does not inherit the permissions from its bucket\. For example, if you create a bucket and grant write access to a user, you can't access that user’s objects unless the user explicitly grants you access\.

You can grant permissions to other AWS accounts or predefined groups\. The user or group that you grant permissions to is called the *grantee*\. By default, the owner, which is the AWS account that created the bucket, has full permissions\.

Each permission you grant for a user or a group adds an entry in the ACL that is associated with the object\. The ACL lists grants, which identify the grantee and the permission granted\. For more information about ACLs, see [Managing Access with ACLs](https://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To set permissions for an object**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the object\.  
![\[Screenshot showing bucket name list with "admin-created" bucket highlighted.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, choose the name of the object for which you want to set permissions\.  
![\[Console screenshot showing choosing an object name.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-name-select.png)

1. Choose **Permissions**\.

1. You can manage object access permissions for the following: 

   1. 

**Access for object owner**

      The *owner* refers to the AWS account root user, and not an AWS Identity and Access Management \(IAM\) user\. For more information about the root user, see [The AWS Account Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html) in the *IAM User Guide*\.

      To change the owner's object access permissions, under **Access for object owner**, choose **Your AWS Account \(owner\)**\.

      Select the check boxes for the permissions that you want to change, and then choose **Save**\.  
![\[Screenshot showing permissions check boxes for account owner.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-permissions-owner.png)

   1. 

**Access for other AWS accounts**

      To grant permissions to an AWS user from a different AWS account, under **Access for other AWS accounts**, choose **Add account**\. In the **Enter an ID** field, enter the canonical ID of the AWS user that you want to grant object permissions to\. For information about finding a canonical ID, see [AWS Account Identifiers](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) in the *Amazon Web Services General Reference*\. You can add as many as 99 users\.

      Select the check boxes for the permissions that you want to grant to the user, and then choose **Save**\. To display information about the permissions, choose the Help icons\.   
![\[Console screenshot showing Help icon and tooltip.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-permissions-add-user.png)

   1. 

**Public access**

      To grant access to your object to the general public \(everyone in the world\), under **Public access**, choose **Everyone**\. Granting public access permissions means that anyone in the world can access the object\.

      Select the check boxes for the permissions that you want to grant, and then choose **Save**\.   
![\[Screenshot showing that everyone will have access to the object.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-permissions-public.png)
**Warning**  
Use caution when granting the **Everyone** group anonymous access to your Amazon S3 objects\. When you grant access to this group, anyone in the world can access your object\. If you need to grant access to everyone, we highly recommend that you only grant permissions to **Read objects**\.  
We highly recommend that you *do not* grant the **Everyone** group write object permissions\. Doing so allows anyone to overwrite the ACL permissions for the object\.

You can also set object permissions when you upload objects\. For more information about setting permissions when uploading objects, see [How do I upload files and folders to an S3 bucket?](upload-objects.md)\. 

## More Info<a name="set-object-permissions-moreinfo"></a>
+  [Setting bucket and object access permissions](set-permissions.md)
+ [How do I set ACL bucket permissions?](set-bucket-permissions.md)