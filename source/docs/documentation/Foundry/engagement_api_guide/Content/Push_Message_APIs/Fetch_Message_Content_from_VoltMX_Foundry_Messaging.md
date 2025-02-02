---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Fetch Message Content from Volt MX Foundry Engagement Services
=============================================================

The **Fetch Message Content from Volt MX Foundry Engagement Services** API fetches message content from Volt MX Foundry Engagement server.

Use Case
--------

The push ID can be obtained from the push received on the device.

**URL**
-------

The HTTP URL for **Fetch Message Content from Volt MX Foundry Engagement Services** API is:

{% highlight voltMx %}http://<host or ip>:<port>/api/v1/messages/content/$pushId
{% endhighlight %}

Method
------

GET

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| pushID | Yes | long | Unique ID assigned to a push message |

Sample Response
---------------

{% highlight voltMx %}{
  "content": "sample push message string"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Push message content |
| Status 400 | Invalid push ID / Provided push did not associate with rich content |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
