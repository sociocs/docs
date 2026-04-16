Reschedule a bulk messaging job.

!!!warning
You cannot update a bulk messaging job which is already executing or has already executed.
!!!

## Method

[!badge PUT]

## Path

`/messages/bulk/[job_id]`

## Path parameter

{.compact}
Name | Value | Required?
--- | --- | ---
job_id | ID of the scheduled job | Yes

## Body parameters

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
schedule | ISO 8601 date & time (e.g., "2006-01-02T15:04:05-04:00"). If the value is in the past, messages will be sent immediately. | String | No

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
data | Object `{ job_id: [bulk messaging job id] }` | Only present when status is `success`.

## Code sample

```shell
curl --location --request POST 'https://api.sociocs.com/messages/bulk/Xyz12345' \
--header 'apikey: your_api_key' \
--header 'Content-Type: application/json' \
--data-raw '{
    "schedule: "2023-12-25T11:00:00-04:00"
}'
```
