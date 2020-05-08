# How do I add an S3 Bucket policy?<a name="add-bucket-policy"></a>

This section explains how to use the Amazon Simple Storage Service \(Amazon S3\) console to add a new bucket policy or edit an existing bucket policy\. A bucket policy is a resource\-based AWS Identity and Access Management \(IAM\) policy\. You add a bucket policy to a bucket to grant other AWS accounts or IAM users access permissions for the bucket and the objects in it\. Object permissions apply only to the objects that the bucket owner creates\. For more information about bucket policies, see [Overview of Managing Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

 For examples of Amazon S3 bucket policies, see [Bucket Policy Examples](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) in the *Amazon Simple Storage Service Developer Guide*\. 

**To create or edit a bucket policy**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to create a bucket policy for or whose bucket policy you want to edit\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Permissions**, and then choose **Bucket Policy**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-permissions-bucket-policy.png)

1. In the **Bucket policy editor** text box, type or copy and paste a new bucket policy, or edit an existing policy\. The bucket policy is a JSON file\. The text you type in the editor must be valid JSON\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/bucket-policy-example.png)

1. Choose **Save**\.
**Note**  
Amazon S3 displays the Amazon Resource Name \(ARN\) for the bucket next to the **Bucket policy editor** title\. For more information about ARNs, see [Amazon Resource Names \(ARNs\) and AWS Service Namespaces](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) in the *Amazon Web Services General Reference*\.  
Directly below the bucket policy editor text box is a link to the **Policy Generator**, which you can use to create a bucket policy\.

## More info<a name="add-bucket-policy-moreinfo"></a>
+ [Setting bucket and object access permissions](set-permissions.md)
+ [How do I set ACL bucket permissions?](set-bucket-permissions.md)