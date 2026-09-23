---
layout: default
title: Privacy policy
---
{% comment %}
Every statement below carries a claim id (P1…P25). The evidence for each id is
in docs/adr/2026-09-23_ADR-047_PERSONAL_DATA_DISCLOSURES.md in the NexCall
repository. Change a sentence only together with its row there.
{% endcomment %}

# Privacy policy

This policy explains what personal data NexCall handles, why, where it is kept,
for how long, and what you can do about it. It is written to meet India's
Digital Personal Data Protection Act, 2023 (DPDP Act) and the Information
Technology (Intermediary Guidelines and Digital Media Ethics Code) Rules, 2021.

**Who is responsible.** NexCall is run by {{ site.grievance_name }}, who is the
data fiduciary for the data described here. Contact: <{{ site.grievance_email }}>.

## The short version

- Your messages, photos, videos, voice notes, files and calls are **end-to-end
  encrypted**. We cannot read or listen to them. {% comment %}P6 P10{% endcomment %}
- We do not collect your phone number, phone contacts or location. We keep
  your email only in a scrambled form. {% comment %}P3 P26{% endcomment %}
- We have no ads, no analytics and no tracking. {% comment %}P21{% endcomment %}
- We can see some **metadata**: who you message or call, and when. {% comment %}P11{% endcomment %}
- You can delete your account at any time, in the app or on
  [this website](delete-account). {% comment %}P22{% endcomment %}

## 1. What we collect and why

| Data | Why | How long we keep it |
|---|---|---|
| **Your account:** username, display name, and your password stored as a one-way hash (we never see the password itself), and when you signed up. {% comment %}P1{% endcomment %} | To create your account and let you sign in. | Until you delete your account. |
| **Your email:** stored only as a scrambled code (a keyed hash) plus a hint like s•••••@gmail.com, never as the address itself. {% comment %}P26{% endcomment %} | To let you sign in with your email and reset a forgotten password with a code we send to it. When you type your email to get a code, we use it once to send the mail and do not keep it. | Until you delete your account. |
| **Google sign-in (optional):** only Google's account identifier for you and a display name. Not your email or photo. {% comment %}P2{% endcomment %} | To let you sign in with Google, and to reset a forgotten password. | Until you delete your account. |
| **Your NexCall contacts:** who you have added, who asked to add you, who you blocked. {% comment %}P4{% endcomment %} | So you can message and call your contacts, and so blocking works. | Until you or they remove the contact, or an account is deleted. |
| **Presence:** whether you are online, and when you were last seen. {% comment %}P5{% endcomment %} | To show your contacts whether you are available. You can turn this off in Me › Privacy. | Updated as you use the app; removed when you delete your account. |
| **Messages waiting for delivery:** encrypted, unreadable to us. {% comment %}P6 P7{% endcomment %} | To deliver messages to a phone that is offline. | Deleted when delivered, or after 14 days. |
| **Photos, videos and files you send:** encrypted on your phone before upload, unreadable to us. {% comment %}P6 P8{% endcomment %} | To deliver attachments. | Deleted after 30 days. |
| **Message history backup:** encrypted on your phone, unreadable to us. {% comment %}P9{% endcomment %} | So you can restore your chats on a new phone. | Until you delete your account. |
| **Push token:** an identifier from Google's Firebase Cloud Messaging for your phone. {% comment %}P13{% endcomment %} | To wake your phone for an incoming call or message. The notification we send carries no names and no message content. | Replaced when it changes; removed when you delete your account. |
| **Sign-in sessions.** {% comment %}P18{% endcomment %} | To keep you signed in. | 1 hour, or up to 7 days (30 days with "Remember me"). |
| **Call-quality reports:** when a call fails, the app sends the network type, whether a VPN was on, your mobile carrier's code, technical connection details, why the call ended, and the app version. No user id, no IP address, no one else's details; the time is rounded to the hour. {% comment %}P14{% endcomment %} | To find and fix call failures. This is **on by default**; turn it off in Me › Privacy › "Send anonymous call-quality reports". | 90 days. |
| **Abuse reports** you file: who you reported, the reason, anything you wrote, and — **only if you report a specific message — the text of that one message, sent from your phone**, with who sent it and when. The app tells you this before you send. {% comment %}P15{% endcomment %} | To act on abuse and meet our legal duties. | Until the report is resolved, then 180 days. If an account involved is deleted, the report is kept without the link to that account. |
| **Server logs:** the requested address (without search terms), the result, a shortened IP address (the last part removed), and account ids on some events such as sign-in and calls. {% comment %}P12 P17{% endcomment %} | To keep the service running and secure, and to investigate misuse. | Logs are overwritten as new ones are written, at about 100 MB per log; how many days that covers depends on traffic. |

**What we cannot see.** Messages, attachments, backups and calls are end-to-end
encrypted between the phones taking part. Calls go directly between phones, or
through our relay server, which passes on encrypted traffic it cannot decrypt.
We never record calls. {% comment %}P6 P9 P10{% endcomment %}

**What we can see (metadata).** To deliver messages and connect calls, our
server knows which accounts message or call each other, when, and how large
messages are. {% comment %}P11{% endcomment %}

## 2. On your phone

The app keeps your messages (in an encrypted store), your call history, a copy
of your contact list and your settings on your phone. They are not included in
Android backups. {% comment %}P25{% endcomment %}

Your **recovery key**, which opens your message backup, is kept on your phone
and in Google Block Store, which backs it up to your Google account. Google
encrypts that backup end to end when your phone has a screen lock. NexCall's
server never receives this key. {% comment %}P20{% endcomment %}

## 3. Who else handles your data

We do not sell or share your data. These service providers process it for us:
{% comment %}P19 P21{% endcomment %}

| Provider | What for | What they receive |
|---|---|---|
| Oracle Cloud (India, Hyderabad region) | Hosting the server; storing encrypted database backups (kept 7 days) | Everything the server stores, as described above. Backups are encrypted with a key Oracle does not have. |
| Google (Firebase Cloud Messaging) | Waking your phone for calls and messages | Your push token and a wake-up signal without names or content |
| Google (Sign-In, Block Store) | Optional Google sign-in; backing up your recovery key to your Google account | Your sign-in request; your recovery key, stored in your own Google account |
| Google (Gmail) | Sending sign-up and password-reset codes, and "your password was changed" notices | The email address you typed and the message |
| Let's Encrypt | The server's security certificate | Our domain name only |

The app contains no advertising, analytics or crash-reporting software. {% comment %}P21{% endcomment %}

Our server and its backups are in India. Google processes the push token and your Google sign-in on its own servers, which may be outside India. {% comment %}P19 P21{% endcomment %}

## 4. Your rights

Under the DPDP Act you can:

- **Know what we hold about you.** Your profile is shown in the app (Me). For a
  full summary, write to the grievance officer. {% comment %}P24{% endcomment %}
- **Correct it.** Change your display name, username, email and password in
  the app (Me › Profile, Me › Security). {% comment %}P23 P26{% endcomment %}
- **Erase it.** Delete your account in the app (Me › Security › Delete
  account) or on [the deletion page](delete-account). Server data is removed at
  once; encrypted backups age out within 8 days. Messages you already sent stay
  on the other person's phone. {% comment %}P22{% endcomment %}
- **Withdraw consent** by deleting your account, turning off call-quality
  reports, or turning off presence sharing.
- **Nominate** someone to exercise these rights if you die or cannot act, by
  writing to the grievance officer.
- **Complain** to the grievance officer (below), and, if you are not satisfied,
  to the Data Protection Board of India.

## 5. Grievance officer

{{ site.grievance_name }} — <{{ site.grievance_email }}>

- We acknowledge a complaint within **24 hours** and resolve it within **15
  days**.
- A request to remove content that is unlawful under Rule 3(1)(b) of the IT
  Rules is resolved within **72 hours**; content showing a person in a sexual
  act or nudity without consent is removed within **24 hours**.
- Privacy complaints under the DPDP Act are answered within **90 days** at the
  latest.
- If you disagree with a decision under the IT Rules, you can appeal to the
  Grievance Appellate Committee within 30 days.

## 6. Children

NexCall is not meant for anyone under 18. We do not knowingly create accounts
for children.

## 7. Security

Connections to our server use TLS. Message content is end-to-end encrypted.
Backups are encrypted before they leave the server. Report a security problem
to the grievance officer.

## 8. Changes

When this text changes, the version and date at the bottom of the page change
with it.
