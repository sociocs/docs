Add one or more contacts to a contact list using phone numbers.

## Method

[!badge POST]

## Path

`/contacts/add-to-list`

## Body parameters

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
dest_list_id | Destination contact list ID | Integer | Yes
phone_numbers | Array of the phone numbers of the contacts to be added to the list (e.g. `["16317471111"]`) | Array of string | Yes

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
curl --location --request POST 'https://api.sociocs.com/contact/add-to-list' \
--header 'apikey: your_api_key'
--header 'Content-Type: application/json' \
--data-raw '{
    "dest_list_id": 10001,
    "phone_numbers": ["16317471111", "16317472222"]
}'
```

+++
