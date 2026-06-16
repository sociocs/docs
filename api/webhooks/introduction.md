Webhooks are your REST APIs which get called when a subscribed event takes place in Sociocs. URL of your REST API endpoint is referred to as webhook endpoint.

## Channels supporting webhooks

- SMS (with Telnyx)
- SMS (with Twilio)
- WhatsApp (with Gupshup)
- WhatsApp (with Twilio)

## How to set it up?

In order for Sociocs to start calling your webhook endpoint, you need to subscribe it for a specific channel and the events you are interested in. You can add multiple webhooks for the same channel, or same webhook for multiple channels, depending upon your needs.

## Webhook endpoint invocation details

Sociocs calls the webhook endpoints with an assumption that it's a REST API accepting JSON body parameters.

### Method used

[!badge POST]

### New incoming message body parameters

{.compact}
Name | Value | Data type
--- | --- | ---
message_id | Message ID | String
event | `message` | String
provider | `twlo` (for Twilio SMS), <br />`twlowa` (for Twilio WhatsApp), <br />`gswa` (for Gupshup WhatsApp) | String
channel_key | Channel key associated to the webhook | String
direction | `incoming` | String
from | Sending phone number | String
to | Receiving phone number | String
name | Sender's name (if available) | String
text | Message text | String
file_urls | Publicly accessible links to files in the message | Array of String
image_urls | Publicly accessible links to images in the message | Array of String
video_urls | Publicly accessible links to videos in the message | Array of String
contact | Object with contact details (if a contact with the 'from' phone number is found) | Object
timestamp | Timestamp as milliseconds since epoch. | Integer

#### Example 

```
{
  "message_id": "MM2aa0db1b276eaeaa5d730d5aa34167f2",
  "event": "message",
  "provider": "twlo",
  "channel_key": "twlo_16311113333",
  "direction": "incoming",
  "from": "16311112222",
  "to": "16311113333",
  "text": "Hello World!",
  "video_urls": [],
  "image_urls": [],
  "file_urls": [],
  "contact": {
    "id": 123,
    "name": "Emily Johnson",
    "phone_number": "16311112222",
    "phone_number_cc": "",
    "extra_fields": "{\"city\": \"Ahmedabad\", \"country\": \"India\"}",
    "created_at": "2025-07-11T11:29:46.000Z",
    "updated_at": "2025-08-04T12:29:21.000Z",
    "is_blocked": 0
  }
  "timestamp": 1754455905897,
}
```

### Outgoing message status updates body parameters

Name | Value | Data type
--- | --- | ---
message_id | Message ID | String
event | `status_update` | String
event_data | Object `{ status: "sent"|"delivered"|"read"|"failed", event: "status_update", error: [error details when failed]},  provider_err_obj: [error object from provider when failed] }` <br/><br/>Note: Only WhatsApp channels support the `read` status. | Object

#### Examples

#### Successfully sent message

```
{
  "message_id": "MM2aa0db1b276eaeaa5d730d5aa34167f2",
  "event": "status_update",
  "event_data": {
    "status": "sent"
  }
}
```

#### Successfully delivered message

```
{
  "message_id": "MM2aa0db1b276eaeaa5d730d5aa34167f2",
  "event": "status_update",
  "event_data": {
    "status": "delivered"
  }
}
```

#### Failed message

```
{
  "message_id": "MM2aa0db1b276eaeaa5d730d5aa34167f2",
  "event": "status_update",
  "event_data": {
    "status": "failed",
    "error": {
      "code": 21614,
      "message": "You have attempted to send a message to a number that is either a landline number or is an invalid number. (code: 21614)"
    },
    "provider_err_obj": {
      "status": 400,
      "code": 21614,
      "moreInfo": "https://www.twilio.com/docs/errors/21614",
      "error": true
    }
  }
}
```

### Validating webhook deliveries

When [subscribing your webhook endpoint](/api/webhooks/add/), you can optionally pass a `secret` field. Sociocs will use your secret token to create a hash signature that's sent to you with each payload. The hash signature will appear in each delivery as the value of the `X-Sociocs-Signature` header.

In your code that handles webhook deliveries, you should calculate a hash using your secret token. Then, compare the hash that Sociocs sent with the expected hash that you calculated, and ensure that they match. This allows you to verify that incoming requests are genuinely from Sociocs and have not been tampered with.

!!!
Adding secret and verifying the signature is optional but highly recommended.
!!!

There are a few important things to keep in mind when validating webhook payloads:

- Sociocs uses an HMAC sha256 hex digest to compute the hash.
- The hash signature is generated using your webhook's secret token and the payload contents.
- If your language and server implementation specifies a character encoding, ensure that you handle the payload as UTF-8. Webhook payloads can contain unicode characters.

#### Examples

##### JavaScript / Node.js

```javascript
const crypto = require("crypto");

/**
 * Validates an incoming webhook signature.
 * @param {string} rawBody - The exact raw string body received in the HTTP request.
 * @param {string} signature - The signature sent in the header (i.e., X-Sociocs-Signature).
 * @param {string} secret - The shared webhook secret.
 * @returns {boolean} True if the signature is valid, false otherwise.
 */
function verifyWebhookSignature(rawBody, signature, secret) {
  if (!rawBody || !signature || !secret) {
    return false;
  }

  try {
    // Generate the expected signature using the raw string body
    const expectedSignature = crypto
      .createHmac("sha256", secret)
      .update(rawBody, "utf8")
      .digest("hex");

    // Convert both strings to buffers for a timing-safe comparison
    const expectedBuffer = Buffer.from(expectedSignature, "hex");
    const actualBuffer = Buffer.from(signature, "hex");

    // Protects against timing attacks by ensuring the comparison 
    // takes the same amount of time regardless of where a mismatch occurs
    if (expectedBuffer.length !== actualBuffer.length) {
      return false;
    }
    
    return crypto.timingSafeEqual(expectedBuffer, actualBuffer);
  } catch (error) {
    return false;
  }
}
```

##### Python

```python
import hmac
import hashlib

def verify_webhook_signature(raw_body: str, signature: str, secret: str) -> bool:
    """
    Validates an incoming webhook signature.
    
    :param raw_body: The exact raw string body received in the HTTP request.
    :param signature: The signature sent in the header (i.e., X-Sociocs-Signature).
    :param secret: The shared webhook secret.
    :return: True if the signature is valid, false otherwise.
    """
    if not raw_body or not signature or not secret:
        return False

    try:
        # Both the secret and payload must be encoded to bytes before hashing
        secret_bytes = secret.encode("utf-8")
        body_bytes = raw_body.encode("utf-8")

        # Generate the expected signature
        expected_signature = hmac.new(
            secret_bytes, 
            body_bytes, 
            hashlib.sha256
        ).hexdigest()

        # Prevent timing attacks by using a constant-time comparison function
        return hmac.compare_digest(expected_signature, signature)
    except Exception:
        return False
```

#### Testing your webhook payload validation

You can use the following secret and raw body values to verify that your implementation is correct:

- Secret: `My Shared Secret`
- Raw body: `Hello, World!`

If your implementation is correct, the signatures that you generate for the comparison should be: `a52954ef969a496aeed237f48b03c6df7ea43cd0f6e595d06dfe7a8b14b5d891`.
