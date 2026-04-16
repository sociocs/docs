---
title: Get subscription
order: -400
data:
    path: "/webhook-subscriptions"
    path_for_sample: "/webhook-subscriptions/ABC1234567890XYZ"
---

Get a subscription.

## Method

[!badge GET]

## Path

`{{path}}/[subscription_id]`

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
data | Subscription object. See below | Only present when status is `success`

#### Subscription object

{{include "object-table/subscription"}}

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
