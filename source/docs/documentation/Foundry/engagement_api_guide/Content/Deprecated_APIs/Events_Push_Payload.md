---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Events Push Payload
===================

The **Event Push Payload** API is used to send event push messages.

> **_Important:_** The Events Push Payload API is maintained here to preserve backward compatibility. We encourage you to use [Events Push Message](../REST_API_Event/Event_Push_Message.html)

URL
---

The HTTP URL for Events Push Payload API is:

{% highlight voltMx %}http://<host or ip>:<port>/vpns/service/eventpushmessage
{% endhighlight %}

Method
------

HTTP POST

Content Type
------------

Based on the content format, the payload's request header includes "Content-Type" for:

*   **XML** is text/xml;charset=UTF-8
*   **JSON** is application/json;charset=UTF-8

Sample Request
--------------

### XML

{% highlight voltMx %}<?xml version='1.0' encoding='UTF-8'?>
<event>
  <eventid>1</eventid>
  <eventNamePairs>
  </eventNamePairs>
  <message>
    <subscribers>
      <subscriber ksid="xxxx"/>
    </subscribers>
    <content>
      <mimeType>text/plain</mimeType>
      <priorityService>false</priorityService>
    </content>
  </message>
</event>

{% endhighlight %}

### JSON

{% highlight voltMx %}{
 "event": {
  "message": {
   "content": {
    "priorityService": "false",
    "mimeType": "text/plain"
   },
   "subscribers": {
    "subscriber": [
     {
      "ksid": "xxxx"
     }
    ]
   }
  },
  "eventNamePairs": {
   "key": []
  },
  "eventid": "1"
 }
}
{% endhighlight %}

Sample Responses
----------------

### XML

{% highlight voltMx %}            1\. Success Response:

<messageResponse>
    <code>200</code>
    <description>Request Queued. </description>
    <messages>
        <message  msgId="xxxx" ></message>
    </messages>
</messageResponse>

2. Invalid Subscribers:

<messageResponse>
    <code>200</code>
    <description>Request Queued. </description>
    <invalidSubscribers>
        <subscriber ksid=xxxx></subscriber>
        <subscriber ksid=xxxx></subscriber>
    </invalidSubscribers>
    <messages>
        <message  msgId="-1" ></message>
    </messages>
</messageResponse>

3. Invalid request format:

<messageResponse>
    <code>400</code>
    <description>Invalid request format.</description>
    <messages></messages>
</messageResponse>

4. If Associated Application is Invalid: 

<messageResponse>
    <code>404</code>
    <description>Invalid Volt MX Application ID associated with Event.</description>
    <messages></messages>
</messageResponse>

5. If Associated Applications is Not Published: 

<messageResponse>
    <code>405</code>
    <description>Associated Application is not Published.</description>
    <messages></messages>
</messageResponse>

6. Invalid Event: 

<messageResponse>
    <code>406</code>
    <description>Invalid Volt MX Event ID. </description>
    <messages></messages>
</messageResponse>

7. If Event Not Published: 

<messageResponse>
    <code>407</code>
    <description>Event is not Published.</description>
    <messages></messages>
</messageResponse>

8. Server Error: 

<messageResponse>
    <code>500</code>
    <description>Server failed to process the request.</description>
    <messages></messages>
</messageResponse>
{% endhighlight %}

### JSON

{% highlight voltMx %}            1.SuccessResponse: {
  "messageResponse": {
    "invalidSubscribers": [
      
    ],
    "description": "Request Queued. ",
    "code": 200,
    "messages": [
      {
        "msgId": xxxx
      }
    ]
  }
}2.InvalidSubscribers: {
  "messageResponse": {
    "invalidSubscribers": [
      {
        "ufid": ,
        "ksid": xxxx,
        "deviceId": 
      },
      {
        "ufid": ,
        "ksid": xxxx,
        "deviceId": 
      }
    ],
    "description": "Request Queued. ",
    "code": 200,
    "messages": [
      {
        "msgId": xxxx
      }
    ]
  }
}3.Invalidrequestformat: {
  "messageResponse": {
    "invalidSubscribers": [
      
    ],
    "description": "Invalid request format. ",
    "code": 400,
    "messages": [
      
    ]
  }
}4.IfAssociatedApplicationisInvalid: {
  "messageResponse": {
    "invalidSubscribers": [
      
    ],
    "description": "Invalid Volt MX Application ID associated with Event.",
    "code": 404,
    "messages": [
      
    ]
  }
}5.IfAssociatedApplicationsisNotPublished: {
  "messageResponse": {
    "invalidSubscribers": [
      
    ],
    "description": "Associated Application is not Published.",
    "code": 405,
    "messages": [
      
    ]
  }
}6.InvalidEvent: {
  "messageResponse": {
    "invalidSubscribers": [
      
    ],
    "description": "Invalid Volt MX Event ID. ",
    "code": 406,
    "messages": [
      
    ]
  }
}7.IfEventNotPublished: {
  "messageResponse": {
    "invalidSubscribers": [
      
    ],
    "description": "Event is not Published.",
    "code": 407,
    "messages": [
      
    ]
  }
}8.ServerError: {
  "500": "Server failed to process the request."
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| 200 | Request queued |
| 400 | Invalid request format |
| 405 | Associated application is not published |
| 406 | Invalid Volt MX event ID |
| 407 | Event is not published |
| 500 | Server failed to process the request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
