## Introduction

Sociocs Web Chat plugin adds a chat bubble on your website that draw user's attention, and gives them an easy way to reach out to you. It converts an inquiry into SMS / text messaging based conversation, so that your user doesn't have to wait on the website for a response.

When your web app user initiates the inquiry, it shows up in your Sociocs Inbox, from where you can reply to the user, and continue the conversation.

[!button variant="info" target="blank" text="Demo"](https://wordpress-demo.sociocs.com/)

![image](https://user-images.githubusercontent.com/12301512/203017406-4b197d3f-6094-496d-a76c-f84a0865c783.png)

## Setup

### Twilio

* You can skip this step if you already have an account with Twilio.
* If you don't have an account with Twilio, you can sign up for a <a href="https://www.twilio.com/try-twilio" target="_blank">free trial account</a>. (Once you sign up for a trial, you should consider upgrading right away to avoid outbound SMS restrictions.

### Sociocs

1. Sign up or log in on <a href="https://app.sociocs.com" target="_blank">app.sociocs.com</a>.

1. Select "*SMS (with Twilio)*" in the "*Connect a new channel*" page. If you are an existing user, after logging in, click on "*Channels*" menu on the top, click on "*+*" button to go to the "*Connect a new channel*" page.

1. Connect your Twilio phone by following the instructions.

1. Go to "*Connect a new channel*" page again (click on "*Channels*" on the top menu, and click on "*+*" button), and select "*Click to Chat by Text/SMS*".

1. Enter information for your Web Chat plugin and customize the chat prompt UI (if you want), and click "*Next*".

1. You should see the plugin code. You will be using this code in your WordPress site in the instruction below.

### WP Admin Dashboard

Adding this plugin on a WordPress site simply requires inserting plugin script and div tag in your website. There are multiple ways to introduce custom JavaScript and HTML in a WordPress site. Here are the steps using a well known plugin `Insert Headers and Footers`.

#### Insert plugin script and div tag

1. Install "*Insert Headers and Footers*" plugin "*By WPBeginner*" through the "*Plugins*" menu in your admin dashboard.

2. Activate the plugin.

3. Go to the "Settings > Insert Headers and Footers" menu.

4. Copy and paste plugin code mentioned above in the "Scripts in Footer" textbox.

5. Click "Save".

That's it! Refresh your WordPress website page, and you should see a chat bubble on bottom right.
