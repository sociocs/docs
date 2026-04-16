---
title: Get contact
order: -300
data:
    path: "/contacts/[phone_number]"
    path_for_sample: "/contacts/16175551212"
---

Get a contact.

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
data | Object with the contact fields | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
