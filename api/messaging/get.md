Get all the messages.

## Method

[!badge GET]

## Path

`/messages`

## Query string parameter

{.compact}
Name | Value | Required? | Remarks
--- | --- | --- | ---
start_date | Date in YYYY-MM-DD format (e.g., `2024-01-01`) | No |  Defaults to 90 days before today. <br />Results include given date.
end_date | Date in YYYY-MM-DD format (e.g., `2024-01-31`) | No |  Defaults to today. <br />Results include given date.

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
data | Array of message objects | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/messages' \
--header 'apikey: your_api_key' \
```

+++
