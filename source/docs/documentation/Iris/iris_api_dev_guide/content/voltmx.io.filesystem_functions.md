---
layout: "documentation"
category: "iris_api_dev_guide"
---
                            


voltmx.io.FileSystem Namespace
============================

The voltmx.io.FileSystem namespace includes APIs to create, read, and navigate through the device file system.

Information about the voltmx.io.FileSystem namespace is presented in the following topic.

Functions
---------

The voltmx.io.FileSystem namespace contains the following functions.

### voltmx.io.FileSystem.browse

This API provides the ability to browse and select files from your local system.

Syntax

{% highlight voltMx %}voltmx.io.FileSystem.browse(browseConfig,browseCallBack);
{% endhighlight %}

Input Parameters

  
| Parameter | Description |
| --- | --- |
| browseConfig \[String\] - Mandatory | Configuration params which is a simple JSON object of key value pairs, that drive the possible options during the browse. Currently the following keys are supported in the configuration:**selectMultipleFiles**: (Boolean) - Default (true)**filter**: An array indicates what file Filters should be applied to the file selection dialog. The file Filters need to follow the conventions specified in the IANAMediaTypes specification. For more information, see [http://www.iana.org/assignments/media-types/media-types..html](http://www.iana.org/assignments/media-types/media-types..html). |
| browseCallBack \[Object\] - Mandatory |   |

 

Example

{% highlight voltMx %}function selectBtn_onClick_seq0() { // Event on button click
    var config = {
        selectMultipleFiles: true,
        filter: ["image/png", "image/jpeg"]
    };
    voltmx.io.FileSystem.browse(config, selectedFileCallback);
}
{% endhighlight %}

Return Values

None.

Platform Availability

*   Desktop Web only

### voltmx.io.FileSystem.copyBundledRawFileTo

This API copies a bundled file from the application binary to the specified destination path on the device. While copying the pre-bundled file, the destination file name can be different from the source.

Syntax

voltmx.io.FileSystem.copyBundledRawFileTo (String rawFileName, String destFilePath)

Input Parameters

| Parameter | Description |
| --- | --- |
| rawFileName \[String\] | Specify the file name with the extension of a pre-bundled raw file that you want to copy. |
| destFilePath \[String\] | Specify the absolute file path along with the file name and extension (if any) where you want to copy the pre-bundled file. In this parameter, the destination file name can be different from the source. |

 

Example

{% highlight voltMx %}//The destination file name can be different from the source.
var destFilePath = voltmx.io.FileSystem.getDataDirectoryPath() + "/Destinationfile.pdf";
var fileObj = null;
try {    
    var file = new voltmx.io.File(destFilePath);    
    //copyBundledRawFileTo API overrides the destination file with new one.   
    //Hence check before copying    
    if (!file.exists()) {      
        var fileObj = voltmx.io.FileSystem.copyBundledRawFileTo(“Sourcefile.pdf”, destFilePath);    
    } else {     
        fileObj = file;      
        alert("File is already available");     
        return;    
    }
} catch (e) {    
    voltmx.print(“Exception“ + e);
}
{% endhighlight %}

Remarks

*   When the app functionality is tested in functional preview application, the voltmx.io.FileSystem.copyBundledRawFileTo API looks for the file in the child app (Downloaded test application). If not found, searches for the same file in the parent app (Functional Preview application).
*   The voltmx.io.FileSystem.copyBundledRawFileTo API overrides the destination file with new one if any file exists with the same name at the destination path.

For more information about bundling the files in the application binary, refer to the Pre bundling the Files topic.

Return Values

VoltMX.io.File returns a handle to the File object pointing to the destination file, if successful. If failure, then throws appropriate exception.

Exceptions

| Error Code | Error Message |
| --- | --- |
| 100 | Source file not found. |
| 100 | Invalid Destination. |
| 101 | Invalid number of arguments. |
| 106 | Unknown error. |

 

Platform Availability

*   iOS
*   Android
*   Windows

### voltmx.io.FileSystem.getAppGroupDirectoryPath

This API retrieves the root path of an app group.

Syntax

voltmx.io.FileSystem.getAppGroupDirectoryPath(  
    appGroupID)

Parameters

| Parameter | Description |
| --- | --- |
| appGroupID | Holds a string containing the unique ID of the app group. |

 

Example

{% highlight voltMx %}var appGroupPath = voltmx.io.FileSystem.getAppGroupDirectoryPath("String");
{% endhighlight %}

Return Values

A string containing the fully-qualified path to the root directory of the app group.

Platform Availability

*   iOS only

### voltmx.io.FileSystem.getApplicationDirectoryPath

The getApplicationDirectoryPath API returns the application directory path.

Syntax

voltmx.io.FileSystem.getApplicationDirectoryPath()

Input Parameters

None

Example

{% highlight voltMx %}var appDirectoryPath = voltmx.io.FileSystem.getApplicationDirectoryPath();
{% endhighlight %}

Return Values

String

Exceptions

None

Platform Availability

*   iOS only

### voltmx.io.FileSystem.getCacheDirectoryPath

The getCacheDirectoryPath API returns the application's cache directory path.

Syntax

voltmx.io.FileSystem.getCacheDirectoryPath()

Input Parameters

None

Example

{% highlight voltMx %}var cacheDirectoryPath = voltmx.io.FileSystem.getCacheDirectoryPath();
{% endhighlight %}

Return Values

String

Exceptions

None

Platform Availability

*   All native platforms
*   Desktop Web

### voltmx.io.FileSystem.getDatabaseDirectoryPath

This API returns the application's database directory path (from application's private file system) where [voltmx.db](voltmx.db_functions.html) APIs access the database files.

This API is useful in accessing the pre-bundled SQLite database file. You need to copy the pre-bundled database file to the directory path returned by the voltmx.io.FileSystem.getDatabaseDirectoryPath API, using the voltmx.io.FileSystem.copyBundledRawFileTo API. You can then use the [voltmx.db.openDatabase](voltmx.db_functions.html#volt-mx-db-opendatabase) API to open the SQLite database files after copying.

Syntax

voltmx.io.FileSystem.getDatabaseDirectoryPath()

Input Parameters

None

Example

{% highlight voltMx %}//Example for opening the pre-bundled database
//The destination file name can be different from the source.
var destFilePath = voltmx.io.FileSystem.getDatabaseDirectoryPath() + ”test.db”;
var fileObj = null;
try {    
    var file = new voltmx.io.File(destFilePath);    
    //copyBundledRawFileTo API overrides the destination file with new one.    
    //Hence check before copying    
    if (!file.exists()) {      
        fileObj = voltmx.io.FileSystem.copyBundledRawFileTo(dbName, destFilePath);    
    } else {      
        fileObj = file;      
        alert("File is already available");      
        return;    
    }
} catch (e) {    
    voltmx.print(“Exception“ + e);  
}  
if (fileObj == null) {   
    voltmx.print(“Copy failed”);  
} else {   
    voltmx.print(“Copy Success”); 
}
dbObject = voltmx.db.openDatabase("test.db", "1.0", "Prebundled SQL Database", 5 * 1024 * 1024);  

{% endhighlight %}

Return Values

Application's database directory path in the form of String.

Remarks

For Functional Preview, the path returned by the getDatabaseDirectoryPath API points to the child application on your device. This feature is available on iOS, Android, and Windows devices.

Exceptions

None

Platform Availability

*   iOS
*   Android
*   Windows

### voltmx.io.FileSystem.getDataDirectoryPath

This API returns the application’s data directory path.

Syntax

voltmx.io.FileSystem.getDataDirectoryPath()

Input Parameters

None

Example

{% highlight voltMx %}var dataDirectoryPath = voltmx.io.FileSystem.getDataDirectoryPath();
{% endhighlight %}

Return Values

String

Remarks

For Functional Preview, the path returned by the getDataDirectoryPath API points to the child application on your device. This feature is available on iOS, Android, and Windows devices.

Exceptions

None

Platform Availability

*   Applicable for all native platforms, except Desktop Web

### voltmx.io.FileSystem.getExternalCacheDir

The getExternalCacheDir API returns the absolute path to the directory on the primary shared or external storage device where the application can store its cached files.

Syntax

voltmx.io.FileSystem.getExternalCacheDir();

Example

{% highlight voltMx %}var dirPath = voltmx.io.FileSystem.getExternalCacheDir();
{% endhighlight %}

Return Values

String

> **_Note:_** If the shared storage is not available, this API returns a  `null` value.

Exceptions

None

Platform Availability

*   Android

### voltmx.io.FileSystem.getExternalCacheDirs

The getExternalCacheDirs API returns the absolute paths to the application-specific directories on all the shared or external storage devices where the application can store its cached files.

Syntax

voltmx.io.FileSystem.getExternalCacheDirs();

Example

{% highlight voltMx %}var dirPath = voltmx.io.FileSystem.getExternalCacheDirs();
{% endhighlight %}

Return Values

Array of Strings

> **_Note:_** If the shared storage is not available, this API returns a  `null` value.

Exceptions

None

Platform Availability

*   Android

> **_Note:_** If your device runs on Android versions before Android KitKat, the voltmx.io.FileSystem.getExternalFilesDirs API returns the same result as the voltmx.io.FileSystem.getExternalFilesDir API.

### voltmx.io.FileSystem.getExternalFilesDir

The getExternalFilesDir API returns the absolute path to the directory on the primary shared or external storage device where the application can store its persistent files.

> **_Note:_**  

*   From API level 29, apps do not require additional permissions to read and write files to this directory.   
*   The files in this directory are internal to the application, and are deleted when you uninstall the app.

Syntax

voltmx.io.FileSystem.getExternalFilesDir([type](#type));

Input Parameters

| Parameters | Description |
| --- | --- |
| type | The type of file directory to return. The **type** can have one of the following values:`voltmx.io.FileSystem.DIRECTORY_MUSIC``voltmx.io.FileSystem.DIRECTORY_PODCASTS``voltmx.io.FileSystem.DIRECTORY_ALARMS``voltmx.io.FileSystem.DIRECTORY_RINGTONES``voltmx.io.FileSystem.DIRECTORY_NOTIFICATIONS``voltmx.io.FileSystem.DIRECTORY_PICTURES``voltmx.io.FileSystem.DIRECTORY_MOVIES`> **_Note:_** If you provide null or invalid values for the type, the API returns the main directory path of the primary shared or external storage. |

Example

{% highlight voltMx %}var dirPath = voltmx.io.FileSystem.getExternalFilesDir(voltmx.io.FileSystem.DIRECTORY_PICTURES);
{% endhighlight %}

Return Values

String

> **_Note:_** If the shared storage is not available, this API returns a  `null` value.

Exceptions

None

Platform Availability

*   Android

### voltmx.io.FileSystem.getExternalFilesDirs

The getExternalFilesDirs API returns the absolute paths to the application-specific directories on all the shared or external storage devices where the application can store its persistent files.

> **_Note:_**  

*   From API level 29, apps do not require additional permissions to read and write files to this directory.   
*   The files in this directory are internal to the application, and are deleted when you uninstall the app.

Syntax

voltmx.io.FileSystem.getExternalFilesDirs([type](#type1));

Input Parameters

| Parameters | Description |
| --- | --- |
| type | The type of file directory to return. The **type** can have one of the following values:`voltmx.io.FileSystem.DIRECTORY_MUSIC``voltmx.io.FileSystem.DIRECTORY_PODCASTS``voltmx.io.FileSystem.DIRECTORY_ALARMS``voltmx.io.FileSystem.DIRECTORY_RINGTONES``voltmx.io.FileSystem.DIRECTORY_NOTIFICATIONS``voltmx.io.FileSystem.DIRECTORY_PICTURES``voltmx.io.FileSystem.DIRECTORY_MOVIES`> **_Note:_** If you provide null or invalid values for the type, the API returns the main directory path of the primary shared or external storage. |

Example

{% highlight voltMx %}var dirPath = voltmx.io.FileSystem.getExternalFilesDirs(voltmx.io.FileSystem.DIRECTORY_PICTURES);
{% endhighlight %}

Return Values

Array of Strings

> **_Note:_** If the shared storage is not available, this API returns a  `null` value.

Exceptions

None

Platform Availability

*   Android

> **_Note:_** If your device runs on Android versions before Android KitKat, the voltmx.io.FileSystem.getExternalFilesDirs API returns the same result as the voltmx.io.FileSystem.getExternalFilesDir API.

### voltmx.io.FileSystem.getExternalStorageDirectoryPath

The getExternalStorageDirectoryPath API returns the path to the external storage, typically sdcard.

Syntax

voltmx.io.FileSystem.getExternalStorageDirectoryPath()

Input Parameters

None

Example

{% highlight voltMx %}var mainLoc = voltmx.io.FileSystem.getExternalStorageDirectoryPath();
{% endhighlight %}

Return Values

String

Exceptions

None

Platform Availability

*   Android

> **_Note:_** If the targetSdk version used is above version 28, scoped storage is enabled by default, and the legacy Storage APIs (getExternalStorageDirectoryPath) will not work. You must use scoped Storage APIs such as [getExternalFilesDir](#volt-mx-io-filesystem-getexternalfilesdir) and [getExternalFilesDirs](#volt-mx-io-filesystem-getexternalfilesdirs) on devices that run on Android version 11, and above.

### voltmx.io.FileSystem.getExternalStorageState

The getExternalStorageState API returns the current state of the shared or external storage media at the specified path.

Syntax

voltmx.io.FileSystem.getExternalStorageState([path](#Path1));

Input Parameters

| Parameters | Description |
| --- | --- |
| Path | Path to the file or directory. |

 

Example

{% highlight voltMx %}var path = voltmx.io.FileSystem.getExternalFilesDir();  
var stats = voltmx.io.FileSystem.getExternalStorageState(path);
{% endhighlight %}

Return Values

File System Constant

The **File System Constant** can have one of the following values:

`voltmx.io.FileSystem.MEDIA_UNKNOWN`: Unknown storage state, such as when a path isn't backed by known storage media.

`voltmx.io.FileSystem.MEDIA_REMOVED`: Storage state if the media is not present.

`voltmx.io.FileSystem.MEDIA_UNMOUNTED`: Storage state if the media is present but not mounted.

`voltmx.io.FileSystem.MEDIA_CHECKING`: Storage state if the media is present and the disk is being checked.

`voltmx.io.FileSystem.MEDIA_NOFS`: Storage state if the media is present but is blank or is using an unsupported filesystem.

`voltmx.io.FileSystem.MEDIA_MOUNTED`: Storage state if the media is present and mounted at its mount point with read/write access.

`voltmx.io.FileSystem.MEDIA_MOUNTED_READ_ONLY`: Storage state if the media is present and mounted at its mount point with read/write access.

`voltmx.io.FileSystem.MEDIA_SHARED`: Storage state if the media is present not mounted, and shared via USB mass storage.

`voltmx.io.FileSystem.MEDIA_BAD_REMOVAL`: Storage state if the media was removed before it was unmounted.

`voltmx.io.FileSystem.MEDIA_UNMOUNTABLE`: Storage state if the media is present but cannot be mounted. Typically, this happens if the file system on the media is corrupted.

`voltmx.io.FileSystem.MEDIA_EJECTING`: Storage state if the media is in the process of being ejected.

Exceptions

None

Platform Availability

*   Android

### voltmx.io.FileSystem.getFile

The getFile API returns a voltmx.io.File object representing the file for the given path. It returns a voltmx.io.File object for the specified file path. getFile API does not create a File.

Syntax

voltmx.io.FileSystem.getFile(string path)

Input Parameters

| Parameters | Description |
| --- | --- |
| Path | path to the file or directory. |

 

Example

{% highlight voltMx %}var mainLoc = voltmx.io.FileSystem.getDataDirectoryPath();
var myFileLoc = mainLoc + constants.FILE_PATH_SEPARATOR + "myFileToGet.txt";
var myFile = new voltmx.io.File(myFileLoc).createFile();
var getMyFile = voltmx.io.FileSystem.getFile(myFileLoc);
if (getMyFile === null) {
    alert("getting File failed with null");
} else {
    alert(JSON.stringify(getMyFile.name));
}
{% endhighlight %}

Return Values

VoltMX.io.File

Platform Availability

*   All native platforms
*   Desktop Web

### voltmx.io.FileSystem.getFileSystemStats

The getFileSystemStats API retrieves the detailed information about the space on a file system.

Syntax

voltmx.io.FileSystem.getFileSystemStats([path](#Path));

Input Parameters

| Parameters | Description |
| --- | --- |
| Path | Path to the file or directory. |

Example

{% highlight voltMx %}var path = voltmx.io.FileSystem.getExternalFilesDir();  
var stats = voltmx.io.FileSystem.getFileSystemStats(path);
{% endhighlight %}

Return Values

A **JSON Object** that contains the values for the following parameters

`freeBytes`: Number of bytes that are free, including reserved blocks, on the file system.

`availableBytes`: Number of bytes that are free and available to applications on the file system.

`totalBytes`: Total number of bytes supported by the file system.

> **_Note:_** If the file path does not exist, this API returns a  `null` value.  
On devices that run Android version 18 (or earlier), the value for totalBytes parameter is not returned.

Exceptions

None

Platform Availability

*   Android

### voltmx.io.FileSystem.getNoBackupFilesDir

The getNoBackupFilesDirAPI returns the absolute path to the directory on the file system that is similar to the [voltmx.io.FileSystem.getDataDirectoryPath](#volt-mx-io-filesystem-getdatadirectorypath) API. However, the files present in the directory returned by this API are excluded during the automatic backup process to the remote storage.

Syntax

voltmx.io.FileSystem.getNoBackupFilesDir();

Input Parameters

None

Example

{% highlight voltMx %}var dirPath = voltmx.io.FileSystem.getNoBackupFilesDir();
{% endhighlight %}

Return Values

String

Exceptions

None

Platform Availability

*   Android

### voltmx.io.FileSystem.getRawDirectoryPath

The getRawDirectoryPath API returns the application’s “raw” directory path. getRawDirectoryPath API API is applicable only on Android.

Syntax

voltmx.io.FileSystem.getRawDirectoryPath()

Input Parameters

None

Example

{% highlight voltMx %}var rawDirectoryPath =  voltmx.io.FileSystem.getRawDirectoryPath();
{% endhighlight %}

Return Values

Returns the directory path in the form of String.

Exceptions

None

Remarks

> **_Note:_** In the Android platform, you should not perform read and write operations to the raw directory.

Platform Availability

*   Android
*   iOS

### voltmx.io.FileSystem.getSupportDirectoryPath

This API returns the application’s support directory path. This is only applicable for iOS.

Syntax

voltmx.io.FileSystem.getSupportDirectoryPath()

Input Parameters

None

Example

{% highlight voltMx %}var supportDirectoryPath = voltmx.io.FileSystem.getSupportDirectoryPath();
{% endhighlight %}

Return Values

String

Remarks

For Functional Preview, the path returned by the getSupportDirectoryPath API points to the child folder present inside the Application Support folder. This feature is available only on iOS devices.

Exceptions

None

Platform Availability

*   iOS

### voltmx.io.FileSystem.isExternalStorageAvailable

The isExternalStorageAvailable API is used to check, if the external storage is available and accessible on the device. The isExternalStorageAvailable API returns boolean value as true/false accordingly on Android platform.

Syntax

voltmx.io.FileSystem.isExternalStorageAvailable()

Input Parameters

None

Example

{% highlight voltMx %}var isExternalStorageAvialable = voltmx.io.FileSystem.isExternalStorageAvailable();
{% endhighlight %}

Return Values

Boolean

Exceptions

None

Platform Availability

*   iOS
*   Android
*   Windows

### voltmx.io.FileSystem.isExternalStorageEmulated

The isExternalStorageEmulated API is used to check if the primary shared or external storage media is emulated. The isExternalStorageAvailable API returns a boolean value as true/false accordingly.

Syntax

voltmx.io.FileSystem.isExternalStorageEmulated([File](#File))

Input Parameters

| Parameters | Description |
| --- | --- |
| File | File Object or path to the file. |

 

Example

{% highlight voltMx %}var dirPath = voltmx.io.FileSystem.getExternalFilesDirs(voltmx.io.FileSystem.DIRECTORY_PICTURES);
var isEmulated = voltmx.io.FileSystem.isExternalStorageEmulated(dirPath);
{% endhighlight %}

Return Values

Boolean

Exceptions

None

Platform Availability

*   Android

> **_Note:_** If this API is invoked on a device that runs on Android version KitKat, it always returns a  `false` value.

### voltmx.io.FileSystem.isExternalStorageLegacy

The isExternalStorageLegacy API is used to check if the primary shared or external storage media at the specified path is from the legacy view and includes files that are not specific to the app. The isExternalStorageLegacy API returns a boolean value as true/false accordingly.

Syntax

voltmx.io.FileSystem.isExternalStorageLegacy([File](#File2))

Input Parameters

| Parameters | Description |
| --- | --- |
| File | File Object or path to the file. |

 

Example

{% highlight voltMx %}var dirPath = voltmx.io.FileSystem.getExternalFilesDirs(voltmx.io.FileSystem.DIRECTORY_PICTURES);
var isLegacy = voltmx.io.FileSystem.isExternalStorageLegacy(dirPath);
{% endhighlight %}

Return Values

Boolean

Exceptions

None

Platform Availability

*   Android

> **_Note:_** If this API is invoked on a device that runs on Android versions prior to Android Q, it always returns a  `true` value.

### voltmx.io.FileSystem.isExternalStorageRemovable

The isExternalStorageRemovable API is used to check if the primary shared or external storage media at the specified path is physically removable. The isExternalStorageRemovable API returns a boolean value as true/false accordingly.

Syntax

voltmx.io.FileSystem.isExternalStorageRemovable([File](#File1))

Input Parameters

| Parameters | Description |
| --- | --- |
| File | File Object or path to the file. |

 

Example

{% highlight voltMx %}var dirPath = voltmx.io.FileSystem.getExternalFilesDirs(voltmx.io.FileSystem.DIRECTORY_PICTURES);
var isRemovable = voltmx.io.FileSystem.isExternalStorageRemovable(dirPath);
{% endhighlight %}

Return Values

Boolean

Exceptions

None

Platform Availability

*   Android

> **_Note:_** If this API is invoked on a device that runs on Android version KitKat, it always returns a  `false` value.

### voltmx.io.FileSystem.uploadFiles

When the developer invokes this API with the list of files, the API internally iterates through the fileList and makes the network call to the URL mentioned and uploads the files. The API assumes that the application using this API has the necessary server side infrastructure to handle the upload.

Internally, the API uses AJAX-based multi-part upload of the files to the URL mentioned in all browsers except IE 8 and 9. In the case of IE 8 and 9, we provide frame-based submit as the multi-part through AJAX (as it is not handled by the browser).

> **_Note:_** The API voltmx.io.FileSystem.uploadFiles cannot be tested in local jetty server included in the Volt MX Iris. Use Tomcat to test the API. The uploadURL must have code to receive and store the files sent via Volt MX Iris app. The sample war file [UploadServlet30.war](resources/images/uploadservlet30.zip), contains code to handle uploading or storing files at server end. Both Volt MX Iris app and UploadURL needs to be on the same domain.

Syntax

voltmx.io.FileSystem.uploadFiles([URL](#JavaScriptFunction), [fileList](#paramsTable), [upLoadCallBack](#uploadCallBack_), [upLoadConfig](#uploadConfig))

Input Parameters

| Parameter | Description |
| --- | --- |
| URL \[String\] - Mandatory | Provide target location to upload the file. |
| fileList \[Object\] - Mandatory | Specifies the list of files to be uploaded. This is as an array of voltmx.io.FileSystem.file objects. |
| uploadCallBack \[Object\] - Mandatory | The callback is invoked each time when the file is getting uploaded. The signature of the call back is expected to be as follows: _uploadCallBack(URL, upLoadStates)._upLoadState \[Object\] - MandatoryThis is an array of key value map states of the individual files that are uploaded. The key value map currently consists of the following keys:**file**: File (voltmx.io.FileSystem.file) object **status**: One of the following four status are possible : FILE\_UPLOAD\_START\_STATE = 0 FILE\_UPLOAD\_PROGRESS\_STATE = 1 FILE\_UPLOAD\_COMPLETE\_STATE = 2 FILE\_UPLOAD\_ERROR\_STATE = 3**uploadBytes**: Number of bytes that are uploaded. |
| uploadConfig \[Object\] | Configuration parameters, which is a simple JSON object of key value pairs, that provides the possible options during the upload. Currently there are no keys. |

 

Example

{% highlight voltMx %}function UploadBtn_onClick_seq0() { // Event on upload button click
    var uploadURL = "http://10.10.4.17:8080/fileupload/upload";
    var filesQueue = [{
        File object
    }, {
        File Object
    }]; //Array of File objects got in browseCallBack()
    voltmx.io.FileSystem.uploadFiles(uploadURL, filesQueue, upLoadCallBack);
};
{% endhighlight %}

Limitations for File Browse and Upload APIs

1.  API cannot be used in pre-show, post-show, appService, pre-appinit, or post-app init.
2.  For details on filter types for Browse API, follow the specification provided in the IANAMediaTypes. The Volt MX Irisdepends on the browsers respecting the given filter type and enable appropriate file selection for the end user.
3.  File Upload API does not work in the cross origin request scenarios. That is, the file can be uploaded only to the site from which the original app has been accessed. For more information, check CORS documentation.
4.  For security reasons all browsers just give name or size of the file and not parent or full path. So, file parent and full path are not available in File object in browse or upload APIs. For more information, see [http://stackoverflow.com/questions/15201071/how-to-get-full-path-of-selected-file-on-change-of-input-type-file-using-jav](http://stackoverflow.com/questions/15201071/how-to-get-full-path-of-selected-file-on-change-of-input-type-file-using-jav).
5.  **IE 8 and 9 Limitations**:
    
    1.  Multiple file selection will not work. As _multiple_ attribute is not supported for input type= file, it allows the user to select only one file from the browse window even when ‘selectMultipleFiles’ is passed as true. For more information, see [http://www.w3schools.com/tags/att\_input\_multiple.asp](http://www.w3schools.com/tags/att_input_multiple.asp).
    2.  Filters in the Browse API do not work. As _accept_ attribute is not supported for input type= file, even through the filter is passed, it does not have any effect on browse window. User can select any file of any type. Hence, server side file validation is recommended. For more information, see [http://www.w3schools.com/tags/att\_input\_accept.asp](http://www.w3schools.com/tags/att_input_accept.asp).
        
    3.  The file object in Browse API callback method will not have file size in IE 8. IE 8 browsers do provide file path, but it is inconsistent and depends on IE 8 security configuration (IE 9 provide fakepath). We recommend to avoid accessing file parent, path and size in IE 8 and 9. File size is provided in IE 10, Firefox, and Chrome.
    4.  IE 8 and 9 uses iframe for file upload. The uploadprogress event is not triggered and bytes uploaded information is not provided in Upload API callback. So, callback is fired only twice.
        
        1.  When you submit form to iframe with FILE\_UPLOAD\_PROGRESS\_STATE.
        2.  When you get error or success onload event of iframe with respective state constants.
    5.  **Multiple Upload**. If a widget onclick action invokes the Browse API and user selects the file multiple times from the browse window, in browse API callback, you must handle all the files (selected by the user one by one). When Upload API is called, all the files user selected is uploaded to the specified URL. If you want to upload different files on different servers or URLs, then they need to call Browse API and Upload API subsequently one after the other. That is, you need to upload the selected file before letting the user select an other file (in case user wants to upload files on different URLs).
    6.  Empty files cannot be uploaded in case of IE browsers.
6.  **IE 8 and 9 Limitations**:
    
    1.  Multiple file selection will not work. As _multiple_ attribute is not supported for input type= file, it allows the user to select only one file from the browse window even when ‘selectMultipleFiles’ is passed as true. For more information, see [http://www.w3schools.com/tags/att\_input\_multiple.asp](http://www.w3schools.com/tags/att_input_multiple.asp).
    2.  Filters in the Browse API do not work. As _accept_ attribute is not supported for input type= file, even through the filter is passed, it does not have any effect on browse window. User can select any file of any type. Hence, server side file validation is recommended. For more information, see [http://www.w3schools.com/tags/att\_input\_accept.asp](http://www.w3schools.com/tags/att_input_accept.asp).
        
    3.  The file object in Browse API callback method will not have file size in IE 8. IE 8 browsers do provide file path, but it is inconsistent and depends on IE 8 security configuration (IE 9 provide fakepath). We recommend to avoid accessing file parent, path and size in IE 8 and 9. File size is provided in IE 10, Firefox, and Chrome.
    4.  IE 8 and 9 uses iframe for file upload. The uploadprogress event is not triggered and bytes uploaded information is not provided in Upload API callback. So, callback is fired only twice.
        
        1.  When you submit form to iframe with FILE\_UPLOAD\_PROGRESS\_STATE.
        2.  When you get error or success onload event of iframe with respective state constants.
    5.  **Multiple Upload**. If a widget onclick action invokes the Browse API and user selects the file multiple times from the browse window, in browse API callback, you must handle all the files (selected by the user one by one). When Upload API is called, all the files user selected is uploaded to the specified URL. If you want to upload different files on different servers or URLs, then they need to call Browse API and Upload API subsequently one after the other. That is, you need to upload the selected file before letting the user select an other file (in case user wants to upload files on different URLs).
    6.  Empty files cannot be uploaded in case of IE browsers.
7.  When the user uploads a file that has special characters in its file name, the special characters in the file name are replaced with other special characters on the server.
8.  Check if the user is selecting the same file again and create appropriate conditions for browseCallBack. The check will help identify same files if selected earlier and eliminate duplicate files from getting uploaded.
9.  **Firefox Limitation**. Filters with specific Mimetype might not work properly. It is a known bug in Firefox, for more information, see:
    *   [http://techblog.procurios.nl/k/618/news/view/15872/14863/mimetype-corruption-in-firefox.html](http://techblog.procurios.nl/k/618/news/view/15872/14863/mimetype-corruption-in-firefox.html)
    *   [http://support.mozilla.org/en-US/questions/953914](http://support.mozilla.org/en-US/questions/953914)
    *   [https://bugzilla.mozilla.org/show\_bug.cgi?id=826176](https://bugzilla.mozilla.org/show_bug.cgi?id=826176)
    *   [https://bugzilla.mozilla.org/show\_bug.cgi?id=373621](https://bugzilla.mozilla.org/show_bug.cgi?id=373621)

> **_Note:_** Constants: Constants.FILE\_PATH\_SEPARATOR: Platform specific File path separator.

Return Values

None.

Platform Availability

*   Desktop Web

![](resources/prettify/onload.png)
