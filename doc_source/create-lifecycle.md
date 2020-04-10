# How Do I Create a Lifecycle Policy for an S3 Bucket?<a name="create-lifecycle"></a>

You can use lifecycle policies to define actions you want Amazon S3 to take during an object's lifetime \(for example, transition objects to another storage class, archive them, or delete them after a specified period of time\)\.

You can define a lifecycle policy for all objects or a subset of objects in the bucket by using a shared prefix \(that is, objects that have names that begin with a common string\)\. 

A versioning\-enabled bucket can have many versions of the same object, one current version and zero or more noncurrent \(previous\) versions\.  Using a lifecycle policy, you can define actions specific to current and noncurrent object versions\. For more information, see [Object Lifecycle Management](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) and [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To create a lifecycle policy**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to create a lifecycle policy for\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose the **Management** tab, and then choose **Add lifecycle rule**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-lifecycle-tab.png)

1. In the **Lifecycle rule** dialog box, type a name for your rule to help identify the rule later\. The name must be unique within the bucket\. Configure the rule as follows: 
   + To apply this lifecycle rule to all objects with a specified name prefix \(that is, objects with names that begin with a common string\), type a prefix in the box, choose the prefix from the drop\-down list, and then press **Enter**\.  For more information about object name prefixes, see [Object Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#object-keys) in the *Amazon Simple Storage Service Developer Guide*\. 
   + To apply this lifecycle rule to all objects with one or more object tags, type a tag in the box, choose the tag from the drop\-down list, and then press **Enter**\. Repeat the procedure to add another tag\. You can combine a prefix and tags\. For more information about object tags, see [Object Tagging](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html) in the *Amazon Simple Storage Service Developer Guide*\.
**Warning**  
If you do not enter a prefix or tag to limit the scope of your lifecycle rule, it will apply to **all** objects in your bucket\.
   + Choose **Next**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-name-scope.png)

1. You configure lifecycle rules by defining rules to transition objects to the Standard\-IA, One Zone\-IA, Glacier, and Deep Archive storage classes\. For more information, see [Storage Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html) in the *Amazon Simple Storage Service Developer Guide*\.

   You can define transitions for current or previous object versions, or for both current and previous versions\. Versioning enables you to keep multiple versions of an object in one bucket\. For more information about versioning, see [How Do I Enable or Suspend Versioning for an S3 Bucket?](enable-versioning.md)\.

   1. Select **Current version** to define transitions that are applied to the current version of the object\. 

      Select **Previous versions** to define transitions that are applied to all previous versions of the object\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-transition-current-version.png)

   1. Choose **Add transitions** and specify one of the following transitions:
      + Choose **Transition to Standard\-IA after**, and then type the number of days after the creation of an object that you want the transition to be applied \(for example, 30 days\)\. 
      + Choose **Transition to Intelligent\-Tiering after**, and then type the number of days after the creation of an object that you want the transition to be applied \(for example, 30 days\)\. 
      + Choose **Transition to One Zone\-IA after**, and then type the number of days after the creation of an object that you want the transition to be applied \(for example, 30 days\)\. 
      + Choose **Transition to Glacier after**, and then type the number of days after the creation of an object that you want the transition to be applied \(for example, 100 days\)\.
      + Choose **Transition to Glacier Deep Archive after**, and then type the number of days after the creation of an object that you want the transition to be applied \(for example, 100 days\)\.
**Important**  
When you choose the Glacier or Glacier Deep Archive storage class, your objects remain in Amazon S3\. You cannot access them directly through the separate Amazon S3 Glacier service\. For more information, see [Transitioning Objects Using Amazon S3 Lifecycle](https://docs.aws.amazon.com/AmazonS3/latest/dev/lifecycle-transition-general-considerations.html)\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-add-transition.png)

1. When you are done configuring transitions, choose **Next**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-config-transition.png)

1. For this example, select both **Current version** and **Previous versions**\. 

1. Select **Expire current version of object**, and then enter the number of days after object creation to delete the object \(for example, 395 days\)\. If you select this expire option, you cannot select the option to clean up expired delete markers\. 

1. Select **Permanently delete previous versions**, and then enter the number of days after an object becomes a previous version to permanently delete the object \(for example, 465 days\)\.

1. It is a recommended best practice to always select **Clean up incomplete multipart uploads**\. For example, type **7** for the number of days after the multipart upload initiation date that you want to end and clean up any multipart uploads that have not completed\. For more information about multipart uploads, see [Multipart Upload Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/mpuoverview.html) in the Amazon Simple Storage Service Developer Guide\.

1. Choose **Next**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-expirations.png)

1. For **Review**, verify the settings for your rule\. If you need to make changes, choose **Previous**\. Otherwise, choose **Save**\. 

1. If the rule does not contain any errors, it is listed on the **Lifecycle** page and is enabled\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/lifecycle-rules-list.png)