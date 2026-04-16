---
title: Unsubscribe
order: -500
data:
    path: "/webhook-subscriptions/[subscription_id]"
    path_for_sample: "/webhook-subscriptions/ABC1234567890XYZ"
---

Unsubscribe a webhook to stop receiving messages.

## Method

[!badge DELETE]

## Path

`{{path}}`

## Path parameter

{.compact}
Name | Value | Required?
--- | --- | ---
subscription_id | Subscription ID | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

{.compact}
Name | Value | Remarks
--- | --- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}

## Code sample

+++ cURL

```shell
{{include "curl/delete"}}
```

+++
