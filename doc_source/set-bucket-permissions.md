# How Do I Set ACL Bucket Permissions?<a name="set-bucket-permissions"></a>

This section explains how to use the Amazon Simple Storage Service \(Amazon S3\) console to manage access permissions for S3 buckets by using access control lists \(ACLs\)\. ACLs are resource\-based access policies that grant access permissions to buckets and objects\. For more information about managing access permissions with resource\-based policies, see [Overview of Managing Access](http://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

You can grant permissions to other AWS account users or to predefined groups\. The user or group that you are granting permissions to is called the grantee\. By default, the owner, which is the AWS account that created the bucket, has full permissions\.

Each permission you grant for a user or group adds an entry in the ACL associated with the bucket\. The ACL lists grants, which identify the grantee and the permission granted\. For more information about ACLs, see [Managing Access with ACLs](http://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To set ACL access permissions for an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to set permissions for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Permissions**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-permissions.png)

1. You can manage bucket access permissions for the following: 

   1. 

**Owner access**

      The *owner* refers to the AWS account root user, and not an AWS Identity and Access Management \(IAM\) user\. For more information about the root user, see [The AWS Account Root User](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)\.

      To make changes to the owner's bucket access permissions, under **Owner access**, choose the account name, which is the name of the AWS account root user\.

      Select the check boxes for the permissions that you want to change, and then choose **Save**\.  
![\[Manage owner access\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/bucket-permissions-owner.png)

   1. 

**Access for other AWS accounts**

      To grant permissions to an AWS user from a different AWS account, under **Access for other AWS accounts**, choose **Add account**\. In the **Enter an ID** field, type the canonical ID of the AWS user that you want to grant bucket permissions to\. For information about finding a canonical ID, see [AWS Account Identifiers](http://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) in the *Amazon Web Services General Reference*\. You can add as many as 99 users\.

      Select the check boxes next to the permissions that you want to grant to the user, and then choose **Save**\. To display information about the permissions, choose the Help icons\.   
![\[Help icons\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/bucket-permissions-add-user.png)
**Warning**  
When you grant other AWS accounts access to your resources, be aware that the AWS accounts can delegate their permissions to users under their accounts\. This is known as *cross\-account access*\. For information about using cross\-account access, see [ Creating a Role to Delegate Permissions to an IAM User](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user.html) in the *IAM User Guide*\. 

   1. 

**Public access**

      To grant access to your bucket to the general public \(everyone in the world\), under **Public access**, choose **Everyone**\. Granting public access permissions means that anyone in the world can access the bucket\.

      Select the check boxes for the permissions that you want to grant, and then choose **Save**\.   
![\[Grant public access\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/bucket-permissions-public.png)
**Warning**  
Use caution when granting the **Everyone** group public access to your S3 bucket\. When you grant access to this group, anyone in the world can access your bucket\. We highly recommend that you never grant any kind of public write access to your S3 bucket\.

   1. 

**S3 log delivery group**

      To grant access to Amazon S3 to write server access logs to the bucket, under **S3 log delivery group**, choose **Log Delivery**\.

      If a bucket is set up as the target bucket to receive access logs, the bucket permissions must allow the **Log Delivery** group write access to the bucket\. When you enable server access logging on a bucket, the S3 console grants write access to the **Log Delivery** group for the target bucket that you choose to receive the logs\. For more information about server access logging, see [How Do I Enable Server Access Logging for an S3 Bucket?](server-access-logging.md)\.

You can also set bucket permissions when you are creating a bucket\. For more information on setting permissions when creating a bucket, see [How Do I Create an S3 Bucket?](create-bucket.md)\. 

## More Info<a name="set-bucket-permissions-moreinfo"></a>
+  [Setting Bucket and Object Access Permissions](set-permissions.md)
+ [How Do I Set Permissions on an Object?](set-object-permissions.md)
+ [How Do I Add an S3 Bucket Policy?](add-bucket-policy.md)