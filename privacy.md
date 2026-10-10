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
  encrypted**: our server is not given the keys. To be sure nobody, including
  us, is in between you and a contact, compare the safety number with that
  contact. {% comment %}P6 P10{% endcomment %}
- We do not collect your phone number, phone contacts or location. Our server
  does not keep your email address (a sign-in in progress holds it for at most
  about an hour); it stores a code made from it, with which we can check an
  address you type, and a hint like s•••••@gmail.com. The mail
  service that sends our codes receives the address (see the table of
  providers). {% comment %}P3 P26{% endcomment %}
- We have no ads, and no advertising, analytics or tracking software from
  other companies. The app sends us its own call and message quality numbers,
  which you can turn off (see the table). {% comment %}P21{% endcomment %}
- We can see some **metadata**: who you message or call, and when. {% comment %}P11{% endcomment %}
- You can delete your account at any time, in the app or on
  [this website](delete-account). {% comment %}P22{% endcomment %}

## 1. What we collect and why

| Data | Why | How long we keep it |
|---|---|---|
| **Your account:** username, display name, when you signed up, and values made from your password that a sign-in is checked against (a one-way hash, and for the newer sign-in a record made on your phone). Our server receives your password when you create your account, when you change or reset it, and when you sign in on a phone that has not yet completed the newer sign-in that proves the password without sending it (the first sign-in for an older account, or an attempt where that sign-in did not succeed, which includes a mistyped password); it keeps those values, never the password. The account-deletion page on this website signs in without sending your password, except for an account that has not yet used the newer sign-in; it asks first. Not receiving your password does not make a weak one safe: whoever runs the server, or gets a copy of its data, can try passwords against the values it keeps. {% comment %}P1{% endcomment %} | To create your account and let you sign in. | Until you delete your account. |
| **After you delete your account:** a record of your username, when you signed up and when you deleted the account. That record holds nothing else. Separately: an abuse report that someone filed about you is kept as described below; counts of failed sign-in attempts are kept as described below; and the server's encrypted backups and logs still hold older data until they age out (see "Server logs", and 8 days for backups). {% comment %}P28{% endcomment %} | Indian law (IT Rules 2021, Rule 3(1)(h)) requires us to keep registration details for 180 days after an account is deleted. | 180 days after deletion, then erased automatically. |
| **Your email:** stored only as a scrambled code (a keyed hash) plus a hint like s•••••@gmail.com, never as the address itself. {% comment %}P26{% endcomment %} | To let you sign in with your email and reset a forgotten password with a code we send to it. When you type your email, to sign in or to get a code, our server receives it and uses it for that step; at a sign-in it is held as typed until the sign-in finishes, at most about an hour. | Until you delete your account. |
| **Google sign-in (optional):** only Google's account identifier for you and a display name. Not your email or photo. {% comment %}P2{% endcomment %} | To let you sign in with Google, and to reset a forgotten password. | Until you delete your account. |
| **Your NexCall contacts:** who you have added, who asked to add you, who you blocked. {% comment %}P4{% endcomment %} | So you can message and call your contacts, and so blocking works. | Until you or they remove the contact, or an account is deleted. |
| **Presence:** whether you are online, and when you were last seen. {% comment %}P5{% endcomment %} | To show your contacts whether you are available. You can turn this off in Me › Privacy. | Updated as you use the app; removed when you delete your account. |
| **Messages waiting for delivery:** encrypted, unreadable to us. {% comment %}P6 P7{% endcomment %} | To deliver messages to a phone that is offline. | Deleted when delivered, or after 30 days. |
| **Photos, videos and files you send:** encrypted on your phone before upload, unreadable to us. {% comment %}P6 P8{% endcomment %} | To deliver attachments. | Deleted after 30 days. |
| **Message history backup:** encrypted on your phone before it is uploaded. The key that opens it never leaves your phone unprotected. If you sign in with a password, a copy of that key is kept on our server, locked with a key made from your password: this protects your backup from other people, but not from whoever runs the server, because the server receives your password when you set it. A backup opened only by your Google account's protected backup, a passkey or a recovery key you saved cannot be read by us. The app shows which of these you have in Me › Chats backup. {% comment %}P9{% endcomment %} | So you can restore your chats on a new phone. | The backup of a phone that is set up for messages on your account is kept until you delete your account. When a phone stops being one (a new phone or a reinstall replaced it, or you removed it), its backup is kept for at least 7 more days. After that it can be deleted the next time one of your phones backs up, unless that phone is one of the three most recently set up on your account, or its backup was set aside when a phone started fresh (kept 90 days). Up to three earlier versions of each phone's backup are kept beside the newest. If you choose a storage time in Me › Chats backup (30 days, 60 days or 1 year), voice-note backups older than that are deleted (a set-aside backup keeps its voice notes for its 90 days), and so is the backup of a phone that is no longer set up and has not backed up for that long. Deleting your account deletes all of it at once. |
| **Push token:** an identifier from Google's Firebase Cloud Messaging for your phone. {% comment %}P13{% endcomment %} | To wake your phone for an incoming call or message. The notification we send carries no names and no message content. | Replaced when it changes. When a sign-in is ended (sign-out, logged out, another phone took over), its token is used for up to 30 more days only to tell that phone that someone asked to replace your account's security key. The token of a sign-in that only lapsed stays until it changes or the account is deleted. Removed when you delete your account. |
| **Missed calls your phone has not collected:** when a call ends before it reached your phone, or while your phone had no connection, we keep who called, when, whether it was an audio or video call, and why it ended (not reached, not answered, or cancelled). Nothing is kept about a call that was answered or declined, or that your phone already knew about. {% comment %}P33{% endcomment %} | So your phone can show you the missed call when it is back online. | Deleted as soon as your phone has collected it, or after 7 days. |
| **Sign-in sessions.** {% comment %}P18{% endcomment %} | To keep you signed in. | A sign-in is renewed each time the app uses it, so one that stays in use does not end by itself. One that is not used ends after 7 days, or after a year with "Remember me" (the app's default). Signing in on another phone ends the sign-in on this one. You can end any other sign-in in Me › Security & Recovery › Devices & sessions; Sign out ends this one. |
| **Service-quality numbers:** once a day the app sends rough, anonymous numbers about how well calls and messages worked: bands of how long a call took to connect, its sound and picture quality, the kind of connection and network, and how long it lasted; and, counted per day, how long messages took to be sent and delivered and how often something failed. No user id, no IP address, no one else's details, nothing you said or sent; only the day, never the time. {% comment %}P29{% endcomment %} | To make calls and messages faster and more reliable. **On by default**; turn it off in Me › Privacy › "Help improve calls and messages", which also deletes anything not yet sent. | 90 days. |
| **Live call reports (temporary, while calls are being stabilised):** during a call, every 10 seconds, the app sends technical numbers about that call: picture size, frame rate and bitrate sent and received, delay and loss, how loud your microphone is as a number (never the sound itself), whether voice focus is on, whether the sound goes to the earpiece, speaker, a wired headset or Bluetooth (the kind only, never the name of a headset), the kind of network and connection path, how warm the phone is, the battery level, how much charge the battery reports it has left, whether the phone is charging and the battery's temperature, the app version, and your phone model. Nothing you said or showed, no names, no addresses. These reports are **not anonymous**: each is stored with the call it belongs to, and the server knows which accounts were in that call. {% comment %}P32{% endcomment %} | To find out why a call had a poor picture or dropped, on either phone, and how much battery calls use. **On by default**; turn it off in Me › Privacy › "Help improve calls and messages". This will be removed when calls are stable. | In the server log only, for as long as that log keeps it (see "Server logs"). |
| **Call-quality reports:** when a call fails, the app sends the network type, whether a VPN was on, your mobile carrier's code, technical connection details, why the call ended, and the app version. No user id, no IP address, no one else's details; the time is rounded to the hour. {% comment %}P14{% endcomment %} | To find and fix call failures. This is **on by default**; turn it off in Me › Privacy › "Help improve calls and messages". | 90 days. |
| **Abuse reports** you file: who you reported, the reason, anything you wrote, and — **only if you report a specific message — the text of that one message, sent from your phone**, with who sent it and when. The app tells you this before you send. {% comment %}P15{% endcomment %} | To act on abuse and meet our legal duties. | Until the report is resolved, then 180 days. If you delete your account, a report you filed stays without your name. A report filed about you keeps your username, the reason, what the reporter wrote and any message they quoted, until it is resolved and then 180 days. |
| **Server logs:** the requested address (without search terms), the result, a shortened IP address (the last part removed), and your account id on some single-account events such as sign-in. Log lines about a call carry only a random call number, never who was on it, and our call relay keeps no logs at all. {% comment %}P12 P17{% endcomment %} | To keep the service running and secure, and to investigate misuse. | Limited by size: older lines are overwritten as new ones arrive. The server's own full log files are deleted 7 days after they were last written; the hosting software's copy of the same lines is limited by size only. |
| **Devices & sessions:** for each sign-in to your account, the device name the app reports (for example "Samsung SM-S921B"), when it signed in and was last active, and a shortened IP address (the last part removed). {% comment %}P12{% endcomment %} | To show you, in Me › Security & Recovery › Devices & sessions, where your account is signed in, and to let you log any device out. | Until you delete your account. The app shows a sign-in that has ended for 30 days; the server's record of it (device name, times, shortened IP address, and why it ended) stays until the account is deleted. |
| **Sign-in attempts that did not succeed:** for the account or name that was tried, a count and the times of the first and last attempt, stored under a code made with a secret key of the server, not under the name. A second count, with the same times, is kept under your account's id until a password sign-in succeeds, you change your password, or the account is deleted. For each place an attempt came from, a count and times stored under a code made from that network address and the name that was typed; this code is made without a secret key. While a sign-in is in progress the name as typed is held, at most about an hour. {% comment %}NC-BL-135{% endcomment %} | To make a place that keeps guessing a password wait (after 10 wrong tries: 1 minute, then 10, then 60), and to record in your account's security record when sign-in attempts keep failing (the published app does not show that record yet). | The count for an account or name: until a sign-in under it succeeds, or 24 hours after the last attempt. The count for a place: until a sign-in from that place under that name succeeds; after a lock-out, 24 hours after the lock ended; a place that never reached the lock-out is not removed on a timer. |
| **Security record:** when something security-relevant happened on your account: a new sign-in; your password or Google account used to confirm a sign-in on a device that is not signed in; your messages moved to another phone, or a messaging device removed; a passkey added or removed; automatic sign-in on a new phone set up; Google sign-in added or removed; the password copy of your backup key turned on or removed; a copy of your backup key or account key handed to a signed-in phone; your password or email changed; your other sign-ins ended; your backup storage time changed; where a sign-in's notifications are sent was changed or cleared; a sign-in found to have been used in two places; several sign-in attempts that did not succeed. Only what kind of change and when, and which of your sign-ins made it; no content. {% comment %}P34{% endcomment %} | So the app can show you what happened on your account (the published app does not show this record yet) and warn your other phones. | 180 days. |

**What we cannot see.** Messages, attachments and calls are end-to-end
encrypted between the phones taking part. (Backups are described in the table
above.) Your phone learns which keys belong to a contact from our server the
first time; comparing the safety number with that contact confirms no one,
including us, is in between. Calls go directly between phones, or
through our relay server, which passes on encrypted traffic it cannot decrypt.
We never record calls. Your phone finds its network path with our own server,
not a third party's. With "Hide my IP on calls" (Me › Calls) every call goes
through our relay, so the other person never learns your IP address. {% comment %}P6 P9 P10{% endcomment %}

**What we can see (metadata).** To deliver messages and connect calls, our
server knows which accounts message or call each other, when, and how large
messages are. {% comment %}P11{% endcomment %}

## 2. On your phone

The app keeps your messages (in an encrypted store), your call history, a copy
of your contact list and your settings on your phone. None of it is included in
Android's own backups. NexCall's own encrypted backup (see the table) holds your
messages, chat settings, nicknames, profile, call list and newest voice notes,
and brings them back on a new phone. After you sign in on a phone with a screen
lock and Google backup on, the app also saves a sign-in key with Android's
device backup, encrypted under your screen lock, so
that a phone set up from that backup can sign in by itself; it stops working
when you sign in anywhere else or sign out. {% comment %}P25{% endcomment %}

Your **recovery key**, which opens your message backup, is kept on your phone
and in Google Block Store. Block Store copies it to your Google account only
when your phone has a screen lock (on our test phone, also only with Google
backup on), and Google then encrypts that copy end to end; otherwise the key
stays on your phone only. If
a password copy of this key exists (see the table above), our server stores it
locked with a key made from your password. Our server cannot open that copy as
it runs, but whoever runs the server can try passwords against it. If you add
a passkey, the server stores a copy locked by the passkey, which it cannot
open. {% comment %}P20{% endcomment %}

## 3. Who else handles your data

We do not sell or share your data. These service providers process it for us:
{% comment %}P19 P21{% endcomment %}

| Provider | What for | What they receive |
|---|---|---|
| Oracle Cloud (India, Hyderabad region) | Hosting the server; storing encrypted database backups (kept 7 days) | Everything the server stores, as described above. Backups are encrypted before they are sent to Oracle's storage. The key is not stored with the backups; it is on our server, which Oracle hosts. |
| Google (Firebase Cloud Messaging) | Waking your phone for calls and messages | Your push token and a wake-up signal without names or content |
| Google (Sign-In, Block Store, Android device backup) | Optional Google sign-in; backing up your recovery key and your automatic sign-in key to your Google account | Your sign-in request; your recovery key and sign-in key, stored in your own Google account |
| Google (Gmail) | Sending sign-up and password-reset codes, and a "your password was changed" notice after a reset by emailed code | The email address you typed and the message |
| Let's Encrypt | The server's security certificate | Our domain name only |

The app contains no advertising, analytics or crash-reporting software. {% comment %}P21{% endcomment %}

Our server and its backups are in India. Google processes the push token and your Google sign-in on its own servers, which may be outside India. {% comment %}P19 P21{% endcomment %}

## 4. Your rights

Under the DPDP Act you can:

- **Know what we hold about you.** Your profile is shown in the app (Me). For a
  full summary, write to the grievance officer. {% comment %}P24{% endcomment %}
- **Correct it.** Change your display name, username, email and password in
  the app (Me › Profile, Me › Security & Recovery). {% comment %}P23 P26{% endcomment %}
- **Erase it.** Delete your account in the app (Me › Security & Recovery ›
  Delete account) or on [the deletion page](delete-account). Server data is removed at
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
