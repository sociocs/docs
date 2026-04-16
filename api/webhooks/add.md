---
title: Subscribe
order: -200
data:
    path: "/webhook-subscriptions"
---

Subscribe a webhook endpoint to receive incoming messages received on your channel. You can also subscribe to status updates for outgoing messages.

## Method

[!badge POST]

## Path

`{{path}}`

## Body parameters

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
platform | A value that identifies the platform hosting the endpoint (e.g., "salesforce") | String | Yes
{{include "param-row/provider"}}
{{include "param-row/channel-key"}}
events | Array of event types to listen to. <br />`messages` to receiving incoming messages, <br /> `status_updates` to receive status updates for outgoing messages. | Array of string | No. Defaults to `["messages"]`.
subscriber_reference_id | Unique identifier for the subscription. If you call the API again with the same value for this field, it will update the existing subscription. | String | Yes
webhook_url | Webhook endpoint URL | String | URL

!!! info
If you call this API with the same `subscriber_reference_id`, it will update the existing subscription.
!!!

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

{.compact}
Name | Value | Remarks
--- | --- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Object `{ id: [subscription id]}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/post"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "platform": "salesforce",
    "provider": "twlo",
    "channel_key": "[your channel key]",
    "events": ["messages", "status_updates"],
    "subscriber_reference_id": "ABC1234567890XYZ",
    "webhook_url": "https://example.com/incoming"  
}'
```

+++
