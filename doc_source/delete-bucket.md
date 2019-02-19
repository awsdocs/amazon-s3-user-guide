# How Do I Delete an S3 Bucket?<a name="delete-bucket"></a>

You can delete an empty bucket, and when you're using the AWS Management Console, you can delete a bucket that contains objects\. If you delete a bucket that contains objects, all the objects in the bucket are permanently deleted\. 

When you delete a bucket with versioning enabled, all versions of all the objects in the bucket are permanently deleted\. For more information about versioning, see [Managing Objects in a Versioning\-Enabled Bucket](https://docs.aws.amazon.com/AmazonS3/latest/dev/manage-objects-versioned-bucket.html) in the *Amazon Simple Storage Service Developer Guide*\.

Before deleting a bucket, consider the following:
+ Bucket names are unique\. If you delete a bucket, another AWS user can use the name\. 
+ When you delete a bucket that contains objects, all the objects in the bucket are permanently deleted, including objects that transitioned to the Amazon S3 `Glacier` storage class\.
+ If the bucket hosts a static website, and you created and configured an Amazon Route 53 hosted zone as described in [ Create and Configure Amazon Route 53 Hosted Zone](https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html#root-domain-walkthrough-switch-to-route53-as-dnsprovider): You must clean up the Route 53 hosted zone settings that are related to the bucket as described in [ Delete the Route 53 Hosted Zone](https://docs.aws.amazon.com/AmazonS3/latest/dev/getting-started-cleanup.html#getting-started-cleanup-route53)\.
+ If the bucket receives log data from Elastic Load Balancing \(ELB\): We recommend that you stop the delivery of ELB logs to the bucket before deleting it\. After you delete the bucket, if another user creates a bucket using the same name, your log data could potentially be delivered to that bucket\. For information about ELB access logs, see [Access Logs](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/access-log-collection.html) in the *User Guide for Classic Load Balancers* and [Access Logs](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.html) in the *User Guide for Application Load Balancers*\.

**Important**  
If you want to continue to use the same bucket name, don't delete the bucket\. We recommend that you empty the bucket and keep it\. After a bucket is deleted, the name becomes available to reuse, but the name might not be available for you to reuse for various reasons\. For example, it might take some time before the name can be reused, and some other account could create a bucket with that name before you do\.

**To delete an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the bucket icon next to the name of the bucket that you want to delete and then choose **Delete bucket**\.  
![\[Delete bucket highlighted.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/delete-bucket.png)

1. In the **Delete bucket** dialog box, type the name of the bucket that you want to delete for confirmation, and then choose **Confirm**\. 
**Note**  
The text in the dialog box changes depending on whether the bucket is empty, is used for a static website, or is used for ELB access logs\.  
![\[Delete bucket highlighted.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/delete-bucket-confirm.png)

## More Info<a name="delete-bucket-moreinfo"></a>
+ [How Do I Empty an S3 Bucket?](empty-bucket.md)
+ [How Do I Delete Objects from an S3 Bucket?](delete-objects.md)