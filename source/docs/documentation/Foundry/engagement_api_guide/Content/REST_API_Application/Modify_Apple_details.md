---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Modify Apple Details
====================

The **Modify Apple details** API updates the Apple certificate.

URL
---

The HTTP URL for **Modify Apple details** API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/applications/<id>/apple
{% endhighlight %}

This service implements Gateway Filter for Authentication to authenticate access of the service by a user.

> **_Note:_** <id>: While creating an app, a unique ID is assigned to an application. Provide the unique identifier for the app in REST URL.  

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
| appIcon | Yes | Icon should be in .jpeg or .png format and not more than 64 kb in size. | Image that represents the app |
| appleCertDev | Yes | p12 files | Apple Push Notification Certificate (Development) |
| appleCert | Yes | .p12 files | Apple Push Notification Certificate (Production) |
| appleDevCertPassPhrase | Yes | alphanumeric(no spaces). | Password |
| appleCertPassPhrase | Yes | alphanumeric(no spaces) | Password |
| ipadCertDev | Yes | p12 files | Apple iPad Push Notification Certificate (Development) |
| ipadCert | Yes | p12 files | Apple iPad Push Notification Certificate (Production) |
| ipadDevCertPassPhrase | Yes | alphanumeric(no spaces). | Apple iPad Push Certificate Password(Dev)(optional) |
| ipadCertPassPhrase | Yes | alphanumeric(no spaces). | Apple iPad Push Certificate Password(Prod)(Optional) |
|  appleApplicationMode | Yes | Boolean | Application Production mode(true/false) |

Sample Request
--------------

{% highlight voltMx %}appIcon:  icon file  
appleCert: Production apple certificate  
appleCertPassPhrase: Production apple certificate password  
appleCertDev: Sandbox apple certificate  
appleDevCertPassPhrase: Sandbox apple certificate password  
ipadCert: Production Apple Certificate for iPad  
ipadCertPassPhrase: Production Apple Certificate for iPad password  
ipadCertDev: Sandbox Apple Certificate for iPad  
ipadDevCertPassPhrase: Sandbox Apple Certificate for iPad password  
appleApplicationMode: true  

{% endhighlight %}

Output Parameters
-----------------

The following fields are output parameters:

  
| Output Parameter | Type | Description |
| --- | --- | --- |
| id | long | Unique app ID assigned to an app |
| message | string | Response status message |

Sample Response
---------------

{% highlight voltMx %}{  
   "message" : "Details updated successfully",  
   "id" : "appId"  
}  

{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Details uploaded successfully |
| Status 400 | Invalid appID provided or no application found with provided appID |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
