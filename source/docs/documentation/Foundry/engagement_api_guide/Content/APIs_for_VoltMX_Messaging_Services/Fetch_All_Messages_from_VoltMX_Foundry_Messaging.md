---
layout: "documentation"
category: "engagement_api_guide"
---
                           


Fetch All Messages from Volt MX Foundry Engagement Services
==========================================================

The **Fetch All Messages from Volt MX Foundry Engagement Services** API is used to get message content from the server based on the input parameters.

> **_Important:_** The Fetch All Message Content from Volt MX Foundry Engagement Services API is maintained here to preserve backward compatibility.  
We encourage you to use [Fetch All Message Content from Volt MX Foundry Engagement Services](../Push_Message_APIs/Fetch_All_Messages_from_VoltMX_Foundry_Messaging.html)

URL
---

The HTTP URL for Fetch All Messages from Volt MX Foundry Engagement Services API is:

{% highlight voltMx %}http://<host or ip>:<port>/service/entrydata/fetchmessages
{% endhighlight %}

Method
------

POST

Input Parameters
----------------

This service takes input parameters in JSON formats.

1.  With KSID  
      
    {% highlight voltMx %}{ "ksid": "VoltMXSubscriberID",  
      "startElement": "0",   
      "elementsPerPage": "10" }
    {% endhighlight %}
    *   **ksid**: Volt MX Subscription ID returned when you subscribe to Volt MX Foundry Engagement Services.
    *   startElement: Starting element is a non-negative integer such as 0,1,2,3.
    *   elementsPerPage: Number of messages to be displayed per page.
2.  With DEVICEID and APPID{% highlight voltMx %}{ "deviceId": "123456",  
       "appId" : "VoltMX Foundry Messaging_APPLICATION_ID",  
      "startElement": "0",   
      "elementsPerPage": "10" }
    {% endhighlight %}
    *   **deviceId**: Device ID of the Subscriber which was used when you subscribe to Volt MX Foundry Engagement Services.
    *   **appId**: Application ID in Volt MX Foundry Messaging Engagement Services.
    *   startElement: Starting element is a non-negative integer such as 0,1,2,3.
    *   elementsPerPage: Number of messages to be displayed per page.
3.  With UFID and APPID{% highlight voltMx %}{ "ufid": "xxx@gmail.com",  
       "appId": "VoltMX Foundry Messaging_APPLICATION_ID",  
      "startElement": "0",   
      "elementsPerPage": "10" }
    {% endhighlight %}
    
    *   **ufid**: UFID of the subscriber which was used when you subscribe to Volt MX Foundry Engagement Services.
    *   **appId**: Application ID in Volt MX Foundry Engagement Services.
    *   startElement: Starting element is a non-negative integer such as 0,1,2,3.
    *   elementsPerPage: Number of messages to be displayed per page.
    
    > **_Important:_** If the **Auth** t**oken** for **subscription** APItext box is enabled in the **Administration** \> **General** tab > **Security**, you need to append the authToken element in the JSON request for all the three formats.
    
    Sample JSON with authToken
    
    {% highlight voltMx %}{ "ksid": "VoltMXSubscriberID",  
      "startElement": "0",   
      "elementsPerPage": "10",  
      "authToken":  "xxxxxx"}
    {% endhighlight %}

Response
--------

Success response code is "_200_".

Response will be a JSON with all Push messages sent to the Subscriber. Sample response is:

{% highlight voltMx %}{"openedMessages":0,"submittedMessages":1,"totalMessages":1,"messages":[{"content":"This is a test push.","status":"Submitted","fetchid":"7530271640775557121"}]}
{% endhighlight %}

*   **openedMessages**: Number of Messages opened by subscriber.
*   **submittedMessages**: Number of messages successfully delivered to subscriber and not opened.
*   **totalMessages**: Total number of messages successfully delivered to subscriber.

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
