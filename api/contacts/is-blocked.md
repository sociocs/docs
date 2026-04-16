---
title: Is contact blocked
order: -800
data:
    path: /contacts/isblocked/[phone_number]
    path_for_sample: /contacts/isblocked/16175551212
---

Check if a contact is blocked.

## Method

[!badge GET]

## Path

`{{path}}`

## Path parameter

{.compact}
Name | Value | Required?
--- | --- | ---
phone_number | {{include "api/phone-number-value"}} | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

{.compact}
Name | Value | Remarks
--- | --- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Object `{ is_blocked: true | false}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
