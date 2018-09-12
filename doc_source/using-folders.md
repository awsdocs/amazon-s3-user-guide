# How do I use folders in an S3 Bucket?<a name="using-folders"></a>

In Amazon S3, buckets and objects are the primary resources, where objects are stored in buckets\. Amazon S3 has a flat structure with no hierarchy like you would see in a file system\. However, for the sake of organizational simplicity, the Amazon S3 console supports the folder concept as a means of grouping objects\. Amazon S3 does this by using a shared name prefix for objects \(that is, objects that have names that begin with a common string\)\. Object names are also referred to as key names\.

For example, you can create a folder in the console called `photos`, and store an object named `myphoto.jpg` in it\. The object is then stored with the key name `photos/myphoto.jpg`, where `photos/` is the prefix\.

Here are two more examples: 
+ If you have three objects in your bucket—`logs/date1.txt`, `logs/date2.txt`, and `logs/date3.txt`—the console will show a folder named `logs`\. If you open the folder in the console, you will see three objects: `date1.txt`, `date2.txt`, and `date3.txt`\.
+ If you have an object named `photos/2017/example.jpg`, the console will show you a folder named `photos` containing the folder `2017` and the object `example.jpg`\.

**Topics**
+ [Creating a Folder](create-folder.md)
+ [How Do I Delete Folders from an S3 Bucket?](delete-folders.md)
+ [Making Folders Public](public-folders.md)

You can have folders within folders, but not buckets within buckets\. You can upload and copy objects directly into a folder\. Folders can be created, deleted, and made public, but they cannot be renamed\. Objects can be copied from one folder to another\. 

**Important**  
 The Amazon S3 console treats all objects that have a forward slash "/" character as the last \(trailing\) character in the key name as a folder, for example `examplekeyname/`\. You cannot upload an object with a key name with a trailing "/" character by using the Amazon S3 console\. However, objects named with a trailing "/" can be uploaded with the Amazon S3 API by using the AWS CLI, the AWS SDKs, or REST API\.   
An object named with a trailing "/" displays as a folder in the Amazon S3 console\. The Amazon S3 console does not display the content and metadata for such an object\. When copying an object named with a trailing "/" by using the Amazon S3 console, a new folder is created in the destination location but the object's data and metadata are not copied\. 