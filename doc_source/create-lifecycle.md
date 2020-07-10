# How do I create a lifecycle policy for an S3 Bucket?<a name="create-lifecycle"></a>

You can use lifecycle policies to define actions that you want Amazon S3 to take during an object's lifetime \(for example, transition objects to another storage class, archive them, or delete them after a specified period of time\)\.

You can define a lifecycle policy for all objects or a subset of objects in the bucket by using a shared prefix \(objects names that begin with a common string\) or a tag\. 

Using a lifecycle policy, you can define actions specific to current and noncurrent object versions\. For more information, see [Object Lifecycle Management](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) and [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To create a lifecycle policy**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want to create a lifecycle policy for\.

1. Choose the **Management** tab, and choose **Add lifecycle rule**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-lifecycle-tab.png)

1. In the **Lifecycle rule** dialog box, type a name for your rule\. 

   The name must be unique within the bucket\. 

1. Choose the scope of the lifecycle rule: all objects with a specific prefix or tag or all the objects in the bucket\.
   + To apply this lifecycle rule to *all objects with a specific prefix or tag*, choose **Limit the scope to specific prefixes or tags**\. In the **Add prefix or tag filter** box, type the prefix or tag name, and press **Enter**\.  For more information about object name prefixes, see [Object Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#object-keys) in the *Amazon Simple Storage Service Developer Guide*\.For more information about object tags, see [Object Tagging](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html) in the *Amazon Simple Storage Service Developer Guide*\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-name-scope.png)
   + To apply this lifecycle rule to *all objects in the bucket*, choose **Apply to *all* objects in the bucket**\.

1. Choose **Next**\.

   The **Storage class transition** page opens\. When you configure your storage class transitions, you define the rules to transition objects to the Standard\-IA, One Zone\-IA, Glacier, and Deep Archive storage classes\. For more information, see [Storage Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html) in the *Amazon Simple Storage Service Developer Guide*\. You can define transitions for current or previous object versions or for both current and previous versions\. Versioning enables you to keep multiple versions of an object in one bucket\. For more information about versioning, see [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)\.

1. Choose the versions for which you want to define transitions, current or noncurrent:
   + To define transitions that are applied to the current verion of the object, choose **Current version**\. 
   + To define transitions that are applied to all previous versions of the object, choose **Previous versions**\.

     In the screenshot below, **Current version** is chosen\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-transition-current-version.png)

1. To add a transition: 

   1. For a current version, under **For current object versions**, choose **Add transition**\.

   1. For a non\-current version, under **For non\-current object versions**, choose **Add transition**\.

1. For each transition that you add, choose one of the following:
   + **Transition to Standard\-IA after**\.
   + **Transition to Intelligent\-Tiering after**\. 
   + **Transition to One Zone\-IA after**\. 
   + **Transition to Glacier after**\.
   + **Transition to Glacier Deep Archive after**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-add-transition.png)
**Important**  
When you choose the Glacier or Glacier Deep Archive storage class, your objects remain in Amazon S3\. You cannot access them directly through the separate Amazon S3 Glacier service\. For more information, see [Transitioning Objects Using Amazon S3 Lifecycle](https://docs.aws.amazon.com/AmazonS3/latest/dev/lifecycle-transition-general-considerations.html)\. 

1. In the **Days after creation** box, enter the number of days after the creation of the object that you want the transition to be applied \(for example, 30 or 100 days\)\.

1. When you are done configuring transitions, choose **Next**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-config-transition.png)

1. Under **Configure expiration**, for this example, choose both **Current version** and **Previous versions**\. 
**Important**  
In a non\-versioned bucket the expiration action results in Amazon S3 permanently removing the object\. For more information about lifecycle actions, see [Elements to describe lifecycle actions](https://docs.aws.amazon.com/AmazonS3/latest/dev/intro-lifecycle-rules.html#intro-lifecycle-rules-actions) in the *Amazon Simple Storage Service Developer Guide*\.

1. Choose **Expire current version of object**, and then enter the number of days after object creation to delete the object \(for example, 395 days\)\.

   If you choose this expire option, you cannot choose the option to clean up expired delete markers\. 

1. Choose **Permanently delete previous versions**, and then enter the number of days after an object becomes a previous version to permanently delete the object \(for example, 465 days\)\.

1. To clean up incomplete multipart uploads, we recommend that you choose **Clean up incomplete multipart uploads** and enter the number of days after the multipart upload initiation that you want to end and clean up incomplete multipart uploads\(for example, 7 days\)\. 

   For more information about multipart uploads, see [Multipart Upload Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/mpuoverview.html) in the Amazon Simple Storage Service Developer Guide\.

1. Choose **Next**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-expirations.png)

1. For **Review**, verify the settings for your rule\. If you need to make changes, choose **Previous**\. Otherwise, choose **Save**\. 

   If the rule does not contain any errors, it is enabled and you can see it on the **Lifecycle** page\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-rules-list.png)