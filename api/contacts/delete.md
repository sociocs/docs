---
title: Delete contact
order: -500
data:
    path: "/contacts/[phone_number]"
    path_for_sample: "/contacts/16175551212"
---

Delete a contact.

## Method

[!badge DELETE]

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
curl --location --request DELETE '{{apiBaseUrl}}{{path_for_sample ?? path}}' \
{{include "curl/header-apikey"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "list_id_": 0
}'
```

+++
