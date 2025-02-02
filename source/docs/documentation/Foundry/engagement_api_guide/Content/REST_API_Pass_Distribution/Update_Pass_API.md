---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Update Pass
===========

The Update Pass API only updates a scheduled pass.

> **_Note:_** To update passes that have been sent, use the Pass Distribution API with multiple passes in a single request.

URL
---

The HTTP URL for the Update Pass API is:

{% highlight voltMx %}http://<<host>>:<<port>>/api/v1/message/pass/update
{% endhighlight %}

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
| recipients |   |   |   | An array of recipients objects |
|   | recipient:-ID |   | string | An array of recipient objects:Unique id assigned to a recipient |
| passContent |   |   |   | An array of passContent objects |
|   | basicDetails |   |   | An array of basicDetails objects. For more details, [see](Pass_Distribution_main.html#passtemplates) |
|   | appearance |   |   | An array of appearance objects. For more details, [see](Pass_Distribution_main.html#appearance_for_dist) |
|   | frontLayout |   |   | An array of frontLayout objects. For more details, [see](Pass_Distribution_main.html#frontLayout_for_dist) |
|   | backLayout |   |   | An array of backLayout objects. For more details, [see](Pass_Distribution_main.html#backLayout_for_dist) |
|   | passRelevance |   |   | An array of passRelevance objects. For more details, [see](Pass_Distribution_main.html#passRelevance_for_dist) |
|   | passRules |   |   | An array of passRules objects. For more details, [see](Pass_Distribution_main.html#passRules_for_dist) |
|   | languageDetails |   |   | An array of languageDetails objects. For more details, [see](Pass_Distribution_main.html#languageDetails_for_dist) |

Sample Request
--------------

{% highlight voltMx %}{
  "recipients": {
    "recipient": [
      {
        "id": "48494"
      }
    ]
  },
  "passContent": {
    "basicDetails": {
      "passType": "A Constant value applicable for PassType",
      "passTypeIdentifier": "",
      "passSerialNumberType": "A Constant value applicable for PassSerialNumberType",
      "passSerialNumber": "",
      "groupIdentifier": "",
      "appLaunchURL": "",
      "ituneIdentifiers": "Comma separated iTunes Identifier values.",
      "customJsonData": "",
      "timezone": "A Constant value applicable for TimeZones",
      "organizationName": "",
      "description": ""
    },
    "appearance": {
      "bgColor": "the color value in hexadecimal",
      "labelColor": "the color value in hexadecimal",
      "valueColor": "the color value in hexadecimal",
      "suppressStripShine": true/false,
      "images": [
        {
          "imageType": "A Constant value applicable for ImageType",
          "blob": trueifyouareuploadingimageorusingimageId,
          Falseifyouareprovidinglink.,
          "url": "url of the image",
          "imageId": "the image id stored in Volt MX Foundry Messaging system",
          "imageFieldName": "name of the field from the request parameters that is applicable here"
        }
      ]
    },
    "frontLayout": {
      "logoText": "",
      "transitType": "A Constant value applicable for TransitType",
      "headerFields": [
        arrayoffieldswithstructure{
          "label": "",
          "data": "",
          "dataType": "A Constant value applicable for PassDataType",
          "numberFormat": "A Constant value applicable for NumberFormatType",
          "currency": "A Constant value applicable for CurrencyFormat",
          "dateTimeFormat": "A Constant value applicable for DateFormatType",
          "displayRelatively": true/false,
          "ignoreTimezone": true/false,
          "alignment": "A Constant value applicable for PassFieldAlignment",
          "autolink": "A Constant value applicable for DataDetectorType",
          "key": ""
        }
      ],
      "primaryFields": [
        arrayoffieldswithstructure{
          "label": "",
          "data": "",
          "dataType": "A Constant value applicable for PassDataType",
          "numberFormat": "A Constant value applicable for NumberFormatType",
          "currency": "A Constant value applicable for CurrencyFormat",
          "dateTimeFormat": "A Constant value applicable for DateFormatType",
          "displayRelatively": true/false,
          "ignoreTimezone": true/false,
          "alignment": "A Constant value applicable for PassFieldAlignment",
          "autolink": "A Constant value applicable for DataDetectorType",
          "key": ""
        }
      ],
      "auxiliaryFields": [
        arrayoffieldswithstructure{
          "label": "",
          "data": "",
          "dataType": "A Constant value applicable for PassDataType",
          "numberFormat": "A Constant value applicable for NumberFormatType",
          "currency": "A Constant value applicable for CurrencyFormat",
          "dateTimeFormat": "A Constant value applicable for DateFormatType",
          "displayRelatively": true/false,
          "ignoreTimezone": true/false,
          "alignment": "A Constant value applicable for PassFieldAlignment",
          "autolink": "A Constant value applicable for DataDetectorType",
          "key": ""
        }
      ],
      "secondaryFields": [
        arrayoffieldswithstructure{
          "label": "",
          "data": "",
          "dataType": "A Constant value applicable for PassDataType",
          "numberFormat": "A Constant value applicable for NumberFormatType",
          "currency": "A Constant value applicable for CurrencyFormat",
          "dateTimeFormat": "A Constant value applicable for DateFormatType",
          "displayRelatively": true/false,
          "ignoreTimezone": true/false,
          "alignment": "A Constant value applicable for PassFieldAlignment",
          "autolink": "A Constant value applicable for DataDetectorType",
          "key": ""
        }
      ],
      "barcodeDetails": {
        "barcodeType": "A Constant value applicable for BarcodeType",
        "embeddedMessageType": "A Constant value applicable for barcodeType BarcodeMsgType",
        "message": "",
        "alternativeTextType": "A Constant value applicable for barcodeType BarcodeAltTextType",
        "alternateText": "",
        "embeddedFormat": "A Constant value applicable for barcodeType EncodingType"
      }
    },
    "backLayout": {
      "fields": [
        arrayoffieldswithstructure{
          "label": "",
          "data": "",
          "dataType": "A Constant value applicable for PassDataType",
          "numberFormat": "A Constant value applicable for NumberFormatType",
          "currency": "A Constant value applicable for CurrencyFormat",
          "dateTimeFormat": "A Constant value applicable for DateFormatType",
          "displayRelatively": true/false,
          "ignoreTimezone": true/false,
          "alignment": "A Constant value applicable for PassFieldAlignment",
          "autolink": "A Constant value applicable for DataDetectorType",
          "key": ""
        }
      ]
    },
    "passRelevance": {
      "relevantDate": "09/18/2014 12:00:00 AM",
      "ignoreTimezone": true/false,
      "relevantLocations": [
        arrayoflocationswithstructure{
          "id": ##idofthelocationstoredinVoltMXFoundryMessaging##,
          "relevantText": "Relevant text to appear when user is in the given location"
        }
      ],
      "maxDistance": Maxradialdistancethatthepassisapplicablefortheabovegivenlocations,
      "relevantBeacons": [
        arrayofbeaconswithstructure{
          "id": ##idofthebeaconstoredinVoltMXFoundryMessaging##,
          "relevantText": "Relevant text to appear when user is in the given beacon region"
        }
      ]
    },
    "passRules": {
      "dateRestriction": "A Constant value applicable for PassDateRestriction",
      "stopAfter": "",
      "expiryDate": "09/26/2014 07:00:00 AM",
      "voided": true/false
    },
    "languageDetails": {
      "originalFields": [
        "field1",
        "field2",
        "field3".......
      ],
      "languageEntries": [
        Arrayoflanguageentries{
          "language": "A Constant value applicable for Language",
          "data": [
            Arrayoftranslationsfortheselectedlanguage{
              "localText": "translation for field1"
            },
            {
              "localText": "translation for field2"
            },
            {
              "localText": "translation for field3"
            }
          ],
          "images": [
            arrayofimagesfortheselectedlanguagewithstructure{
              "imageType": "A Constant value applicable for ImageType",
              "blob": trueifyouareuploadingimageorusingimageId,
              Falseifyouareprovidinglink.,
              "url": "url of the image",
              "imageId": "the image id stored in Volt MX Foundry Messaging system",
              "imageFieldName": "name of the field from the request parameters that is applicable here"
            }
          ]
        }
      ],
      "passLanguage": "A Constant value applicable for Language"
    }
  },
  "passIntegrationConfig": {
    "passIssueNotificationDetails": [
      {
        "channel": "SMS",
        "enabled": true/false,
        "messageContent": "Content of your email. Using place holder ##SMS Pass Link## will generate pass download link."
      },
      {
        "channel": "EMAIL",
        "enabled": true/false,
        "messageContent": "Content of your email. Using place holder ##Email Pass Link## will generate pass download link.",
        "subject": "subject for the mail",
        "senderName": "The email will be sent on this name",
        "senderEmail": "The email will be sent from this Email ID"
      }
    ],
    "passUpdateNotificationDetails": [
      {
        "channel": "SMS",
        "enabled": true/false,
        "messageContent": "SMS to be sent when the user downloads the pass."
      },
      {
        "channel": "EMAIL",
        "enabled": true/false,
        "messageContent": "Email to be sent when the user downloads the pass.",
        "subject": "subject for the mail",
        "senderName": "The email will be sent on this name",
        "senderEmail": "The email will be sent from this Email ID"
      }
    ]
  },
  "priority": true,
  "startTimeStamp": 0,
  "endTimeStamp": 0
}
{% endhighlight %}

Sample Response
---------------

{% highlight voltMx %}{"requestId":"2318508739642895844","description":"Request Queued. "}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Request queued |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">AU</td></tr></tbody></table>
