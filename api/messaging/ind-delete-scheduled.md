Delete a scheduled message.

!!!warning
You cannot delete a scheduled message which is already being sent or is already sent.
!!!

## Method

[!badge DELETE]

## Path

`/messages/scheduled/[message_id]`

## Path parameter

{.compact}
Name | Value | Required?
--- | --- | ---
message_id | ID of the scheduled message. | Yes

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
curl --location --request DELETE 'https://api.sociocs.com/messages/scheduled/Xyz12345' \
--header 'apikey: your_api_key'
```

+++
