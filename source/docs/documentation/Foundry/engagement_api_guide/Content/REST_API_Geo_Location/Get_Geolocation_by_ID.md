---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Get Geolocation by ID
=====================

The **Get Geolocation by ID** API uses the geolocation ID as an input parameter and returns the location details.

Use Case
--------

The user would like to get the details of a geoboundary that is associated with an ATM location. The user already retrieved the geolocation IDs in his/her application. Because the geolocation ID uniquely identifies a geolocation in the engagement server, the user can then invoke this API to retrieve the details.

URL
---

The HTTP URL for **Get Geolocation by ID** API is:

{% highlight voltMx %}http://<host>:<port>/api/v1/geolocations/{id}
{% endhighlight %}

This API is protected and implements Gateway Filter for Authentication to authenticate access of the API by a user.

> **_Note:_** <id>: Here, id refers to an id that is used to map a geolocation with internal data record.

Method
------

GET

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Required | Type | Description |
| --- | --- | --- | --- |
| id | Yes | long | The id is used to map a geolocation with an internal data record in the engagement server. |

Output Parameters
-----------------

The following fields are output parameters:

  
| Output Parameter | Type | Description |
| --- | --- | --- |
| id | long | The specific location ID. |
| name | string | Location name. |
| description | string | Location description. |
| latitude | long | Specifies the latitude value of this geolocation. Latitude is a geographic coordinate that specifies the north–south position of a location on the earth's surface. Geographic coordinates are specified in decimal degrees |
| longitude | long | Specifies the longitude value of this geolocation. Longitude specifies the east–west position of a location on the earth's surface. Geographic coordinates are specified in decimal degrees |
| altitude | long | The altitude of the location that is returned. Altitude is the height of a location, in meters, in relation to sea level or ground level. |
| miles | long | The radius of the geolocation that is returned. |
| lastModifiedBy | string | User name showing who last modified the location. |
| createdBy | string | User name showing who created the location. |
| clientAction | string | Possible values are: "Notify Engagement Server" - This is the default value. This means that the client application will need to update its location with the Engagement server when the geoboundary is entered. This could be used in a scenario where the Engagement server will need to send the notifications because of a location-based campaign that is set up. "Local Notification"- This value means that the client application must display a local notification when the geoboundary is entered. All the geoboundaries with this clientAction have a local notification message that is associated and this is the message that is displayed in the local notification. "Custom Client Logic" - This value is any java script code that needs to be executed by the client application. A geoboundary with this clientAction will have a java script code that is associated with it which can be executed on the client side if needed. |
| message | string | The message that is displayed if clientAction is "Local Notification". |
| lastModifiedDateStr | string | Date the location was last modified |
| createdDateStr | string | Date and time location is created |
| locationTags | array | An array of tags associated with the location. These tags represent additional data that is associated with the geoboundaries. The tags can be used to filter the list of geoboundaries that are returned. For example, geoboundaries can be tagged with an application name and only those geoboundaries associated with the tag can be retrieved when needed. |
| metadata | array | An array of key/value pairs that contain metadata of the location. |

Sample Response
---------------

{% highlight voltMx %}{
  "id" : 1,
  "name" : "New York",
  "description" : "New York City Shopping Area",
  "latitude" : 40.7324,
  "longitude" : -73.8248,
  "altitude" : 20.0,
  "miles" : 50.0,
  "lastModifiedBy" : "admin",
  "createdBy" : "admin",
  "clientAction" : "local notification"
  "message" : "Sample notification message"			
  "lastModifiedDateStr" : "06/21/2016 06:19:01 PM IST",
  "createdDateStr" : "06/21/2016 05:21:49 PM IST"
  "locationTags" : ["Times Square", "Manhattan"],
  "metadata" : [
    {
       "key" : "nycKey1",
       "value" : "nycKey2"
    }]
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Array of geolocation details |
| Status 400 | Invalid location ID provided or no location found with the ID |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.3</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">SS</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">Ss</td></tr></tbody></table>
