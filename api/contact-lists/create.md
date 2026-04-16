---
title: Create contact list
order: -100
data:
    path: "/lists"
    path_for_sample: "/lists"
---

Create a new contact list.

## Method

[!badge POST]

## Path

`{{path}}`

## Body parameters

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
name | Contact list name | String | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

{.compact}
Name | Value | Remarks
--- | --- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Object `{ id: [new contact list id]}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/post"}} \
{{include "curl/header-ct-json"}} \
--data-raw '{
    "name": "My Contact List"
}'
```

+++
