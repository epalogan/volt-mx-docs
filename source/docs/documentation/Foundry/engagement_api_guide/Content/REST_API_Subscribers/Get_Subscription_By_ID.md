---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Get Subscriber Details by ID
============================

The **Get Subscriber Details by ID** API responds with a subscriber's details matching the subscriber ID. You need to pass KSID in URL to receive the subscriber's details.

URL
---

The HTTP URL for **Get Subscriber Details by ID** API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/subscribers/<subscriberId>
{% endhighlight %}

This service implements Gateway Filter for Authentication to authenticate access of the service by a user.

Method
------

GET

Ouput Parameters
----------------

The following fields are output parameters:

  
| Output Parameter | Type | Description |
| --- | --- | --- |
| ksid | long | The Volt MX subscription ID of the application |
| appId | long | Unique ID assigned to the application |
| ufid | string | The User Friendly Identifier or UFID is used when you subscribe to Volt MX Foundry Engagement Services. Based on your requirement, you can provide an UFID. It is alphanumeric, for example xxx@voltmx.com or 2890XZCY. It can be used to map devices to the user using the value as a reconciliation key. |
| deviceId | string | Unique ID assigned to the device |
| deviceName | string | The device name |
| sid | string | Subscription token registered with the corresponding cloud service (Apple, Android, BlackBerry, Windows) |
| osType | string | Valid OStype : iPhone, iPad, iPod, androidgcm, Windows, Windows8, BlackBerry, webfcm |
| phoneNo | long | Telephone number of the subscriber |
| createdDateStr | string | Date and time on which the subscription was created |
| userAgent | string | Client used to call this subscription API |
| ipAddress | string | The IP address of the system |
| subscriptionStatus | boolean | Whether the subscription status is active |
| cloudStatus | boolean | Whether cloud subscription status is active |

Sample Response
---------------

{% highlight voltMx %}{
  "ksid" : 4927562634448402412,
  "appId" : "20096-6548262167",
  "ufid" : "aron.hale@voltmx.com",
  "deviceId" : "800ABC1",
  "deviceName" : "Second Device",
  "sid" : "9002390C",
  "osType" : "windows",
  "phoneNo" : "",
  "createdDateStr" : "06/22/2016 12:42:20 PM IST",
  "userAgent" : "Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.103 Safari/537.36",
  "ipAddress" : "10.10.30.89",
  "subscriptionStatus" : true,
  "cloudStatus" : true
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Subscriber details |
| Status 400 | Invalid KSID |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">DR</td></tr></tbody></table>
