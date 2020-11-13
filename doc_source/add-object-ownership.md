# Setting S3 Object Ownership to bucket owner preferred in the console<a name="add-object-ownership"></a>

S3 Object Ownership enables you to take ownership of new objects that other AWS accounts upload to your bucket with the `bucket-owner-full-control` canned access control list \(ACL\)\. This section describes how to set Object Ownership using the AWS Management Console\.

**Setting Object Ownership to bucket owner preferred on an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want to enable S3 Object Ownership for\.

1. Choose the **Permissions** tab\.

1. Choose **Edit** under **Object Ownership**\.

1. Choose **Bucket owner preferred**, and then choose **Save**\.

## How do I ensure that I take ownership of new objects?<a name="add-object-ownership-moreinfo"></a>

With the preceding steps, Object Ownership enables you to take ownership of any new objects that are written by other accounts with the `bucket-owner-full-control` canned ACL\. For information about enforcing Object Ownership, see [How do I ensure that I take ownership of new objects?](https://docs.aws.amazon.com/AmazonS3/latest/dev/about-object-ownership.html#ensure-object-ownership) in the *Amazon Simple Storage Service Developer Guide*\.