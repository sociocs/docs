---
title: Save incoming message
order: -200
data:
    path: /incoming
---

Save a message in the inbox. You can use it to save a message received on an external platform or create a mock message with information you may need during the conversation.

## Method

[!badge POST]

## Path

`{{path}}`

## Body parameters

Name | Value | Data type | Required? {class="compact"}
--- | ---
provider | `twlo` (for Twilio SMS). No other providers supported yet. | String | Yes
channel_key | Channel key value from *Profile & settings -> API*  | String| Yes
from | {{include "api/phone-number-value"}} | String | Yes
name | Sender name | String | No
text | Message text | String | Yes
media_url | Publicly accessible image, video or file URL | String | No
media_type | MIME type of the media (e.g., `image/png`, `video/mp4`, `application/pdf`, etc). [!button variant="info" size="xs" target="blank" text="List of common MIME types"](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types) | String | Only when `media_url` is present

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}

## Code sample

+++ cURL

```shell
curl --location --request POST '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "provider": "[provider]",
    "channel_key": "[your channel key]",
    "from": "[phone number]",
    "name": "[sender name]",
    "text": "[message]"
}'
```

+++
