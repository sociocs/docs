---
title: "Bulk messaging"
icon: megaphone
order: -200
---

{{include "alert-paid-account-required"}}

## Introduction

Bulk messaging feature allows you to send personalized text/SMS/MMS or WhatsApp messages to multiple recipients simultaneously, ideal for marketing campaigns, updates, or notifications.

## Channels supporting bulk messaging

- SMS (with Twilio)
- SMS (with Telnyx)
- SMS with TWilio Messaging Service
- WhatsApp (with Gupshup) (*Future plan, not available at the moment.*)
- WhatsApp (with Twilio) (*Future plan, not available at the moment.*)

## Data sources supported

- CSV files
- Excel files
- Contact lists
- Segments

## Message content types supported

- Text
- Image
- Video
- File (only supported for WhatsApp)

## Compliance and Best Practices
- Obtain explicit consent from recipients before sending messages.
- Include an opt-out text in the message (e.g., "Reply STOP to unsubscribe").
- Comply with local regulations, such as TCPA (US) or GDPR (EU).
- Send messages during reasonable hours to respect recipients’ time.

## Sending bulk messages

- Go to "*Bulk messaging*" from the left sidebar menu.

- Select a channel from the list of eligible channels in your account.

---

**Provide information for the below fields.**

### Message content

+++ For text/SMS/MMS

#### Message text

Enter message content in this field. You can personalize the messages by adding [dynamic fields](/miscellaneous/dynamic-fields.md) from your data source.

![Message example](https://github.com/sociocs/docs/assets/12301512/6f3a05fb-c385-44df-8ec9-9c723cda9ac4)

{{include "alert-whatsapp-apprvd-tmplt-reqd"}}

#### Save as template

You can use this check box to save the entered messages text as a template. It can update an existing template with new text or create a new template.

!!!
One benefit of using templates for the bulk messaging is that we link all the campaign information you enter to the template. So when you select the same template next time, it will prefill the information you used last time. :bulb:
!!!

#### Attach media file

In addition to the text, you can also send an image or video in the message.

+++ For WhatsApp

!!!
Sending bulk WhatsApp messages requires an approved template from WhatsApp. You can submit the template for approval on the website of the provider you used to create your WhatsApp account (e.g., Twilio).
!!!

#### Template type [only applicable for WhatsApp (with Gupshup) channels]

Select a template type as applicable for your situation.

- **Legacy templates**: You can use this option to send messages without any personalizations. Please ensure to enter the "*Message text*" that matches a WhatsApp approved template. You can ignore the "*Select a template*" step mentioned below.

- **Rich templates**: This the recommended option which supports message personalization with dynamic parameters.

#### Select a template

Select a WhatsApp approved template from the list on the right hand size. 

**After selecting a template, a light blue box for variable mapping appears on the page, below the data sources configuration. You should map the dynamic parameters there to enable personalization.**

+++

### Data source

+++ Upload CSV/Excel

![Upload CSV/Excel tab](https://github.com/sociocs/docs/assets/12301512/ace4720a-a57f-4a39-836b-a2aeb0489ccd)

#### File

You can upload a CSV or an Excel file with any number of columns in any order.

This gives you flexibility to directly upload a file exported from another system without a need of any data manipulation. Necessary data mapping are captured in the fields below.

##### Duplicates allowed

Check this box if you would like to send multiple messages to the same number if duplicates found in the file. When unchecked, message is sent only once per phone number.

##### The file's first record doesn't have column headers

When the file you're uploading doesn't have any column headers, you can specify the column headers in text box that shows up once you check this box.

!!! info
This is very helpful when you're exporting the file from another system which doesn't export with column headers. You can specify the column headers here instead of adding to the exported file each time.
!!!

Column headers must be provided separated by comma in the exact order as the file records. For example, if you upload a file like below, you could enter values in the text box like this - `id,full_name,first_name,last_name,phone_number,email_address,date_of_birth,address`.

![File example without column headers](https://github.com/sociocs/docs/assets/12301512/6ceaa641-9048-40ed-9ca6-68477a6d35be)

#### To country code

If the phone numbers in the file do not start with the country dial code (e.g., `+1` or `1`), you should select the appropriate country dial code in this dropdown list.

!!! info
If the value shown by default is correct, there is no need to change it.
!!!

##### Phone numbers in the uploaded file start with the country code

This option must be checked when the phone numbers in the file you're uploading already start with the country dial code (e.g., +1 or 1).

!!!warning
If the phone numbers in the file already have country dial code, and you don't check this box, the messages may not get delivered because we will apply country code from the "*To country code*" dropdown list.

On the flip side, if the phone numbers in the file do not have country code, and you check this box, the messages may not get delivered at all because they cannot be routed to correct destination number, or they may get delivered incorrectly to recipients in the same country as the source phone number.
!!!

#### Recipient name column header (optional)

Specify the column header of the recipient name column in the uploaded file.

For example, if you upload a file like below, the value entered should be `Full_Name`.
![File example](https://github.com/sociocs/docs/assets/12301512/4935ce0f-a842-46c9-b79d-bc92be929aa3)

If the file doesn't have column headers, and you checked "*The file's first record doesn't have column headers*", provide the value you entered as the column header for the recipient name column.

#### Phone number column header

Specify the column header of the phone number column in the uploaded file.

For example, if you upload a file like below, the value entered should be `Phone_Number`.
![File example](https://github.com/sociocs/docs/assets/12301512/fb7a8197-a3d3-42bc-9336-7fc42090072b)

If the file doesn't have column headers, and you checked "*The file's first record doesn't have column headers*", provide the value you entered as the column header for the phone number column.

+++ Use Contact List or Segment

![Use Contact List tab](https://github.com/sociocs/docs/assets/12301512/246667ba-a663-4dee-a87c-13ef00183f00)

#### Select a list

Select one of the contact lists or segments you have already created. See [Contacts](/contacts/introduction.md) for more information.

+++

### Auto translation

Check this box if you would like to have the message text auto translated to recipient's language. For this to work, the source data also needs to have `language` value from the [list of supported languages](/miscellaneous/translation-languages/).

#### When using a CSV/Excel file

The file needs to have a column with header `language` (*must be in all lowercase*). The value should be *"Language code"* from [this page](/miscellaneous/translation-languages/).

For example, to auto translate message text to a specific recipient to Spanish, you upload a file like below.

![File example](https://github.com/sociocs/docs/assets/12301512/9e8b6b81-d450-4a48-acb2-01a2e016ff0e)

#### When using a contact list

The contact requiring translation should have an `Extra field` with key `language` (*must be in all lowercase*). The value should be "*Language code*" from [this page](/miscellaneous/translation-languages/).

For example, to auto translate message text to a specific contact to Spanish, you add language extra field like below.

![Contact example](https://github.com/sociocs/docs/assets/12301512/da14ca29-b062-4711-9723-bd65c0f7e7fd)

### Send on

You can send the messages immediately or schedule it for a later date and time.

!!! info
You can schedule the campaign up to 30 days in advance.
!!!

### Drip campaign

You can control and limit number of messages sent at specific intervals with this feature.

- Check "*Enable drip messaging*" to activate this option and specify how many messages you would like to send at what interval. 
- By default, message delivery is restricted to between 9 AM and 7 PM. You can customize this time window or disable the restriction entirely.

### Submit

Once you click "*Next*", you will be shown a confirmation popup with a sample preview of the message. You will also be able to send a test message to yourself before confirming the campaign.

In case you need to make any changes, click "*Cancel*" in the confirmation popup to close it.
