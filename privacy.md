---
layout: default
title: Privacy policy
---
{% comment %}
Every statement below carries a claim id (P1…P34, and backlog ids). The evidence for each id is
in docs/adr/2026-09-23_ADR-047_PERSONAL_DATA_DISCLOSURES.md in the NexCall
repository. Change a sentence only together with its row there.
{% endcomment %}

# Privacy policy

**Last updated:** 11 October 2026

This Privacy Policy explains how NexCall collects, uses, stores, protects, and deletes personal data when you use our mobile application, website, messaging, voice and video calling, account recovery, and related services.

It identifies the data we process, the purposes for processing it, the service providers involved, how long data is retained, and how you can exercise your privacy rights or raise a complaint.

NexCall aims to comply with applicable Indian privacy and information technology laws, including the Digital Personal Data Protection Act, 2023, the Digital Personal Data Protection Rules, 2025, as and when their respective provisions apply, and the Information Technology (Intermediary Guidelines and Digital Media Ethics Code) Rules, 2021, where applicable.

**Data Fiduciary:** {{ site.grievance_name }}

**Privacy and grievance contact:** {{ site.grievance_email }}

## The short version

- **Private communications:** Messages, attachments, voice notes, and calls are designed to use end-to-end encryption. Our server cannot ordinarily decrypt this content in transit. Backup protection depends on the backup and recovery method you choose. {% comment %}P6 P9 P10{% endcomment %}
- **What we do not collect:** NexCall does not collect your phone number, your phone's contacts, or your location. {% comment %}P3{% endcomment %}
- **Account information:** We process account identifiers, usernames, authentication records, and limited email-related information to provide sign-in, account recovery, and security features. {% comment %}P1 P3 P26{% endcomment %}
- **Contacts and activity:** We process NexCall contact relationships, presence settings, message-delivery information, and call-related metadata needed to operate the service. {% comment %}P4 P5 P11{% endcomment %}
- **Technical diagnostics:** NexCall may process call and message quality information, connection details, device information, and security logs. You can disable the optional quality-reporting features described below. {% comment %}P12 P14 P29 P32{% endcomment %}
- **No advertising:** NexCall does not use third-party advertising or analytics SDKs, as described in this policy. Operational service logs and first-party diagnostic reporting are separate from third-party advertising analytics. {% comment %}P21{% endcomment %}
- **Your choices:** You can manage available privacy settings, withdraw consent where applicable, request access to your personal data, correct information, and delete your account. {% comment %}P22 P23 P24{% endcomment %}
- **Third-party services:** Google, Oracle Cloud, and other listed providers process certain information to support NexCall. Their own processing may be governed by their respective privacy policies. {% comment %}P19{% endcomment %}

## 1. What we collect and why

| Data | Why | How long we keep it |
|---|---|---|
| **Your account:** username, display name, when you signed up, and values made from your password that a sign-in is checked against. We do not keep the password itself. From version 0.6.0-beta97 of the app, your password is not sent to our server when you create your account, sign in, change it using your current password, or reset it with an emailed code. The app proves that you know it instead. It is still sent, and the app asks you first, in two cases: an account that has not yet been moved to this newer sign-in (when it signs in with the new version, until it has been moved, or if you change its password before that); and when you set or change a password after confirming with Google instead of with your current password. Older versions of the app send your password when you create your account, when you change or reset it, and at some sign-ins. The account-deletion page on this website sends it only for an account that has not been moved to the newer sign-in, and asks first. For an account that was made with an older version, we may still keep an older one-way hash of the password beside the newer values. Not receiving your password does not make a weak one safe: whoever runs the server, or gets a copy of its data, can try passwords against the values it keeps. {% comment %}P1{% endcomment %} | To create your account and let you sign in. | Until you delete your account. |
| **After you delete your account:** a record of your username, when you signed up and when you deleted the account. That record holds nothing else. Separately: an abuse report that someone filed about you is kept as described below; counts of failed sign-in attempts are kept as described below; and the server's encrypted backups and logs still hold older data until they age out (see "Server logs", and 8 days for backups). {% comment %}P28{% endcomment %} | Indian law (IT Rules 2021, Rule 3(1)(h)) requires us to keep registration details for 180 days after an account is deleted. | 180 days after deletion, then erased automatically. |
| **Email address and email-derived identifiers:** When you enter your email address for registration, sign-in, or account recovery, our server processes it to perform that operation. During a sign-in flow, the address may be held temporarily in its original form for up to approximately one hour. For account storage, NexCall retains a keyed hash of the email address and a masked email hint, rather than the original address, as described in this policy. The keyed hash is not the same as encryption and cannot be reversed using the hash alone, although it may still be used to identify or match an address. {% comment %}P26{% endcomment %} | We use this information to support account identification, sign-in, and recovery. The email provider receives the address and message contents necessary to deliver verification and recovery emails. | The stored email-derived identifier and masked hint remain until account deletion, subject to the retention exceptions described in this policy. Temporary sign-in data is removed when the relevant process ends or the temporary retention period expires. |
| **Google sign-in (optional):** only Google's account identifier for you and a display name. Not your email or photo. {% comment %}P2{% endcomment %} | To let you sign in with Google, and to reset a forgotten password. | Until you delete your account. |
| **Your NexCall contacts:** who you have added, who asked to add you, who you blocked. {% comment %}P4{% endcomment %} | So you can message and call your contacts, and so blocking works. | Until you or they remove the contact, or an account is deleted. |
| **Presence:** whether you are online, and when you were last seen. {% comment %}P5{% endcomment %} | To show your contacts whether you are available. You can turn this off in Me › Privacy. | Updated as you use the app; removed when you delete your account. |
| **Messages waiting for delivery:** encrypted, unreadable to us. {% comment %}P6 P7{% endcomment %} | To deliver messages to a phone that is offline. | Deleted when delivered, or after 30 days. |
| **Photos, videos and files you send:** encrypted on your phone before upload, unreadable to us. {% comment %}P6 P8{% endcomment %} | To deliver attachments. | Deleted after 30 days. |
| **Message history backup:** encrypted on your phone before it is uploaded. The key that opens it never leaves your phone unprotected. A copy of that key, locked with a key made from your password, may be kept on our server. From version 0.6.0-beta97 the app makes this copy only if you turn on "Password also opens my backup" in Me › Chats backup; if an older version already made one without asking, the app asks you once whether to keep it or remove it. Older versions of the app make one for every account that signs in with a password, without asking. This copy protects your backup from other people. It does not protect it from whoever runs the server: older versions of the app send your password to the server, and even where the password is not sent, whoever runs the server or gets a copy of its data can try passwords against the copy. It is only as safe as your password. Removing it in the app deletes it from the server at once, and from the server's own backups within 8 days. Changing your password does not delete copies made under the old password. Turning "Password also opens my backup" off deletes them all. A backup opened only by your Google account's protected backup, a passkey or a recovery key you saved cannot be read by us. The app shows which of these you have in Me › Chats backup. {% comment %}P9{% endcomment %} | So you can restore your chats on a new phone. | The backup of a phone that is set up for messages on your account is kept until you delete your account. When a phone stops being one (a new phone or a reinstall replaced it, or you removed it), its backup is kept for at least 7 more days. After that it can be deleted the next time one of your phones backs up, unless that phone is one of the three most recently set up on your account, or its backup was set aside when a phone started fresh (kept 90 days). Up to three earlier versions of each phone's backup are kept beside the newest. If you choose a storage time in Me › Chats backup (30 days, 60 days or 1 year), voice-note backups older than that are deleted (a set-aside backup keeps its voice notes for its 90 days), and so is the backup of a phone that is no longer set up and has not backed up for that long. Deleting your account deletes all of it at once. |
| **Push token:** an identifier from Google's Firebase Cloud Messaging for your phone. {% comment %}P13{% endcomment %} | To wake your phone for an incoming call or message. The notification we send carries no names and no message content. | Replaced when it changes. When a sign-in is ended (sign-out, logged out, another phone took over), its token is used for up to 30 more days only to tell that phone that someone asked to replace your account's security key. The token of a sign-in that only lapsed stays until it changes or the account is deleted. Removed when you delete your account. |
| **Missed calls your phone has not collected:** when a call ends before it reached your phone, or while your phone had no connection, we keep who called, when, whether it was an audio or video call, and why it ended (not reached, not answered, or cancelled). Nothing is kept about a call that was answered or declined, or that your phone already knew about. {% comment %}P33{% endcomment %} | So your phone can show you the missed call when it is back online. | Deleted as soon as your phone has collected it, or after 7 days. |
| **Sign-in sessions.** {% comment %}P18{% endcomment %} | To keep you signed in. | A sign-in is renewed each time the app uses it, so one that stays in use does not end by itself. One that is not used ends after 7 days, or after a year with "Remember me" (the app's default). Signing in on another phone ends the sign-in on this one. You can end any other sign-in in Me › Security & Recovery › Devices & sessions; Sign out ends this one. |
| **Service-quality reports:** If enabled, NexCall collects limited technical measurements to understand how reliably messages and calls work. Daily reports may include call-connection duration bands, audio and video quality measurements, network type, call duration, message delivery delays, and failure counts. These reports are designed to exclude account identifiers, IP addresses, message content, and other users' details. {% comment %}P29{% endcomment %} | To understand how reliably messages and calls work. **On by default.** You can disable this reporting in **Me › Privacy › Help improve calls and messages**. Disabling it also removes reports that have not yet been transmitted, where supported by the app. | Up to 90 days. |
| **Temporary live-call diagnostics:** While call performance is being stabilised, NexCall may collect technical measurements during active calls, including frame rate, video bitrate, connection delay, packet loss, microphone-level measurements, audio routing type, network path, device model, app version, battery status, charging state and battery charge, device temperature, the size of the picture sent and received, and whether voice focus is on. These diagnostics are associated with the relevant call and are therefore **not anonymous**. They do not intentionally include the conversation's audio, video, message content, participant names, or contact details. NexCall does not record calls through this diagnostic feature. This statement does not describe any recording performed independently by a participant or their device. {% comment %}P32{% endcomment %} | Live-call diagnostics are used to investigate connection failures, call quality, and device performance. **On by default.** This temporary diagnostic collection will be removed when it is no longer required, and users can disable the applicable reporting setting in the app (**Me › Privacy › Help improve calls and messages**). | They are retained in server logs and follow the log-retention periods described under **Server logs**. |
| **Call-quality reports:** when a call fails, the app sends the network type, whether a VPN was on, your mobile carrier's code, technical connection details, why the call ended, and the app version. No user id, no IP address, no one else's details; the time is rounded to the hour. {% comment %}P14{% endcomment %} | To find and fix call failures. This is **on by default**; turn it off in Me › Privacy › "Help improve calls and messages". | 90 days. |
| **Abuse reports** you file: who you reported, the reason, anything you wrote, and — **only if you report a specific message — the text of that one message, sent from your phone**, with who sent it and when. The app tells you this before you send. {% comment %}P15{% endcomment %} | To act on abuse and meet our legal duties. | Until the report is resolved, then 180 days. If you delete your account, a report you filed stays without your name. A report filed about you keeps your username, the reason, what the reporter wrote and any message they quoted, until it is resolved and then 180 days. |
| **Server logs:** the requested address (without search terms), the result, a shortened IP address (the last part removed), and your account id on some single-account events such as sign-in. Log lines about a call carry only a random call number, never who was on it, and our call relay keeps no logs at all. {% comment %}P12 P17{% endcomment %} | To keep the service running and secure, and to investigate misuse. | Limited by size: older lines are overwritten as new ones arrive. The server's own full log files are deleted 7 days after they were last written; the hosting software's copy of the same lines is limited by size only. |
| **Devices & sessions:** for each sign-in to your account, the device name the app reports (for example "Samsung SM-S921B"), when it signed in and was last active, and a shortened IP address (the last part removed). {% comment %}P12{% endcomment %} | To show you, in Me › Security & Recovery › Devices & sessions, where your account is signed in, and to let you log any device out. | Until you delete your account. The app shows a sign-in that has ended for 30 days; the server's record of it (device name, times, shortened IP address, and why it ended) stays until the account is deleted. |
| **Sign-in attempts that did not succeed:** for the account or name that was tried, a count and the times of the first and last attempt, stored under a code made with a secret key of the server, not under the name. A second count, with the same times, is kept under your account's id until a password sign-in succeeds, you change your password, or the account is deleted. For each place an attempt came from, a count and times stored under a code made from that network address and the name that was typed; this code is made without a secret key. While a sign-in is in progress the name as typed is held, at most about an hour. {% comment %}NC-BL-135{% endcomment %} | To make a place that keeps guessing a password wait (after 10 wrong tries: 1 minute, then 10, then 60), and to record in your account's security record when sign-in attempts keep failing. | The count for an account or name: until a sign-in under it succeeds, or 24 hours after the last attempt. The count for a place: until a sign-in from that place under that name succeeds; after a lock-out, 24 hours after the lock ended; a place that never reached the lock-out is not removed on a timer. |
| **Security record:** when something security-relevant happened on your account: a new sign-in; your password or Google account used to confirm a sign-in on a device that is not signed in; your messages moved to another phone, or a messaging device removed; a passkey added or removed; automatic sign-in on a new phone set up; Google sign-in added or removed; the password copy of your backup key turned on or removed; a copy of your backup key or account key handed to a signed-in phone; your password or email changed; your other sign-ins ended; your backup storage time changed; where a sign-in's notifications are sent was changed or cleared; a sign-in found to have been used in two places; several sign-in attempts that did not succeed. Only what kind of change and when, and which of your sign-ins made it; no content. {% comment %}P34{% endcomment %} | So the app can show you what happened on your account and warn your other phones. | 180 days. |

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

NexCall does not sell personal data. We use the following service providers to operate, secure, and maintain the service. The information each provider receives depends on the feature you use. {% comment %}P19 P21{% endcomment %}

| Provider | Purpose | Information processed |
|---|---|---|
| Oracle Cloud | Hosting the application server and storing encrypted database backups | Information held by the hosted server and encrypted backup files. Access to information depends on the encryption and hosting configuration. |
| Google Firebase Cloud Messaging | Delivering push notifications | Push tokens and notification payloads needed to alert your device. |
| Google Sign-In | Optional authentication | Information supplied by Google during authentication, including the account identifier and permitted profile information. |
| Google Block Store and Android device backup | Supporting sign-in and recovery features | Eligible sign-in or recovery material, subject to Android, Google account, and device security behaviour. |
| Google (Gmail) | Sending verification and account recovery messages | The destination email address and the content needed to deliver the message. |
| Let's Encrypt | Issuing TLS certificates | Domain and certificate-validation information. |

NexCall's server and its backups are hosted in India, in Oracle Cloud's Hyderabad region. Some Google services may process information outside India. The location of data processing depends on the provider and the particular service. {% comment %}P19 P21{% endcomment %}

Service providers may process information under their own contractual terms and applicable privacy policies. NexCall remains responsible for the processing it controls and for providing accurate information about its service providers.

NexCall does not intentionally include third-party advertising, analytics, or crash-reporting SDKs in the app. This does not mean that operational server logs, first-party diagnostics, or infrastructure-level security logs are never generated. {% comment %}P21{% endcomment %}

**Link previews.** When link previews are on (**Me › Privacy › Link previews**), your phone fetches a website you put in a message directly, to show its title and picture. That website receives your phone's IP address, as it would if you opened it in a browser. NexCall's server is not involved in that fetch.

**This website.** These pages are hosted on GitHub Pages; GitHub receives the IP address of people who visit them. The account-deletion page talks to NexCall's own server.

Information may also be disclosed where required by applicable law or a valid legal process, or where necessary to investigate abuse, protect users, or secure the service, subject to applicable legal requirements.

## 4. Your privacy rights and choices

Subject to applicable law, you may:

- **Access information:** View the account information available in the app and request a summary of the personal data NexCall processes about you. {% comment %}P24{% endcomment %}
- **Correct information:** Update your username, display name, email-related account information, and other editable details through the relevant account settings. {% comment %}P23 P26{% endcomment %}
- **Request deletion:** Delete your account through **Me › Security & Recovery › Delete account** or the [account-deletion page](delete-account) on our website. {% comment %}P22{% endcomment %}
- **Withdraw consent:** Where processing relies on consent, withdraw it through the relevant in-app control or by contacting the grievance officer. Withdrawal does not affect the lawfulness of processing carried out before withdrawal.
- **Manage optional diagnostics:** Disable the applicable call and message quality-reporting settings in the app.
- **Raise a complaint:** Contact the grievance officer using the details below. If your complaint remains unresolved, you may complain to the Data Protection Board of India, or pursue any further remedy available under applicable law.
- **Nominate another person:** Where provided by applicable law, nominate another person to exercise your rights in the event of death or incapacity.

We will verify requests where reasonably necessary to protect your account and prevent unauthorised disclosure. We will respond within the time limits required by applicable law.

Deleting your account initiates deletion of associated server-side account data, subject to applicable legal retention requirements, security records, abuse reports, and the backup and log-retention periods explained in this policy. Messages already delivered to another participant may remain on that participant's device. {% comment %}P22 P28{% endcomment %}

To exercise a right or submit a request, contact **{{ site.grievance_email }}**. Please do not send your password, recovery key, or other authentication secrets in a privacy request.

## 5. Grievance officer and complaints

**Grievance officer:** {{ site.grievance_name }}

**Email:** {{ site.grievance_email }}

Contact the grievance officer for privacy complaints, requests concerning personal data, account-related concerns, or reports of misuse of the service.

Please include enough information to identify the issue, but do not include passwords, recovery keys, or unnecessary sensitive information.

We will acknowledge and resolve complaints within the applicable statutory time limits. Where the Information Technology Rules require acknowledgement within 24 hours and resolution within 15 days, we will follow those requirements. Specific unlawful-content complaints will be handled within the shorter deadlines applicable to the type of complaint:

- A request to remove content that is unlawful under Rule 3(1)(b) of the IT Rules is resolved within **72 hours**; content showing a person in a sexual act or nudity without consent is removed within **24 hours**.
- If you disagree with a decision under the IT Rules, you can appeal to the Grievance Appellate Committee within 30 days.

Privacy requests and complaints under the DPDP framework will be handled in accordance with the provisions and rules in force at the relevant time, and answered within **90 days** at the latest. If you remain dissatisfied, you may approach the Data Protection Board of India or any other competent authority or grievance mechanism available under applicable law.

## 6. Children

NexCall is not meant for anyone under 18. We do not knowingly create accounts
for children.

## 7. Security

NexCall uses technical and organisational safeguards intended to protect personal data, including TLS for connections to its servers, encryption for private communications, and encryption of supported backups before upload where described in this policy.

End-to-end encryption protects message and call content against decryption by the service during normal operation, but it does not eliminate every security risk. Metadata, account information, delivery records, diagnostic reports, and server logs may remain accessible to the service as described above.

Backup security depends on the recovery method selected, the protection of the relevant keys, and the security of your device and account. In particular, password-protected backup-key material may be vulnerable to attempts by someone with access to the server and the necessary stored data.

You should use a strong, unique password, keep your device protected, safeguard recovery keys, and compare safety numbers with contacts when available.

No internet service can guarantee absolute security. If you believe your account or personal data has been compromised, contact the grievance officer promptly. NexCall will handle security incidents and any required notifications in accordance with applicable law.

## 8. International transfers and legal disclosures

NexCall primarily hosts its server and backups in India. However, certain service providers may process personal data outside India, as described in the section on service providers.

Where personal data is transferred or made available outside India, NexCall will follow applicable Indian legal requirements and any relevant restrictions imposed by the competent authorities.

NexCall may disclose information when required by applicable law, a valid court order, or a lawful request from a competent authority. Where legally permitted, we will limit disclosure to the information reasonably required to comply with the request.

## 9. Changes

When this text changes, the version and date at the bottom of the page change
with it.
