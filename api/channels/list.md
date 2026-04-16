Get the list of channels for the given provider.

## Method

[!badge GET]

## Path

`/channels`

## Query string parameter

{.compact}
Name | Value | Required?
--- | --- | ---
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | Yes

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

Array of object

{.compact}
Name | Value | Remarks
--- | --- | ---
id | Channel ID | -
channel_key | Channel key | This is the same as the id field.
name | Channel name | -

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/channels?provider=twlo' \
--header 'apikey: your_api_key' \
```

+++
