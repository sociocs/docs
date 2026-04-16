Get a channel.

## Method

[!badge GET]

## Path

`/channels/[channel_key]`

## Path parameter

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
channel_key | Channel key value from *Profile & settings -> API* | String | Yes

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
data | Channel object. See below. | Only present when status is `success`

#### Channel object

{.compact}
Name | Value
--- | ---
name | Channel name
country_code | Country dial code of the phone number connected in the channel
phone_number | Phone number connected in the channel
provider | Messaging provider for the channel <br />`twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp)

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/channels/your_channel_key' \
--header 'apikey: your_api_key' \
```

+++
