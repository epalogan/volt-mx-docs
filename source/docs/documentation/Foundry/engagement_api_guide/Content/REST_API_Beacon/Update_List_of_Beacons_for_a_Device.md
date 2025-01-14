---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Update List of Beacons for a Device
===================================

The **Update List of Beacons for a Device** API updates the list of beacons for a device. There are two ways to update the list of beacons for a device:

*   Through ksid
*   Through a combination of ufid and appid

URL
---

The HTTP URL for **Update List of Beacons for a Device** API is:

{% highlight voltMx %}http://<<host>>:<<port>>/api/v1/beaconupdate
{% endhighlight %}

This service implements Gateway Filter for Authentication to authenticate access of the service by a user.

Method
------

POST

Header
------

The payload's request header includes Content-Type as application/json;charset=UTF-8.

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Level- Two | Required | Type | Description |
| --- | --- | --- | --- | --- |
| ksid |   | Yes | long   | Volt MX Subscription Identification number of the application > **_Note:_** You must provide the ksid, if you do not provide the ufid and appid. |
| ufid |   | Yes | string | The User Friendly Identifier or UFID is used when you subscribe to Volt MX Foundry Engagement Services. Based on your requirement, you can provide an UFID. It is alphanumeric, for example xxx@voltmx.com or 2890XZCY. It can be used to map devices to the user using the value as a reconciliation key > **_Note:_**  You must provide both the ufid and appid, if you do not provide the ksid. |
| appid |   | Yes | alphanumeric | Unique ID assigned to an app > **_Note:_**  You must provide both the ufid and appid, if you do not provide the ksid. |
| beacon |   |   |   | An array of beacon objects |
|   | uuid | Yes | long | Universally Unique Identifier Number (UUID) assigned to the Beacon. UUID contains 32 hexadecimal digits, split into 5 groups, and separated by dashes, for example, f7826da6-4fa2-4e98-8024-bc5b71e0893eBy default, beacon format consists of three values: UUID, Major, Minor. Beacons broadcast their IDs, which can be recognized by mobile apps to trigger specific actions. |
|   | major | Yes | long | Major ID is a major identifier of a Bluetooth beacon. |
|   | minor | Yes | long | Minor ID is a minor identifier of a Bluetooth beacon. |

Sample Request
--------------

### Updating List of Beacons through ksid

{% highlight voltMx %} {
 	"ksid": "5976328003246374004",
 	"ufid": "",
 	"appid": "",
 	"beacons": {
 		"beacon": {
 			"uuid": "Beacon-Create-UUID",
 			"major": "500",
 			"minor": "100"
 		}
 	}
 }
{% endhighlight %}

### Updating List of Beacons through a combination of ufid and appid

{% highlight voltMx %}{
 	"ksid": "5976328003246374004",
 	"ufid": "admin@voltmx.com",
 	"appid": "AppForAll",
 	"beacons": {
 		"beacon": {
 			"uuid": "Beacon-Create-UUID786IUJHG",
 			"major": "600",
 			"minor": "200"
 		}
 	}
 }
{% endhighlight %}

Sample Response
---------------

{% highlight voltMx %}{
  "id" : "",
  "message" : "Updated Successfully"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Beacons updated successfully |
| Status 400 | Invalid request format |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
