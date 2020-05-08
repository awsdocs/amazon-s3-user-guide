# How do I block public access to S3 buckets?<a name="block-public-access"></a>

Amazon S3 block public access prevents the application of any settings that allow public access to data within S3 buckets\. You can configure block public access settings for an individual S3 bucket or for all the buckets in your account\. For information about blocking public access using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Using Amazon S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) in the *Amazon Simple Storage Service Developer Guide*\.

The following topics explain how to use the Amazon S3 console to configure block public access settings: 
+ [How do I edit public access settings for S3 buckets?](block-public-access-bucket.md)
+ [How do I edit public access settings for all the S3 buckets in an AWS account?](block-public-access-account.md)

The following sections explain viewing bucket access status and searching by access types\.

## Viewing access status<a name="block-public-access-list"></a>

The list buckets view shows whether your bucket is publicly accessible\. Amazon S3 labels the permissions for a bucket as follows:
+ **Public** – Everyone has access to one or more of the following: List objects, Write objects, Read and write permissions\. 
+ **Objects can be public** – The bucket is not public, but anyone with the appropriate permissions can grant public access to objects\. 
+ **Buckets and objects not public** – The bucket and objects do not have any public access\.
+ **Only authorized users of this account** – Access is isolated to IAM users and roles in this account and AWS service principals because there is a policy that grants public access\.

The access column shows the access status of the listed buckets\.

![\[Console screenshot of list buckets view showing access status.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/bucket-access-status.png)

You can also filter bucket searches by access type\. Choose an access type from the drop\-down list that is next to the **Search for buckets** bar\. 

![\[Console screenshot showing how to search for S3 buckets by access type.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/search-by-access-type.png)

## More info<a name="block-public-access-moreinfo"></a>
+  [How do I edit public access settings for S3 buckets?](block-public-access-bucket.md)
+ [How do I edit public access settings for all the S3 buckets in an AWS account?](block-public-access-account.md)
+ [Setting bucket and object access permissions](set-permissions.md)