Get the list of scheduled messages. The list will have max 100 records, ordered by the scheduled date in descending order. Pagination is not available at the moment.

## Method

[!badge GET]

## Path

`/messages/scheduled`

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
data | Array of object with the scheduled message fields. | Only present when status is `success`.

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/messages/scheduled' \
--header 'apikey: your_api_key' \
```

+++
