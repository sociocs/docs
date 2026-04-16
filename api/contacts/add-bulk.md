Add new contacts in bulk. When a given phone number already exists, it updates existing contact. If existing contact gets updated, all information gets overwritten, including all extra fields.

## Method

[!badge POST]

## Path

`/contacts/bulk`

## Body parameters

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
list_id | `0` - to add to "All Contacts" or <br/> List ID - to add to a contact list (Use [/lists](/api/contact-lists/get/) endpoint to get all the contact lists) | Integer | No (defaults to 0)
phone_number_cc | Phone number country dial code (e.g. "1") | String | No
records | See below | Array | Yes

### records

The 'records' field is supposed to be an array of **up to 10,000** contacts. Each item in the array should be as below.

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
phone_number | Phone number starting with the country code with or without leading plus. e.g. `+16175551212` or `16175551212` | String | Yes
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
curl --location --request POST 'https://api.sociocs.com/contacts/bulk' \
--header 'apikey: your_api_key' \
--header 'Content-Type: application/json' \
--data-raw '{
    "list_id": 0,
    "phone_number_cc": "1",
    "records": [
        {
            "phone_number": "16175551212",
            "name": "John Johnson",
            "extra_fields": {
                "email_address": john@example.com
            }
        },
        {
            "phone_number": "16175551111",
            "name": "David Davidson",
            "extra_fields": {
                "email_address": david@example.com
            }
        }
    ]
}'
```

+++
