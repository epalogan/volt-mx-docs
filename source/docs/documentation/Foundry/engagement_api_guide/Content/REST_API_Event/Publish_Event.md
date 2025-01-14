---
layout: "documentation"
category: "engagement_api_guide"
---
                             


Activate Event
==============

The **Activate Event** API activates an event that is added into Volt MX Foundry Engagement server. This service accepts Event ID as an input parameter to activate an event. Only activated events are used for push notifications.

URL
---

The HTTP URL for **Activate Event** API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/events/<id>/publish
{% endhighlight %}

> **_Note:_** <id>: Refers to an ID that is used to map an event with internal data record.

This service implements Gateway Filter for Authentication to authenticate access of the service by a user.

Method
------

POST

Header
------

The payload's request header includes Content-Type for JSON as application/json;charset=UTF-8.

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| Event id | Yes | long | Here, id refers to an ID that is used to map an event with internal data record. |

Sample Response
---------------

{% highlight voltMx %}{
  "id" : "3",
  "message" : "Event activated successfully"
}
{% endhighlight %}

> **_Note:_** Here, id displayed in sample response refers to an ID that is used to map an event with internal data record.

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Event activated successfully |
| Status 401 | Invalid event ID provided or no event found with given ID |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
