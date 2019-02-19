# Introduction to Amazon S3 Batch Operations<a name="batch-ops"></a>

Amazon S3 batch operations performs large\-scale batch operations on Amazon S3 objects\. You can use Amazon S3 batch operations to copy objects, set object tags or access control lists \(ACLs\), initiate object restores from Amazon S3 Glacier, or invoke an AWS Lambda function to perform custom actions using your objects\. You can perform these operations on a custom list of objects, or you can use an Amazon S3 inventory report to make generating even the largest lists of objects easy\. Batch operations use the same Amazon S3 APIs that you already use, so you'll find the interface familiar\. For information about performing batch operations using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Performing Batch Operations](https://docs.aws.amazon.com/AmazonS3/latest/dev/batch-ops.html) in the *Amazon Simple Storage Service Developer Guide*\. 

The following topics explain how to use the Amazon S3 console to configure and run batch operations\.

**Topics**
+ [Creating a Batch Operations Job](batch-ops-create-job.md)
+ [Managing Batch Operations Jobs](#batch-ops-manage-jobs)

## Managing Batch Operations Jobs<a name="batch-ops-manage-jobs"></a>

Amazon S3 provides a set of tools to help you manage your batch operations jobs after you create them\. For more information about managing batch operations, see [Managing Batch Operations Jobs](https://docs.aws.amazon.com/AmazonS3/latest/dev/batch-ops-managing-jobs.html) in the *Amazon Simple Storage Service Developer Guide*\. 