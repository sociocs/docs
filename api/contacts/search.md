Search contacts by partial/full name or phone number.

## Method

[!badge GET]

## Path

`/contacts/search`

## Query string parameter

{.compact}
Name | Value | Required?
--- | --- | ---
query | Search term (either partial/full name or phone number). Search is case insensitive. Minimum 2 characters are required. | Yes
limit | Number of records to return. Max allowed value is 20. | No. Defaults to 20.
offset | Number of records to skip (for pagination). | No. Defaults to 0.

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
data | Array of contact objects. Result is sorted by relevance of the match. | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/contacts/search?query=Emilia&limit=10&offset=0' \
--header 'apikey: your_api_key' \
```

+++
