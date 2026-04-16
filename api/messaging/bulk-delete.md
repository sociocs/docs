Delete a bulk messaging job.

!!!warning
You cannot delete a bulk messaging job which is already executing or has already executed.
!!!

## Method

[!badge DELETE]

## Path

`/messages/bulk/[job_id]`

## Path parameter

{.compact}
Name | Value | Required?
--- | --- | ---
job_id | ID of the scheduled bulk messaging job. | Yes

## Response

### HTTP status codes

{.compact}
Code | Remarks
--- | ---
200 | Request was successful.
400 | Validation error or request body was incorrectly formatted.
401 | Authentication failed. Check `apikey` header.
404 | Requested API endpoint not found.
429 | The rate limit has been reached.
500-511 | There was a problem processing the request on our server. Try again later.

### Response object

{.compact}
Name | Value | Remarks
--- | --- | ---
status | `success` or `error` | -
errors | Array of object `{ msg: [error detail] }` | Only present when status is `error`.

## Code sample

+++ cURL

```shell
curl --location --request DELETE 'https://api.sociocs.com/messages/bulk/Xyz12345' \
--header 'apikey: your_api_key'
```

+++
