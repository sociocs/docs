---
title: Unblock contact
order: -700
data:
    path: /contacts/unblock/[phone_number]
    path_for_sample: /contacts/unblock/16175551212
---

Unblock bulk & automated messages to a contact.

## Method

[!badge POST]

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

## Code sample

+++ cURL

```shell
{{include "curl/post"}}
```

+++
