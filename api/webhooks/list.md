Get the list of subscriptions.

## Method

[!badge GET]

## Path

`/webhook-subscriptions`

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
data | Array of subscription object. See below | Only present when status is `success`

#### Subscription object

{.compact}
Name | Value
--- | ---
id | Subscription ID
channel_key | Channel key associated to this webhook
created_at | Milliseconds timestamp of when the subscription was created
platform | Platform hosting the endpoint (value provided by the caller when creating the subscription)
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp)
status | Status of the webhook subscription. `active` or `paused`
subscriber_reference_id | Unique identifier for the subscription (value provided by the caller when creating the subscription)
trigger_direction | Value is always `incoming`
webhook_url | Webhook endpoint URL

## Code sample

+++ cURL

```shell
curl --location --request GET 'https://api.sociocs.com/webhook-subscriptions' \
--header 'apikey: your_api_key' \
```

+++
