---
title: Get channels
order: -100
data:
    path: "/channels"
    path_for_sample: "/channels?provider=twlo"
---

Get the list of channels for the given provider.

## Method

[!badge GET]

## Path

`{{path}}`

## Query string parameter

{.compact}
Name | Value | Required?
--- | --- | ---
provider | {{include "providers"}} | Yes

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Array of object

{.compact}
Name | Value | Remarks
--- | --- | ---
id | Channel ID | -
channel_key | Channel key | This is the same as the id field.
name | Channel name | -

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
