---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Import Events
=============

The **Import Events** API imports events from a zip file of compressed JSON files. For information about the structure of the files see [JSON Files for Import and Export](../JSON_Files.html). If the format of the data in the file is incorrect, the upload does not occur at all and an error message and the status code is returned.

This API first checks if the format of the file is correct and then performs the data insert. After this API is executed, the return message only indicates whether or not the format of the file is correct. Use the returned ID to call the [Get File Upload Status by ID](../REST_API_Administration/Get_File_Upload_Status_by_ID.html) API to get the status of the import. To view the list of errors that may have occurred during the import, call the [Get File Errors By Pagination](../REST_API_Administration/Get_File_Errors_By_Pagination.html) API.

URL
---

The HTTP URL for **Import Events** API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/events/import
{% endhighlight %}

This API is secure and implements Gateway Filter for Authentication/Basic Authentication to authenticate access of the API by a user.

Method
------

POST

Because this API uploads a file, you must use the "multipart/form-data" encoding format. You must also provide the following request headers with the request.

*   file (which points to the name of the file that is uploaded)
*   **importType**: The possible values for **importType** are:
    *   **insert** - This option reads the data in the zip file and attempts to perform an insert. If the insert fails, an error is thrown.
    *   **upsert** - This option reads the data in the zip file and attempts to perform an update of each record. If the update fails, the record is inserted.
    *   **delsert** - This option deletes all existing data and performs an insert of the data in the zip file. It is strongly recommended that you back up your data before choosing this option.

Header
------

To invoke this API, pass the following request headers with the corresponding values.

Content-Disposition: form-data; file: Events.zip  
Content-Type: application/x-zip.compressed

The payload's request header includes Content-Type as multipart/form-data.

Input Parameters
----------------

The required request headers are:

Content-Disposition: form-data; name="file"; filename="Events.zip"  
Content-Type: application/x-zip.compressed

Output Parameters
-----------------

The following fields are output parameters:

  
| Output Parameter | Type | Description |
| --- | --- | --- |
| message | string | Message associated with response status code |
| id | long | File upload ID |

Call the [Get File Upload Status by ID](../REST_API_Administration/Get_File_Upload_Status_by_ID.html) API using the returned ID as the input parameter to verify the status of the import. This API will also provide additional error information if the import failed.

Sample Response
---------------

{% highlight voltMx %}{
   "message":"File uploaded successfully. Import is in progress.",
   "id" : "4855568447645532159"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Successful upload of file for processing |
| Status 400 | Bad request |
| Status 401 | Unauthorized request |
| Status 500 | Failed to import the data |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.3</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">SS</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">SS</td></tr></tbody></table>
