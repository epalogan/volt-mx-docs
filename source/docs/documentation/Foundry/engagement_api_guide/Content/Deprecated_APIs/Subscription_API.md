---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Subscription
============

To register a subscriber, Volt MX Foundry Engagement Services calls Subscription API with subscription payload and sends the requested pushes to the subscriber. The Subscription API returns a unique KSID for the subscriber that can be used for sending pushes or updating geolocations or unsubsciptions.

> **_Important:_** The Subscription API is maintained here to preserve backward compatibility. We encourage you to use [Create/Modify Subscriber](../REST_API_Subscribers/Create_New_Subscriber.html)

URL
---

The HTTP URL for Subscription API is:

{% highlight voltMx %}http://<host or ip>:<port>/vpns/subscription
{% endhighlight %}

Method
------

POST

Content Type
------------

Based on the content format, the payload's request header includes "Content-Type" for:

*   **XML** is text/xml;charset=UTF-8
*   **JSON** is application/json;charset=UTF-8

Sample Request
--------------

### XML

#### XML syntax for generic

{% highlight voltMx %}<?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
  <subscribe>
    <appId>xxxxx</appId>  
    <deviceId>xxxx</deviceId>
    <ufid>xxxx</ufid>
    <sid>xxxxx</sid>
    <osType>xxxx</osType>  
**<!-- enable authToken if you want to enable security -->**  
 <authToken>xxxx</authToken>  
  </subscribe>
</subscriptionService>

{% endhighlight %}

#### XML syntax for iOS

*   The following subscription request is sent from an iPhone.

{% highlight voltMx %}<?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
  <subscribe>
    <appId>xxxxx</appId>  
    <deviceId>xxxx</deviceId>
    <ufid>xxxx</ufid>
    <sid>xxxxx</sid>  
 <osType>iphone</osType>  
**<!-- enable authToken if you want to enable security -->**  
    <authToken>xxxx</authToken>  
</subscribe>
</subscriptionService>
{% endhighlight %}

*   The following subscription request is sent from an iPad.

{% highlight voltMx %}<?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
  <subscribe>
    <appId>xxxxx</appId>
    <deviceId>xxxx</deviceId>
    <ufid>xxxx</ufid>
    <sid>xxxxx</sid>
   <osType>ipad</osType>
    <authToken>xxxx</authToken>  
</subscribe>
</subscriptionService>
{% endhighlight %}

#### XML syntax for Android

Any one of the following two syntax can be used.

*   The following subscription request is sent from Android.

{% highlight voltMx %}<?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
  <subscribe>
    <appId>xxxxx</appId>  
  
    <deviceId>xxxx</deviceId>
    <ufid>xxxx</ufid>
    <sid>xxxxx</sid>
   <osType>androidgcm</osType>  
**<!-- enable authToken if you want to enable security -->**  
    <authToken>xxxx</authToken>  
</subscribe>
</subscriptionService>   
{% endhighlight %}

*   The following subscription request is sent from androidgcm

{% highlight voltMx %}<?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
  <subscribe>
    <appId>xxxxx</appId>  
  
    <deviceId>xxxx</deviceId>
    <ufid>xxxx</ufid>
    <sid>xxxxx</sid>
    <osType>android</osType>
  <isGCM>true</isGCM>  
**<!-- enable authToken if you want to enable security -->**  
   <authToken>xxxx</authToken>  
  </subscribe>
</subscriptionService>

{% endhighlight %}

#### XML syntax for BlackBerry

{% highlight voltMx %}<?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
    <subscribe>
        <appId>xxxxx</appId>
        <deviceId>xxxx</deviceId>
        <ufid>xxxx</ufid>
        <sid>xxxxx</sid>
        <osType>blackberry</osType>
        <!-- enable authToken if you want to enable security -->
        <authToken>xxxx</authToken>
    </subscribe>
</subscriptionService>
{% endhighlight %}

#### XML syntax for Windows 8 Phones (Windows Phone Notification Services)

{% highlight voltMx %}<?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
    <subscribe>
        <appId>xxxxx</appId>
        <deviceId>xxxx</deviceId>
        <ufid>xxxx</ufid>
        <sid>xxxxx</sid>
        <osType>windows</osType>
        <!-- enable authToken if you want to enable security -->
        <authToken>xxxx</authToken>
    </subscribe>
</subscriptionService>
{% endhighlight %}

#### XML syntax for Windows RT and PRO (Tablets) (Windows Notification Services)

{% highlight voltMx %}            
            <?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
    <subscribe>
        <appId>xxxxx</appId>
        <deviceId>xxxx</deviceId>
        <ufid>xxxx</ufid>
        <sid>xxxxx</sid>
        <osType>windows8</osType>
        <!-- enable authToken if you want to enable security -->
        <authToken>xxxx</authToken>
    </subscribe>
</subscriptionService>
{% endhighlight %}

#### XML syntax for Web

{% highlight voltMx %}            
            <?xml version='1.0' encoding='UTF-8'?>
<subscriptionService>
  <subscribe>
    <appId>xxxxx</appId>  
  
    <deviceId>xxxx</deviceId>
    <ufid>xxxx</ufid>
    <sid>xxxxx</sid>
    <osType>webfcm</osType>
  <isGCM>true</isGCM>  
**<!-- enable authToken if you want to enable security -->**  
   <authToken>xxxx</authToken>  
  </subscribe>
</subscriptionService>

{% endhighlight %}

### JSON

#### JSON syntax for generic

{% highlight voltMx %}{
 "subscriptionService": {
  "subscribe": {
   "sid": "xxxx",
   "appId": "VoltMX Foundry MessagingDEV",
   "ufid": "xxxx",  
**//enable authToken if you want to enable security**  
   "authToken": "xxxx",  
   "osType": "xxxx",  
  
 **"deviceId": "xxxx"
  }
 }
}**
{% endhighlight %}

#### JSON syntax for iOS

*   The following subscription request is sent from an iPhone.

{% highlight voltMx %}{
   "subscriptionService": {
   "subscribe": {
   "sid": "xxxx",
   "appId": "xxxxx",
   "ufid": "xxxx",
   "osType": "iphone",  
  
   "deviceId": "xxxx"
  }
 }
}
{% endhighlight %}

*   The following subscription request is sent from an iPad.

{% highlight voltMx %}{
   "subscriptionService": {
   "subscribe": {
   "sid": "xxxx",
   "appId": "xxxxx",
   "ufid": "xxxx",
   "osType": "ipad",  
   "deviceId": "xxxx"
  }
 }
}
{% endhighlight %}

#### JSON syntax for Android

Any one of the following two syntax can be used.

*   The following subscription request is sent from Android.

{% highlight voltMx %}{
  "subscriptionService": {
  "subscribe": {
   "sid": "xxxx",
   "appId": "xxxxx",
   "ufid": "xxxx",
   "osType": "androidgcm",  
   "deviceId": "xxxx"
  }
 }
}
{% endhighlight %}

*   The following subscription request is sent from androidgcm.

{% highlight voltMx %}{
 "subscriptionService": {
  "subscribe": {
   "sid": "xxxx",
   "appId": "xxxxx",
   "ufid": "xxxx",
   "osType": "android",  
   "isGCM": "true",  
   "deviceId": "xxxx"  
  }
 }
}
{% endhighlight %}

#### JSON syntax for BlackBerry

{% highlight voltMx %}//BlackBerry
{
  "subscriptionService": {
    "subscribe": {
      "sid": "xxxx",
      "appId": "xxxxx",
      "ufid": "xxxx",
      "osType": "blackberry",
      "deviceId": "xxxx"
    }
  }
}
{% endhighlight %}

#### JSON syntax for Windows 8 Phones (Windows Phone Notification Services)

{% highlight voltMx %}{
  "subscriptionService": {
    "subscribe": {
      "sid": "xxxx",
      "appId": "xxxxx",
      "ufid": "xxxx",
      "osType": "windows",
      "deviceId": "xxxx"
    }
  }
}
{% endhighlight %}

#### JSON syntax for Windows RT & PRO (Tablets) (Windows Notification Services)

{% highlight voltMx %}            
            {
  "subscriptionService": {
    "subscribe": {
      "sid": "xxxx",
      "appId": "xxxxx",
      "ufid": "xxxx",
      "osType": "windows8",
      "deviceId": "xxxx"
    }
  }
}
{% endhighlight %}

#### JSON syntax for Web

{% highlight voltMx %}{
 "subscriptionService": {
  "subscribe": {
   "sid": "xxxx",
   "appId": "xxxxx",
   "ufid": "xxxx",
   "osType": "android",  
   "isGCM": "true",  
   "deviceId": "xxxx"  
  }
 }
}
{% endhighlight %}

Input Parameters
----------------

The following fields are input parameters:

  
| Parameter | Required | Description |
| --- | --- | --- |
| appID | Mandatory | App ID is configured in Volt MX Foundry Messaging for your App |
| deviceId | Mandatory | This is the device ID used for sending the pushes to the device. For iOS devices, this value is same as sid. For other devices use Volt MX JavaScript API (voltmx.os.deviceInfo().deviceid) to get these details from app.For BlackBerry, the returned device ID is in hex decimal format and BlackBerry accepts pushes for the values by omitting first two characters from the device ID. So you need to send device ID by omitting the first two characters. For example, Device ID returned from BlackBerry device is 0x2b631c8d, but the device ID to be sent to Volt MX Foundry Engagement Services (or in fact to send pushes to BlackBerry devices) must be 2b631c8d |
| ufid | Optional | The User Friendly Identifier or UFID is used when you subscribe to Volt MX Foundry Engagement Services. Based on your requirement, you can provide an UFID. It is alphanumeric, for example xxx@voltmx.com or 2890XZCY. It can be used to map devices to the user using the value as a reconciliation key |
| sid | Mandatory. | This is the subscription ID returned by the respective device clouds |
| osType | Mandatory. | Allowed values based on a device are iPhone, iPad, androidgcm, android(use in conjunction with fields <isGCM>true/false</isGCM>), BlackBerry, Windows(for Windows 8 Phones ), Windows8 (for Windows RT and PRO (Tablets)), webfcm |
| authToken | Mandatory if security is enabled for Volt MX Foundry Engagement Servicessubscription | This value ensures, if the subscription request is from a valid source. The validity of the subscription request is ensured by matching auth token value provided in subscription service with the value configured in the Volt MX Foundry Engagement Services. This value is configured in Volt MX Foundry Engagement Services using basic details API or from Settings section from Console "Auth token for subscription API". |

### Sample Responses

#### XML

{% highlight voltMx %}            1\. Subscription Success Response:

<subscriptionResponse>
    <statusCode>200</statusCode>
    <ksid>xxxx</ksid>
    <message>Subscription successful. </message>
</subscriptionResponse>

2. Subscription Update Success Response:

<subscriptionResponse>
    <statusCode>200</statusCode>
    <ksid>xxxx</ksid>
    <message>Update successful.  </message>
</subscriptionResponse>

3. Duplicate Subscription: 

<subscriptionResponse>
    <statusCode>201</statusCode>
    <ksid>xxxx</ksid>
    <message>Duplicate subscription. SID element has the ID of existing subscription.  </message>
</subscriptionResponse>

4. If Application ID is Invalid: 

<subscriptionResponse>
    <statusCode>404</statusCode>
    <ksid>-1</ksid>
    <message>Invalid Application ID. </message>
</subscriptionResponse>

5. If Request is invalid: 

<subscriptionResponse>
    <statusCode>400</statusCode>
    <ksid>-1</ksid>
    <message>Invalid request format.  </message>
</subscriptionResponse>

6. If Authentical Token is invalid: 

<subscriptionResponse>
    <statusCode>401</statusCode>
    <ksid>-1</ksid>
    <message>Unauthorized request. The authToken is invalid.   </message>
</subscriptionResponse>

7. If subscription is unclear: 

<subscriptionResponse>
    <statusCode>403</statusCode>
    <ksid>-1</ksid>
    <message>Subscription unclear. Found multiple subscriptions with given input. Check your SID and DEVICE ID</message>
</subscriptionResponse>

8. Server Error: 

<subscriptionResponse>
    <statusCode>500</statusCode>
    <ksid>-1</ksid>
    <message>Server failed to process the request. </message>
</subscriptionResponse>
{% endhighlight %}

### JSON

{% highlight voltMx %}            1. SubscriptionSuccessReponse:  
 {
  "subscriptionResponse": {
    "statusCode": "200",
    "ksid": "xxxx",
    "message": "Subscription successful."
  }
}  
2. SubscriptionUpdateSuccessReponse:  
 {
  "subscriptionResponse": {
    "statusCode": "200",
    "ksid": "xxxx",
    "message": "Update successful."
  }
}  
3. UnsubscriptionSuccessResponse:   
{
  "subscriptionResponse": {
    "statusCode": "200",
    "ksid": "xxxx",
    "message": "Unsubscription successful."
  }
}  
4. Ifalreadyunsubscribed:  
 {
  "subscriptionResponse": {
    "statusCode": "200",
    "ksid": "xxxx",
    "message": "Already unsubscribed."
  }
}  
5. DuplicateSubscription:  
 {
  "subscriptionResponse": {
    "statusCode": "201",
    "ksid": "xxxx",
    "message": "Duplicate subscription. SID element has ID of existing subscription."
  }
}  
6. IfApplicationIdisInvalid:  
 {
  "subscriptionResponse": {
    "statusCode": "404",
    "ksid": "-1",
    "message": "Invalid Application ID."
  }
}  
7. IfRequestisinvalid:   
{
  "subscriptionResponse": {
    "statusCode": "400",
    "ksid": "-1",
    "message": "Invalid request format."
  }
}  
8.IfAuthenticalTokenisinvalid:  
 {
  "subscriptionResponse": {
    "statusCode": "401",
    "ksid": "-1",
    "message": "Unauthorized request. The authToken is invalid."     }
}  
9\. Ifsubscriptionisunclear:  
 {
  "subscriptionResponse": {
    "statusCode": "403",
    "ksid": "-1",
    "message": "Subscription unclear. Found multiple subscriptions with given input. Check your SID and DEVICE ID "
  }
}  
10.ServerError: {
  "subscriptionResponse": {
    "statusCode": "500",
    "ksid": "-1",
    "message": "Server failed to process the request. "
  }
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| 200 | Update successful |
| 200 | Subscription successful |
| 201 | Duplicate subscription. SID element has ID of existing subscription |
| 400 | Invalid request format |
| 401 | Unauthorized request. The authToken is invalid |
| 403 | Subscription unclear. Found multiple subscriptions with given input. Check your SID and DEVICE ID |
| 404 | Invalid Volt MX Application ID |
| 404 | No valid subscription exists |
| 500 | Server failed to process the request. |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
