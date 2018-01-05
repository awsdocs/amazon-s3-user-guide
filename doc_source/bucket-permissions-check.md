# Identifying Public Buckets Using Bucket Permissions Check<a name="bucket-permissions-check"></a>

Bucket permissions check in the Amazon S3 console checks bucket policies and bucket access control lists \(ACLs\) to identify publicly accessible buckets\. *Publicly accessible* is defined as accessible by either everyone in the world or by any authenticated AWS user\. 

*Access* is defined as the ability to either read or write objects to the buckets, edit bucket permissions, or perform other Amazon S3 operations\. *Reading* a bucket means listing the objects that are stored in the bucket, and *writing* means being able to upload/PUT objects into the bucket\. 

There are two ways that S3 buckets can be made publicly accessible: through bucket policies and ACLs\. For more information about bucket policies, ACLs, and permissions, see [ Managing Access Permissions to Your Amazon S3 Resources](http://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html) in the *Amazon Simple Storage Service Developer Guide*\.

Bucket permissions check does not check object ACLs, which can allow everyone in the world or any authenticated AWS user to access the object and its permissions\. An object can also be publicly accessible through the object's ACLs\. When an object is publicly accessible through the `READ` ACL, it allows access to the contents of the object\. With `READ_ACP` and `WRITE_ACP` ACLs, grantees can also read and modify the object ACLs respectively\.

Bucket permissions check makes it easier to identify S3 buckets that provide public read and write access\. You can also view whether the source for the public access is a bucket policy, a bucket ACL, or both\. If you change a bucket policy or a bucket ACL, the Amazon S3 console analyzes them in real time and alerts you if those changes enable public read and write access on the bucket\.

## Listing Public Buckets<a name="bucket-permissions-check-list"></a>

The List buckets view now shows whether your bucket is publicly accessible\. Amazon S3 labels the permissions for a bucket as follows:

+ **Public** – Publicly accessible by either everyone in the world or by any authenticated AWS user\. 

+ **Not public\*** – The bucket is not publicly accessible\. However, objects in the bucket might be publicly accessible due to object ACLs\. 

+ **Access denied** – Locked out of the bucket\.

+ **Error** – A service\-related error occurred\.

+ **Undetermined**– Amazon S3 cannot determine whether the bucket is publicly accessible\.

To get a list of the public buckets with public read and write access, choose the orange **Public** button next to the number of buckets\.

![\[List buckets view with Public button highlighted at the top.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/list-buckets.png)

You can also get a list with more specific access information\. In the **Search for buckets** bar drop\-down list, choose **Buckets with any public access \(read/write\)**, **Buckets with public read access**, or **Buckets with public write access**\. 

![\[List buckets view with search bar and three options to choose from.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/list-publc-buckets-search.png)

If you choose either the orange **Public** button or **Buckets with any public access \(read/write\)**, you see a list of the public buckets with information about **Read** and **Write** access permissions\. 

To change this list to show only **Read** or only **Write** access permissions, choose the **X** on the **Public:Read** or **Public:Write** buttons that are located above the list\. If you choose the** X** on both, you return to the List all buckets page\.

The **Source** column shows whether the bucket is marked as public because of an **ACL** or a **Bucket policy**, or both\. **ACL** and **Bucket policy** are links—choose the link to view the permissions page, which shows why the bucket is marked public\. You can then change the permission if needed\. For more information on changing ACL and bucket policy permission, see [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md) and [How Do I Add an S3 Bucket Policy?](add-bucket-policy.md)\.

![\[Bucket list showing Public:write and Public: read options, and the ACL and bucket
          policy links.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/list-of-public-read-write.png)

## More Info<a name="bucket-permissions-check-moreinfo"></a>

+ [Setting Bucket and Object Access Permissions](set-permissions.md)

+ [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md)

+  [How Do I Add an S3 Bucket Policy?](add-bucket-policy.md)