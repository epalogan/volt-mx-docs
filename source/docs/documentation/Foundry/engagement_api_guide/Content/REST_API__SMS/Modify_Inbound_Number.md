---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Modify Inbound Number
=====================

An inbound number instance resource represents a long number or short code purchased from TWILIO or NEXMO or CLICKATELL. The **Modify Inbound Number** API enables you to modify a new long number or a new short code in Engagement Services. Assume that a customers sends SMS like BAL to 53535, where 53535 is an inbound number and BAL is the inbound command. You can configure multiple commands for an inbound number.

URL
---

The HTTP URL for Modify Inbound Number API is:

{% highlight voltMx %}http://<host>>:<<port>>/api/v1/twowaysms/number/<number-id>/modify
{% endhighlight %}

This service implements ‘Gateway Filter for Authentication’ to authenticate access of the service by a user.

> **_Note:_** <number-id>: Here, number ID refers to an ID that is used to map inbound number with internal data record.

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
| name | Yes | string | A unique name assigned to the number such as Customer Banking Number |
| code | Yes | long | Short code/ Long Number |
| description | Optional | string | Description of the inbound number |
| replyForInvalidReq | Optional | string | SMS to be sent for invalid requests that are sent to this number. If this field is left blank, then no reply SMS will be sent for invalid requests |

Sample Request
--------------

{% highlight voltMx %}{
     "name": "Balance Inquiry",
     "code": "57676",
     "description": "Balance inquiry portal",
     "replyForInvalidReq": "Invalid message, Please type BAL for balance enquiry"
}
{% endhighlight %}

Sample Response
---------------

{% highlight voltMx %}{
  "id" : "1",
  "message" : "Details updated successfully"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Details updated successfully |
| Status 400 | An inbound number already exists with this name or code |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
