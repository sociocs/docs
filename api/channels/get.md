---
title: Get channel
order: -200
data:
    path: "/channels/[channel_key]"
    path_for_sample: "/channels/your_channel_key"
---

Get a channel.

## Method

[!badge GET]

## Path

`{{path}}`

## Path parameter

Name | Value | Data type | Required? {class="compact"}
--- | ---
{{include "param-row/channel-key"}}

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Channel object. See below. | Only present when status is `success`

#### Channel object

Name | Value {class="compact"}
--- | ---
name | Channel name
country_code | Country dial code of the phone number connected in the channel
phone_number | Phone number connected in the channel
provider | Messaging provider for the channel <br />{{include "providers"}}

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
