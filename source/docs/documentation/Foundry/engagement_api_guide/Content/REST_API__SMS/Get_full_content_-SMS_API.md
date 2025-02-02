---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Get Full Content
================

The **Get Full Content** API accepts the SMS ID as an input parameter and returns the SMS message content and selected personalization attribute details like first name, last name, email, mobile number, country and state.

> **_Note:_** This API will return content for both Text as well as Voice SMS.

Use Case
--------

A user may need to retrieve the content of a SMS message to display the same in a custom built application. The Get Full Content API requires SMS ID to retrieve the data.

You need to select the SMS ID from Settings > Status > SMS Queue list view. Select the required SMS ID under the SMS ID column.

URL
---

The HTTP URL for Get Full Content API is:

{% highlight voltMx %}/api/v1/messages/sms/content/{sms_id}
{% endhighlight %}

> **_Note:_** The Get Full Content API does not require authentication. It is not a secure API

Method
------

GET

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| sms\_id | Yes | string | SMS message string / Voice SMS string. |

Sample Response
---------------

{% highlight voltMx %}{
  "content": "Thomas Smith thomassmith@gmail.com +917809654277 \n\nAmazon Electronic Gadgets Sale 2016\n\nBuy your stuff online…"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | SMS config details JSON |
| Status 400 | Invalid SMS ID. No message found with the provided ID |
| Status 401 | Unauthorized request. |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
