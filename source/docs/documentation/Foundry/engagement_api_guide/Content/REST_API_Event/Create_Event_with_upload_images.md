---
layout: "documentation"
category: "engagement_api_guide"
---
                            


Create Pass Event with Upload Images
====================================

The **Create Pass Event with Upload Images** API is used to create an event with your custom images, which are not available as part of the web URL reference.

Use Case
--------

If you wish to create a pass with uploaded images instead of providing the image URL, then you need to post the input parameters as given below:

1.  Send the form data as a key-value pair.
    1.  Post the complete payload as a key-value pair (eventPayload : payload body in the text format)
    2.  Post the image details as a key value pair such as logo: selected file format from the image location.

URL
---

The HTTP URL for **Create Event with Upload Images** API is:

{% highlight voltMx %}http://<<host>>:<<port>>/api/v1/events
{% endhighlight %}

This service implements Gateway Filter for Authentication to authenticate access of the service by a user.

Method
------

POST

Input Parameters
----------------

The following fields are input parameters:

  
| Input Parameter | Level – Two | Required | Type | Description |
| --- | --- | --- | --- | --- |
| name |   | Yes | string | The unique name assigned to an event. |
| description |   | Yes | string | Event description defining objective of the event. |
| Event Type |   | Optional | string | The event type assigned with an event. |
| eventPass |   |   |   | An array of eventPass objects. For more details, [see](Event.html#passtemplatedata) |
| eventPushes |   |   |   | An array of eventPushes objects including platform specific properties. For more details, [see](Event.html#eventpushes) |
|   | platformSpecificProps |   |   | An array of platformSpecificProps properties. For more details, [see](Event.html#platformspecificprops-output-parameters) |
| eventMails |   |   |   | An array of eventMails objects. For more details, [see](Event.html#eventmails) |
| eventSms |   |   |   | An array of eventSms objects. For more details, [see](Event.html#eventsms) |

Sample Request
--------------

{% highlight voltMx %}            
            {
	"name": "eBay Online Shopping June 2017",
	"description": "online shopping Home Goods",
	"eventType": "",
	"eventPass": {
		"id": 1,
		"passName": "eBay Summer Sale coupons",
		"subscribers": "",
		"passOpened": "",
		"passSent": "",
		"passContent": {
			"basicDetails": {
				"passTypeIdentifier":   
"pass.com.vms.xxxxxxxxx",
				"passSerialNumber": "",
				"groupIdentifier": "",
				"appLaunchURL": "",
				"ituneIdentifiers": "",
				"webServiceUrl":   
"http://localhost:xxxx/vpns/",
				"timezone": "  
(GMT-05:00) Eastern Time (US &amp; Canada)",
				"passType": "COUPON",
				"organizationName": "eBay",
				"description": "Online shopping",
				"passSerialNumberType": "AUTO_GEN",
				"eventTicketType": "",
				"customJsonData": {}
			},
			"appearance": {
				"bgColor": "#64798c",
				"labelColor": "#ccdae9",
				"valueColor": "#ffffff",
				"suppressStripShine": false,
				"images": [{
					"blob": true,
					"extension": "png",
					"imageType": "ICON",
					"imageFieldName": "icon"
				}]
			},
			"frontLayout": {
				"logoText": "eBay",
				"headerFields": [{
					"label": "Computer",
					"data": "Laptops",
					"changeMessage": "",
					"displayRelatively": false,
					"ignoreTimezone": false,
					"key": "Summer Sale 2016",
					"dataType": "TEXT",
					"numberFormat": "",
					"currency": "",
					"dateTimeFormat": "",
					"alignment": "LEFT",
					"autolink": []
				}],
				"primaryFields": [],
				"auxiliaryFields": [],
				"secondaryFields": [],
				"barcodeDetails": {
					"message": "",
					"alternateText": "",
					"barcodeType": "PDF417",
					"embeddedMessageType":   
"PASS_SERIAL_NO",
					"alternativeTextType":  
 "BARCODE_CONTENTS",
					"embeddedFormat": "UTF_8"
				},
				"transitType": ""
			},
			"backLayout": {
				"fields": [{
					"label": "Electronic Goods ",
					"data": "Laptops and Gadgets",
					"changeMessage": "",
					"displayRelatively": false,
					"ignoreTimezone": false,
					"key": "Electronic",
					"dataType": "TEXT",
					"numberFormat": "",
					"currency": "",
					"dateTimeFormat": "",
					"alignment": "",
					"autolink": []
				}],
				"enableAutoUpdates": false
			},
			"passRelevance": {
				"relevantDate": "",
				"ignoreTimezone": false,
				"relevantLocations": [],
				"relevantBeacons": [],
				"maxDistance": ""
			},
			"passRules": {
				"stopAfter": "06/30/2016 12:00:00 AM",
				"expiryDate": "",
				"voided": false,
				"dateRestriction":"DONOT_ISSUE_AFTER"
			},
			"languageDetails": {
				"originalFields": [],
				"languageEntries": [],
				"passLanguage": "EN"
			}
		},
		"passIntegrationConfig": {
			"passIssueNotificationDetails": [{
				"channel": "SMS",
				"enabled": true,
				"messageContent": "shopping 2016",
				"subject": "",
				"senderName": "",
				"senderEmail": ""
			}]
		}
	},
	"registrationId": "4928500176715381493",
	"eventPushes": [{
		"messageName": "summer sale",
		"message": "##First Name####Last Name##",
		"richContent": "",
		"platformSpecificProps": {
			"title": "June 16 sale",
			"iphone": {
				"badge": "1",
				"sound": "sound.mp4",
				"category": "",
				"contentAvailable": "1",
				"actionLocKey": "actionkey",
				"locKey": "",
				"locArgs": {
					"locArg": "locArg"
				},
				"launchImage": "",
				"title": "June 216 sale",
				"titleLocKey": "",
				"titleLocArgs": {
					"titleLocArg": "titleLocArg"
				},
				"customData": {
					"key": []
				}
			},
			"blackberry": {
				"header": []
			},
			"android": {
				"title": "June 216 sale"
			},
			"jpush": {
				"key": [{
					"name": "title",
					"value": "June 216 sale"
				}]
			},
                      "web": {
				"title": "June 216 sale"
			},
			"windows": {
				"notificationType": "TOAST",
				"text1": "June 16 sale",
				"text2":"##Last Name##",
				"screenName": "",
				"params": {
					"key": []
				},
				"title": "",
				"badge": "",
				"imagePath": ""
			},
			"wns": {
				"notificationType": "TOAST",
				"text1": "June 16 sale",
				"text2": "##Last Name##"
			}
		},
		"appId": "20096-6548262167",
		"subscribers": 0,
		"pushesSent": 0,
		"pushesOpened": 0
	}],
	"eventMails": [{
		"mailName": "eBay Online Shopping",
		"mailSubject": "summer sale 2016",
		"mailContent": "##Email##",
		"contentType": "text.html",
		"senderMailId": "aron.hale@voltmx.com",
		"senderMailName": "admin",
		"mailDesignsList": [],
		"subscribers": 0,
		"mailsOpened": 0,
		"mailsSent": 0
	}],
	"eventSms": [{
		"smsName": "summer sale 2016",
		"smsContent": "##Mobile Number##",
		"subscribers": 0,
		"smsSent": 0,
		"smsOpened": 0
	}]
}
{% endhighlight %}

Sample Response
---------------

{% highlight voltMx %}{
  "id" : "3",
  "message" : "Details added successfully"
}
{% endhighlight %}

Response Status
---------------

  
| Code | Description |
| --- | --- |
| Status 200 | Event created successfully |
| Status 400 | Invalid request format |
| Status 401 | Unauthorized request |
| Status 500 | Server failure to process request |

<table class="TableStyle-RevisionTable" cellspacing="0" style="margin-left: 0;margin-right: auto;mc-table-style: url('../Resources/TableStyles/RevisionTable.css');" data-mc-conditions="Default.HTML"><colgroup><col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"> <col class="TableStyle-RevisionTable-Column-Column1"></colgroup><tbody><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Rev</td><td class="TableStyle-RevisionTable-BodyE-Column1-Body1">Author</td><td class="TableStyle-RevisionTable-BodyD-Column1-Body1">Edits</td></tr><tr class="TableStyle-RevisionTable-Body-Body1"><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">7.1</td><td class="TableStyle-RevisionTable-BodyB-Column1-Body1">AU</td><td class="TableStyle-RevisionTable-BodyA-Column1-Body1">DR</td></tr></tbody></table>
