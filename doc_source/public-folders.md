# Making Folders Public<a name="public-folders"></a>

You can make a folder public, which means that all of the objects that appear within a public folder in the Amazon S3 console are available for viewing or downloading to anyone on the internet\. However, as described in [How do I use folders in an S3 Bucket?](using-folders.md), the S3 console supports a folder concept as a way to group objects\. If you use a web browser to view a folder that you made public, you will get an access denied error because the folder is just a naming prefix for an object or group of objects\.

**Important**  
Use caution when making a folder public because anyone in the world with access to the internet can view or download the objects in your public folder\. Also, it is easy to make a folder public, but you cannot make a folder private after you make it public\. To make the objects in a public folder private, you must set permissions on each individual object so that the object has no public access\. For more information about how to set an object's permissions, see [How Do I Set Permissions on an Object?](set-object-permissions.md)\.

## More Info<a name="public-folders-moreinfo"></a>
+ [How Do I Delete Folders from an S3 Bucket?](delete-folders.md)
+ [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md)