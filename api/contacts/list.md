---
title: Get contacts
order: -250
data:
    path: "/contacts"
    path_for_sample: "/contacts?list_id=1000001&limit=100&offset=200"
---

Get contacts from 'All Contacts' or belonging to a list.

## Method

[!badge GET]

## Path

`{{path}}`

## Query string parameter

Name | Value | Required? {class="compact"}
--- | ---
list_id | `0` - to get all Contacts or <br/> List ID - to get contacts from a specific list (Use [/lists](/api/contact-lists/get/) endpoint to get all the contact lists) | No
limit | Number of records to return. Max allowed value is 1000. | No. Defaults to 1000.
offset | Number of records to skip (for pagination). | No. Defaults to 0.

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Array of contact objects. Result is sorted by the contact ID in ascending order. | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
