---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Broadcast Push Message with Filters
===================================

The **Broadcast Push Message with Filters** API, based on a selected mobile platform (iOS, Android, BlackBerry,Windows, and Web), broadcasts push notification to only a subset of users.

This is a secure API and the user needs to provide security credentials to invoke this API.

URL
---

The HTTP URL for **Broadcast Push Message with Filters** API is:

{% highlight voltMx %}<host>:<port>/api/v1/message/push
{% endhighlight %}

This API implements Gateway Filter for Authentication to authenticate access of the API by a user.

Header
------

Based on the content format, the payload's request header content type for:

*   XML is text/xml;charset=UTF-8
*   JSON is application/json;charset=UTF-8

Method
------

Post

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Level – Two | Level – Three | Level- Four | Required | Description |
| --- | --- | --- | --- | --- | --- |
| messageRequest |   |   |   |   | An array of messageRequest objects |
|   | appId |   |   | Yes | Unique ID assigned to an app |
|   | global |   |   | Optional | .An array of global objects |
|   | messages |   |   |   | An array of messages objects |
|   |   | message |   |   | An array of message objects |
|   |   |   | content | Optional | An array of content objectscontent- priorityService (boolean value - Optional)- data (push message -Optional)- mimeType (label for a data so system can know it like,text/plain - Optional) |
|   |   |   | overrideMessageId | Optional | If you wish to change the push message and yet the message is not sent, then you need to pass the old message ID in sample request to update the existing push message to be sent |
|   |   |   | startTimestamp | Optional | Time relative to a starting point |
|   |   |   | expiryTimestamp | Optional | Time relative to an ending point |
|   |   |   | subscribers | osType (Required)allActive (Required) | An array of subscribers objects- allActive (boolean value)- osType (Apple, Anroid, Windows, BlackBerry, and Web) |
|   |   | platformSpecificProps |   | Optional | An array of platform specific properties. For more details, [see](Push_Message_APIs.html#platformspecificprops-input-parameters) |
|   |   | type |   | Required | Type of channel, such as push |

Sample Request
--------------

### XML

{% highlight voltMx %}<?xml version="1.0" encoding="UTF-8"?>
<messageRequest appId="BulkPushApp_132012">
   <global>
      <subscribers />
      <platformSpecificProps />
   </global>
   <messages>
      <message expiryTimestamp="0" overrideMessageId="0" refId="" startTimestamp="0" type="PUSH">
         <subscribers>
            <subscriber allActive="true" osType="iphone" />
         </subscribers>
         <content>
            <mimeType>text/plain</mimeType>
            <priorityService>false</priorityService>
            <data>apple broadcast push</data>
         </content>
      </message>
   </messages>
</messageRequest>
{% endhighlight %}

### JSON

{% highlight voltMx %}{
	"messageRequest": {
		"appId": "22874-10836483458",
		"global": {},
		"messages": {
			"message": {
				"content": {
					"priorityService": "false",
					"data": "push",
					"mimeType": "text/plain"
				},
				"overrideMessageId": 0,
				"startTimestamp": 0,
				"expiryTimestamp": 0,
				"subscribers": {
					"subscriber": [
						{
						"allActive":true,
						"osType":"androidgcm"
						}
					]
				},
				"platformSpecificProps": {},
				"type": "PUSH"
			}
		}
	}
}
{% endhighlight %}

Sample Response
---------------

### XML

{% highlight voltMx %}{
  "details" : [ {
    "refId" : "",
    "description" : "",
    "msgId" : "7716369070950409534"
  } ],
  "id" : "7716369071581121961",
  "message" : "Request Queued. "
}
{% endhighlight %}

### JSON

{% highlight voltMx %}{
  "details" : [ {
    "refId" : "",
    "description" : "",
    "msgId" : "7715504112921814245"
  } ],
  "id" : "7715504135616990626",
  "message" : "Request Queued. "
}
{% endhighlight %}

> **_Note:_**  
**refId**: Here, refId refers to an ID that returns the same value as a user provided in the push payload.  
**msgId**: Here, msgId refers to an ID that is used to map messagerequest table and messageentry table for internal data record.  
**id**: Here, id refers to request ID displayed under Settings > Status > List view > Request ID column  

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Request queued |
| Status 400 | Invalid Volt MX appId or application is not published with given appIdNo active subscribers found for application IDInvalid request format. OS type invalidInvalid request format. No enum constant com.voltmx.vms.enums.MessageType |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">DR</td></tr></tbody></table>
