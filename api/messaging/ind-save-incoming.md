Save a message in the inbox. You can use it to save a message received on an external platform or create a mock message with information you may need during the conversation.

## Method

[!badge POST]

## Path

`/incoming`

## Body parameters

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
provider | `twlo` (for Twilio SMS). No other providers supported yet. | String | Yes
channel_key | Channel key value from *Profile & settings -> API*  | String| Yes
from | Phone number starting with the country code with or without leading plus. e.g. `+16175551212` or `16175551212` | String | Yes
name | Sender name | String | No
text | Message text | String | Yes
media_url | Publicly accessible image, video or file URL | String | No
media_type | MIME type of the media (e.g., `image/png`, `video/mp4`, `application/pdf`, etc). [!button variant="info" size="xs" target="blank" text="List of common MIME types"](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types) | String | Only when `media_url` is present

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
curl --location --request POST 'https://api.sociocs.com/incoming' \
--header 'apikey: your_api_key' \
--header 'Content-Type: application/json' \
--data-raw '{
    "provider": "[provider]",
    "channel_key": "[your channel key]",
    "from": "[phone number]",
    "name": "[sender name]",
    "text": "[message]"
}'
```

+++
