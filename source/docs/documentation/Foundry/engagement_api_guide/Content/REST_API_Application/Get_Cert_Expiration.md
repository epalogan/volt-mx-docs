---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Get Certificate Expiration
==========================

The **Get Certificate Expiration** API gets the expiration date of all app certificates and pass certificates. If the appId is passed, the API returns the expiration information for all certificates for the specified app. If no ID is passed, the certificate information for all apps and Pass certificates is returned.

URL
---

The HTTP URL to retrieve a specified certification using the **Get Certificate Expiration** API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/applications/certexpirydetails?appId=yourappId
{% endhighlight %}

The HTTP URL to retrieve all certs in all apps and Pass certs using the **Get Certificate Expiration** API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/applications/certexpirydetails
{% endhighlight %}

This service implements Gateway Filter for Authentication to authenticate access of the service by a user.

Method
------

GET

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| appId | No | string | The specified app for which the certificate information is returned. If this parameter is missing, information for all app certificates and Pass certificates is returned. |

Output Parameters
-----------------

The following fields are output parameters:

  
| Output Parameter | Level Two | Level Three | Type | Description |
| --- | --- | --- | --- | --- |
| appCertificates |   |   |   | An array of information for app certificates |
|   | appId |   | long | The unique ID assigned to the app. |
|   | certificates |   | array | An array of certificate objects. |
|   |   | expiryDate | string | The expiration date of the certificate |
|   |   | daysLeft | long | The number of days remaining before the certificate expires |
|   |   | platform | string | The platform for the app |
|   |   | certificateType | string | The certificate type |
| passCertificates |   |   | array | An array of information for pass certificates. |
|   | expiryDate |   | string | The expiration date of the certificate |
|   | daysLeft |   | long | The number of days remaining before the certificate expires. |
|   | passTypeIdentifier |   | string | The ID used to identify a pass that can be generated using Apple developer’s account. |
|   | passTeamIdentifier |   | alphanumeric string | An identifier that is unique to a particular Apple developer account. |
|   | passCertificateName |   | string | The name of the certificate. |

Sample Response
---------------

In the following code example, an appId was passed as a query parameter. The response a shows a single certificate is returned.

{% highlight voltMx %}{
   "appCertificates" : [ {
      "appId" : "AppForAll1",
      "certificates" : [ {
         "expiryDate" : "07 Jan, 2018 11.41:02 AM IST",
         "daysLeft" : 214,
         "platform" : "iPhone",
         "certificateType" : "Production"
      }, {
         "expiryDate" : "07 Jan, 2018 11.41:02 AM IST",
         "daysLeft" : 214,
         "platform" : "iPad",
         "certificateType" : "Production"
      } ]
   } ]
}


{% endhighlight %}

In the following code example, no query parameters were passed. Information for all certificates is returned.

{% highlight voltMx %}
{
   "appCertificates": [
   {
      "appId": "testAuto3005",
      "certificates": [
      {
         "expiryDate": "07 Jan, 2018 11.41:02 AM IST",
         "daysLeft": 214,
         "platform": "iPhone",
         "certificateType": "Production"
      },
      {
         "expiryDate": "16 Nov, 2017 05.59:07 PM IST",
         "daysLeft": 163,
         "platform": "iPhone",
         "certificateType": "Production"
      }
   ]
   },
   {
      "appId": "testAuto9116",
      "certificates": [
      {
         "expiryDate": "07 Jan, 2018 11.41:02 AM IST",
         "daysLeft": 214,
         "platform": "iPad",
         "certificateType": "Production"
      }
      ]
   }
   ],
   "passCertificates": [
   {
      "expiryDate": "03 Mar, 2018 11.56:13 AM IST",
      "daysLeft": 269,
      "passTypeIdentifier": "pass.com.xxx.xxx",
      "passTeamIdentifier": "passTeamIdentifier",
      "passCertificateName": "admin"
   },
   {
      "expiryDate": "07 Sep, 2017 03.48:31 PM IST",
      "daysLeft": 93,
      "passTypeIdentifier": "pass.com.xxx.xxx",
      "passTeamIdentifier": "passTeamIdentifier",
      "passCertificateName": "ServiceSuiteSetup261"
   }
   ]
}

		
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Array of event types |
| Status 401 | Invalid event type ID provided or no event type found with given ID |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">Au</td></tr></tbody></table>
