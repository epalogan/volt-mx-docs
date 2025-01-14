---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Delete Inbound Command
======================

The **Delete Inbound Command** API deletes an inbound command. All communication from this API stops immediately.

URL
---

The HTTP URL for Delete Inbound Command API is:

{% highlight voltMx %}http://<<host>>:<<port>>/api/v1/twowaysms/<number-id>/command/<command-id>/delete
{% endhighlight %}

> **_Note:_** Use the Get All command API to know the command ID, which needs to be passed in the URL. The ID received from Get All command is the command ID to be used in the URL.

This service implements ‘Gateway Filter for Authentication’ to authenticate access of the service by a user.

Method
------

POST

Header
------

The payload's request header includes Content-Type as application/json;charset=UTF-8.

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| number-id | Yes | long | The unique number ID assigned to an inbound command |
| command-id | Yes | long | The unique command ID assigned to an inbound command |

Sample Response
---------------

{% highlight voltMx %}{
  "id" : "2",
  "message" : "Inbound SMS Command deleted successfully"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Inbound SMS command deleted successfully |
| Status 400 | No SMS number found for this IDNo inbound SMS command found to delete |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
