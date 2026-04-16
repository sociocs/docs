---
title: Delete bulk messaging job
order: -800
data:
    path: "/messages/bulk/[job_id]"
    path_for_sample: "/messages/bulk/Xyz12345"
---

Delete a bulk messaging job.

!!!warning
You cannot delete a bulk messaging job which is already executing or has already executed.
!!!

## Method

[!badge DELETE]

## Path

`{{path}}`

## Path parameter

{.compact}
Name | Value | Required?
--- | --- | ---
job_id | ID of the scheduled bulk messaging job. | Yes

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
{{include "curl/delete"}}
```

+++
