---
title: Get messages
order: -850
data:
    path: "/messages"
    path_for_sample: "/messages"
---

Get all the messages.

## Method

[!badge GET]

## Path

`{{path}}`

## Query string parameter

Name | Value | Required? | Remarks {class="compact"}
--- | ---
start_date | Date in YYYY-MM-DD format (e.g., `2024-01-01`) | No |  Defaults to 90 days before today. <br />Results include given date.
end_date | Date in YYYY-MM-DD format (e.g., `2024-01-31`) | No |  Defaults to today. <br />Results include given date.

## Response

### HTTP status codes

{{include "http-status-codes"}}

### Response object

Name | Value | Remarks {class="compact"}
--- | ---
{{include "resp-obj-row/status"}}
{{include "resp-obj-row/errors"}}
data | Array of message objects | Only present when status is `success`

## Code sample

+++ cURL

```shell
{{include "curl/get"}}
```

+++
