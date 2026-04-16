Subscribe a webhook endpoint to receive incoming messages received on your channel. You can also subscribe to status updates for outgoing messages.

## Method

[!badge POST]

## Path

`/webhook-subscriptions`

## Body parameters

{.compact}
Name | Value | Data type | Required?
--- | --- | --- | ---
platform | A value that identifies the platform hosting the endpoint (e.g., "salesforce") | String | Yes
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | String | Yes
channel_key | Channel key value from *Profile & settings -> API* | String | Yes
subscriber_reference_id | Unique identifier for the subscription. If you call the API again with the same value for this field, it will update the existing subscription. | String | Yes
webhook_url | Webhook endpoint URL | String | URL

!!! info
If you call this API with the same `subscriber_reference_id`, it will update the existing subscription.
!!!

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
data | Object `{ id: [subscription id]}` | Only present when status is `success`

## Code sample

+++ cURL

```shell
curl --location --request POST 'https://api.sociocs.com/webhook-subscriptions' \
--header 'apikey: your_api_key' \
--header 'Content-Type: application/json' \
--data-raw '{
    "platform": "salesforce",
    "provider": "twlo",
    "channel_key": "[your channel key]",
    "subscriber_reference_id": "ABC1234567890XYZ",
    "webhook_url": "https://example.com/incoming"  
}'
```

+++
