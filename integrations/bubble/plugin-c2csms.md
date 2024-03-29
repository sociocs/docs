---
label: Click to Chat by Text
title: 'Bubble plugin :: Sociocs - Click to Chat by Text'
order: -100
---

## Introduction

This plugin adds a chat bubble on your website that draw user's attention, and gives them an easy way to reach out to you. It converts an inquiry into SMS / text messaging based conversation, so that your user doesn't have to wait on the website for a response.

When your web app user initiates the inquiry, it shows up in your Sociocs Inbox, from where you can reply to the user, and continue the conversation.

[!button variant="info" target="blank" text="Demo"](https://sociocs-plugins.bubbleapps.io/version-test/live_chat_by_text_demo) [!button variant="info" target="blank" text="Plugin page on Bubble"](https://bubble.io/plugin/sociocs---live-chat-by-text-1649745550565x177374092711165950)

## Plugin Installation

1. In the Bubble dashboard, go to "*Plugins*".

1. Click on "*+ Add Plugins*".

1. Search for 'Sociocs - "*Live Chat*" by Text'.

1. Click on "*Install*".

## Plugin Configuration

### Twilio

{{include "twilio-signup-steps"}}

### Sociocs

{{include "c2csms-channel-initial-steps"}}

1. You should see the plugin code, find these values in the code: "*data-channel*", "*data-primary-color*", and "*data-prompt-text*". These fields are referred without "*data-*" prefix in the below step (e.g. "*data-channel*" is referred as "*channel*" etc.)
    ![image](https://user-images.githubusercontent.com/12301512/179742406-bbf28620-0024-44da-b532-4155fca6829f.png)

### Bubble Editor

1. Go to the "*Sociocs - Click to Chat by WhatsApp*" plugin in the Bubble Editor.

1. Add "*channel*", "*primary-color*", and "*prompt-text*" configuration parameters.

1. Bubble also shows fields for adding dev keys (i.e. "*channel - dev.*", "*primary-color - dev.*", and "*prompt-text - dev.*"). You can leave them blank.

That's it! Refresh your Bubble web app page, and you should see a chat bubble on bottom right.
