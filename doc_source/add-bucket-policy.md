# How do I add an S3 Bucket policy?<a name="add-bucket-policy"></a>

This section explains how to use the Amazon Simple Storage Service \(Amazon S3\) console to add a new bucket policy or edit an existing bucket policy\. A bucket policy is a resource\-based AWS Identity and Access Management \(IAM\) policy\. You add a bucket policy to a bucket to grant other AWS accounts or IAM users access permissions for the bucket and the objects in it\. Object permissions apply only to the objects that the bucket owner creates\. For more information about bucket policies, see [Overview of Managing Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

 For examples of Amazon S3 bucket policies, see [Bucket Policy Examples](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) in the *Amazon Simple Storage Service Developer Guide*\. 

**To create or edit a bucket policy**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want to create a bucket policy for or whose bucket policy you want to edit\.

1. Choose **Permissions**\.

1. \(Optional\) Choose **Policy generator** to open the AWS Policy Generator in a new window\. On the policy generator page, select **S3 Bucket Policy** from the **Select Type of Policy** dropdown menu\. Add one or more statements by populating the fields presented, and then choose **Generate Policy**\. Copy the generated policy text and return to the **Edit bucket policy** page in the Amazon S3 console\.

1. Under **Bucket policy**, choose **Edit**\.

1. In the **Policy** text field, type or copy and paste a new bucket policy, or edit an existing policy\. The bucket policy is a JSON file\. The text you type in the editor must be valid JSON\.
**Note**  
For convenience, the console displays the Amazon Resource Name \(ARN\) of the current bucket above the **Policy** text field\. You can copy this ARN for use in the policy\. For more information about ARNs, see [Amazon Resource Names \(ARNs\) and AWS Service Namespaces](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) in the *Amazon Web Services General Reference*\.

1. Choose **Save**\.

## More info<a name="add-bucket-policy-moreinfo"></a>
+ [Setting bucket and object access permissions](set-permissions.md)
+ [How do I set ACL bucket permissions?](set-bucket-permissions.md)