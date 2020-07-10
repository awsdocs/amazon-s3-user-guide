# Making folders public<a name="public-folders"></a>

Amazon S3 has a flat structure instead of a hierarchy like you would typically see in a file system\. However, for the sake of organizational simplicity, the Amazon S3 console supports a folder concept as a way to group objects\. In Amazon S3, the folder is a naming prefix for an object or group of objects\. For more information, see [How do I use folders in an S3 bucket?](using-folders.md)

We recommend blocking all public access to your Amazon S3 folders and buckets unless you specifically require a public folder or bucket\. When you make a folder public, anyone on the internet can view all the objects that are grouped in that folder\. In the Amazon S3 console, you can make a folder public\. You can also make a folder public by creating a bucket policy that limits access by prefix\. For more information, see [Setting bucket and object access permissions](set-permissions.md)\. 

**Warning**  
After you make a folder public in the Amazon S3 console, you can't make it private again\. Instead, you must set permissions on each individual object in the public folder so that the objects have no public access\. For more information, see [How do I set permissions on an object?](set-object-permissions.md)

## More info<a name="public-folders-moreinfo"></a>
+ [How do I delete folders from an S3 bucket?](delete-folders.md)
+ [How do I set ACL bucket permissions?](set-bucket-permissions.md)
+ [How do I block public access to S3 buckets?](block-public-access.md)