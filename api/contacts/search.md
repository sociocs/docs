---
title: Search contacts
order: -275
data:
    path: "/contacts/search"
    path_for_sample: "/contacts/search?query=Emilia&limit=10&offset=0"
---

Search contacts by partial/full name or phone number.

## Method

[!badge GET]

## Path

`{{path}}`

## Query string parameter

Name | Value | Required? {class="compact"}
--- | ---
query | Search term (either partial/full name or phone number). Search is case insensitive. Minimum 2 characters are required. | Yes
limit | Number of records to return. Max allowed value is 20. | No. Defaults to 20.
offset | Number of records to skip (for pagination). | No. Defaults to 0.

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Array of contact objects. Result is sorted by relevance of the match. | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
