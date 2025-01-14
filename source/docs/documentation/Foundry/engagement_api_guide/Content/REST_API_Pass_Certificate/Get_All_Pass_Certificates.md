---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Get All Pass Certificates
=========================

The **Get All Pass Certificate**s API accepts start and pageSize as input parameters and returns all the pass certificate details. The pageSize represents the maximum number of the pass certificates for which the details are to be returned. If the start is specified, the number of the pass certificates that are returned are from start position to pageSize value. For example: if the start is zero and pageSize is five, then six pass certificates from position zero to five are returned.

URL
---

The HTTP URL for Get All Pass Certificate API is:

{% highlight voltMx %}http://<<host>>:<<port>>/api/v1/passcerts?start=0&pageSize=10
{% endhighlight %}

Method
------

GET

Output Parameters
-----------------

The following fields are output parameters:

  
| Output Parameter | Level – Two | Type | Description |
| --- | --- | --- | --- |
| total |   | long | Total number of pass certificates |
| certificates |   |   | An array of certificates objects |
|   | id | long | Unique ID assigned to a pass certificate |
|   | name | string | Pass certificate name |
|   | certUrl | string | A valid URL to generate a Pass certificate |
|   | password | string | Unique password assigned to a pass certificate |
|   | fileName | string | Pass certificate name (in p12 format) |
|   | identifier | string | A Pass type identifier is used to identify a pass that can be generated using Apple developer’s account |
|   | teamIdentifier | alphanumeric | Team Identifier is unique to a particular Apple developer account |
|   | expiryDateStr | string | Date on which the pass certificate will expire |
|   | createdBy | string | A user name that shows who created the pass certificate |
|   | createdDateStr | string | Date on which the pass certificate is created |
|   | updatedBy | string | A user name that shows who last modified the pass certificate |
|   | updatedDateStr | string | Date on which the pass certificate is updated |
|   | deleted | boolean | If pass certificate is deleted or not |

Sample Response
---------------

{% highlight voltMx %}{
  "total" : 2,
  "certificates" : [ {
    "id" : 1,
    "name" : "eBay pass",
    "certUrl" : "http://10.10.17.209:8080/vpns/api/v1/passcerts/downloadpasscertificate?id=1",
    "password" : "voltmx123",
    "fileName" : "passbook21.p12",
    "identifier" : "pass.com.vms.passbook2",
    "teamIdentifier" : "PM7352S8QE",
    "expiryDateStr" : "09/01/2016 04:37:40 PM IST",
    "createdBy" : "admin",
    "createdDateStr" : "06/30/2016 10:42:49 AM IST",
    "updatedBy" : "admin",
    "updatedDateStr" : "06/30/2016 10:42:49 AM IST",
    "deleted" : false
  }, {
    "id" : 2,
    "name" : "Pass Certificate 41",
    "certUrl" : "http://10.10.17.209:8080/vpns/api/v1/passcerts/downloadpasscertificate?id=2",
    "password" : "voltmx123",
    "fileName" : "passbook41.p12",
    "identifier" : "pass.com.vms.passbook4",
    "teamIdentifier" : "PM7352S8QE",
    "expiryDateStr" : "09/02/2017 02:22:25 PM IST",
    "createdBy" : "admin",
    "createdDateStr" : "09/14/2016 05:35:29 PM IST",
    "updatedBy" : "admin",
    "updatedDateStr" : "09/14/2016 05:35:29 PM IST",
    "deleted" : false
  } ]
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Array of pass certs |
| Status 400 | Bad request |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
