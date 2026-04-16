---
title: Information
order: -100
---

Webhooks are the REST APIs you created yourself or offered by a third-party software, which get called when a message is received in a Sociocs channel.

URL of the REST API is referred to as webhook endpoint. You can set multiple webhooks endpoints for the same channel, or the same webhook endpoint for multiple channels.

## Channels supporting webhooks

- SMS (with Telnyx)
- SMS (with Twilio)
- WhatsApp (with Gupshup)
- WhatsApp (with Twilio)

## How to set it up?

In order for Sociocs to start calling your webhook endpoint on receiving incoming messages, you need to subscribe the endpoint for a specific channel. You can add multiple webhooks for the same channel, or same webhook for multiple channels, depending upon your needs.

## Webhook endpoint invocation details

Sociocs calls the webhook endpoints with an assumption that it's a REST API accepting JSON body parameters.

### Method used

[!badge POST]

### New incoming message body parameters

{.compact}
Name | Value | Data type
--- | --- | ---
message_id | Message ID | String
event | `message` | String
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | String
channel_key | Channel key associated to the webhook | String
direction | `incoming` | String
from | Sending phone number | String
to | Receiving phone number | String
name | Sender's name (if available) | String
text | Message text | String
file_urls | Publicly accessible links to files in the message | Array of String
image_urls | Publicly accessible links to images in the message | Array of String
video_urls | Publicly accessible links to videos in the message | Array of String
contact | Object with contact details (if a contact with the 'from' phone number is found) | Object
timestamp | Timestamp as milliseconds since epoch. | Integer

#### Example 

```
{
  "message_id": "MM2aa0db1b276eaeaa5d730d5aa34167f2",
  "event": "message",
  "provider": "twlo",
  "channel_key": "twlo_16311113333",
  "direction": "incoming",
  "from": "16311112222",
  "to": "16311113333",
  "text": "Hello World!",
  "video_urls": [],
  "image_urls": [],
  "file_urls": [],
  "contact": {
    "id": 123,
    "name": "Emily Johnson",
    "phone_number": "16311112222",
    "phone_number_cc": "",
    "extra_fields": "{\"city\": \"Ahmedabad\", \"country\": \"India\"}",
    "created_at": "2025-07-11T11:29:46.000Z",
    "updated_at": "2025-08-04T12:29:21.000Z",
    "is_blocked": 0
  }
  "timestamp": 1754455905897,
}
```

### Outgoing message status updates body parameters

Name | Value | Data type
--- | --- | ---
message_id | Message ID | String
event | `status_update` | String
event_data | Object `{ status: "sent"|"delivered"|"read"|"failed", event: "status_update", error: [error details when failed]},  provider_err_obj: [error object from provider when failed] }` <br/><br/>Note: Only WhatsApp channels support the `read` status. | Object

#### Examples

#### Successfully sent message

```
{
  "message_id": "MM2aa0db1b276eaeaa5d730d5aa34167f2",
  "event": "status_update",
  "event_data": {
    "status": "sent"
  }
}
```

#### Successfully delivered message

```
{
  "message_id": "MM2aa0db1b276eaeaa5d730d5aa34167f2",
  "event": "status_update",
  "event_data": {
    "status": "delivered"
  }
}
```

#### Failed message

```
{
  "message_id": "MM2aa0db1b276eaeaa5d730d5aa34167f2",
  "event": "status_update",
  "event_data": {
    "status": "failed",
    "error": {
      "code": 21614,
      "message": "You have attempted to send a message to a number that is either a landline number or is an invalid number. (code: 21614)"
    },
    "provider_err_obj": {
      "status": 400,
      "code": 21614,
      "moreInfo": "https://www.twilio.com/docs/errors/21614",
      "error": true
    }
  }
}
```