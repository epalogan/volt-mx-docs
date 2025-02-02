---
layout: "documentation"
category: "engagement_api_guide"
---
                           


Update Geo Location of Device to Volt MX Foundry Engagement Services
===================================================================

The **Update Geo Location of Device to Volt MX Foundry Engagement Services**  API is used to update the approximate position of the device based on inputs such as Ksid, latitude, location, and longitude.

> **_Important:_** The Update Geo Location of Device to Volt MX Foundry Engagement Services API is maintained here to preserve backward compatibility.  
We encourage you to use [Update Geo Location of a Device](../REST_API_Geo_Location/Update_Geolocation_of_Device_to_VoltMX_Foundry_Messaging.html)

**URL**
-------

The HTTP URL for Update Geo Location of Device to Volt MX Foundry Engagement Services API is:

{% highlight voltMx %}http://<host or ip>:<port>/service/geolocupdate
{% endhighlight %}

Method
------

POST

Content Type
------------

application/json;charset=UTF-8

**Sample Request**
------------------

{% highlight voltMx %}request format:  
{  
"ksid": "$ksid",  
"latitude": "$lat",  
"locname": "$locname",  
"longitude": "$lon"  
}
{% endhighlight %}

*   Ksid: Volt MX Subscription Identification number of the application. For more details, refer to [Ksid]({{ site.baseurl }}/docs/documentation/Foundry/vms_console_user_guide/Content/Apps/Modifying_Subscribers_List.html).
*   **Latitude**: Latitude is a geographic coordinate, in decimal degrees, that specifies the north-south position of a point on the Earth's surface.
*   Locname: The device is identified with the location name.
*   **Longitude**: Longitude is a geographic coordinate, in decimal degrees, that specifies the east-west position of a point on the Earth's surface.

Response Code
-------------

Success response code is _200._

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
