---
layout: "documentation"
category: "engagement_api_guide"
---
                             


Create Segment with Beacon Criteria
===================================

The **Create Segment with Beacon Criteria** API adds segments with beacons into Engagement Services.

URL
---

The HTTP URL for **Create Segment with Beacon Criteria** API is:

{% highlight voltMx %}            
            URL : http://<<host>>:<<port>>/api/v1/segments
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

  
| Input Parameter | Level – Two | Required | Type | Description |
| --- | --- | --- | --- | --- |
| name |   | Yes | string | Unique name assigned to a segment |
| segmentDefinition |   | Yes | string | This includes audience attributes' numbers |
| segmentAudienceList |   |   |   | An array of segmentAudienceList objects |
|   | attributeName | Yes | string | Attribute name, such as beacon, location |
|   | id | Yes | long | Unique ID assigned to an audience attribute name |
|   | attributeOperator | Yes | string | The attribute operator. The following table shows the possible operator values.
| Attribute Type | Acceptable Operator Values |
| --- | --- |
| String | Contains, Equal, NotEqual |
| Pick List | Contains, Equal, NotEqual |
| Number | Contains, Equal, NotEqual, GreaterThan, LessThan |
| Date | Contains, Equal, NotEqual, GreaterThan, LessThan, GreaterThanCurrentDateMinus, GreaterThanCurrentDatePlus, LessThanCurrentDateMinus, LessThanCurrentDatePlus |

 |
|   | conditionNo | Yes | string | Unique condition operator number assigned to an audience attribute operator |

Sample Request
--------------

{% highlight voltMx %}{
  "name": "Segment with Beacons Criteria",
  "segmentDefinition": "1 OR 2 OR 3",
  "segmentAudienceList": [
    {
      "attributeName": "Location",
      "audienceLocation": {
        "id": "1"
      },
      "attributeOperator": "Contains",
      "conditionNo": 1
    },
    {
      "attributeName": "Beacon",
      "audienceBeacon": {
        "id": "1"
      },
      "attributeOperator": "Contains",
      "conditionNo": 2
    },
    {
      "attributeName": "firstName",
      "attributeValue": "admin",
      "attributeOperator": "Equal",
      "conditionNo": 3
    }
  ]
}
{% endhighlight %}

Output Parameters
-----------------

The following fields are output parameters:

Sample Request
--------------

{ "name": "Segment with Beacons Criteria", "segmentDefinition": "1 OR 2 OR 3", "segmentAudienceList": \[ { "attributeName": "Location", "audienceLocation": { "id": "1" }, "attributeOperator": "Contains", "conditionNo": 1 }, { "attributeName": "Beacon", "audienceBeacon": { "id": "1" }, "attributeOperator": "Contains", "conditionNo": 2 }, { "attributeName": "firstName", "attributeValue": "admin", "attributeOperator": "Equal", "conditionNo": 3 } \] }

Output Parameters
-----------------

The following fields are output parameters:

Sample Request
--------------

{% highlight voltMx %}{
  "name": "Segment with Beacons Criteria",
  "segmentDefinition": "1 OR 2 OR 3",
  "segmentAudienceList": [
    {
      "attributeName": "Location",
      "audienceLocation": {
        "id": "1"
      },
      "attributeOperator": "Contains",
      "conditionNo": 1
    },
    {
      "attributeName": "Beacon",
      "audienceBeacon": {
        "id": "1"
      },
      "attributeOperator": "Contains",
      "conditionNo": 2
    },
    {
      "attributeName": "firstName",
      "attributeValue": "admin",
      "attributeOperator": "Equal",
      "conditionNo": 3
    }
  ]
}
{% endhighlight %}

Output Parameters
-----------------

The following fields are output parameters:

  
| Output Parameter | Type | Description |
| --- | --- | --- |
| id | long | Unique ID assigned to a segment |
| message | string | Response status message |

Sample Response
---------------

{% highlight voltMx %}{
  "id" : "8",
  "message" : "Details added successfully"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Segment created successfully |
| Status 400 | Invalid request format |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
