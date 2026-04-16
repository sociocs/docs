Delete an existing contact list.

## Method

[!badge DELETE]

## Path

`/lists/[id]`

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
data | Object `{ id: [deleted contact list's id]}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request DELETE 'https://api.sociocs.com/lists/10001' \
--header 'apikey: your_api_key'
```

+++
