Update a contact.

## Method

[!badge PUT]

## Path

`/contacts/[phone_number]`

## Path parameter

{.compact}
Name | Value | Required?
--- | --- | ---
phone_number | Phone number starting with the country code with or without leading plus. e.g. `+16175551212` or `16175551212` | Yes

## Body parameters

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
phone_number_cc | Phone number country dial code (e.g. "1") | String | No
name | Contact person name | String | No
extra_fields | Key value pair object with additional custom fields (e.g. `{ "email_address": "john@example.com", "id": 987123 }`) | Object | No

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
curl --location --request PUT 'https://api.sociocs.com/contacts/16175551212' \
--header 'apikey: your_api_key' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "John Davidson",
    "phone_number_cc": "1",
    "extra_fields": {
        "email_address": john@example.com
    }
}'
```

+++
