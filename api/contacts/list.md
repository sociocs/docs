Get contacts from 'All Contacts' or belonging to a list.

## Method

[!badge GET]

## Path

`/contacts`

## Query string parameter

{.compact}
Name | Value | Required?
--- | --- | ---
list_id | `0` - to get all Contacts or <br/> List ID - to get contacts from a specific list (Use [/lists](/api/contact-lists/get/) endpoint to get all the contact lists) | No
limit | Number of records to return. Max allowed value is 1000. | No. Defaults to 1000.
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
data | Array of contact objects. Result is sorted by the contact ID in ascending order. | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/contacts?list_id=1000001&limit=100&offset=200' \
--header 'apikey: your_api_key' \
```

+++
