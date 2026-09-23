---
layout: default
title: Delete your account
---
{% comment %}ADR-046 (what is deleted), ADR-047 P22.{% endcomment %}

# Delete your NexCall account

## In the app (easiest)

Open NexCall › **Me** › **Security & Recovery** › **Delete account**, and
confirm with your password (or with Google, if you sign in with Google).

## On this page

If you no longer have the app, sign in below with your username and password.
Your account is deleted as soon as you confirm.

<form id="del" autocomplete="off">
  <label for="u">Username</label>
  <input id="u" name="u" required autocapitalize="none" spellcheck="false">
  <label for="p">Password</label>
  <input id="p" name="p" type="password" required>
  <label><input id="c" type="checkbox" style="width:auto"> I understand this cannot be undone.</label>
  <button id="go" type="submit">Delete my account permanently</button>
</form>
<p id="out" role="status"></p>

<script>
(function () {
  var server = 'https://{{ site.server_domain }}';
  var form = document.getElementById('del');
  var out = document.getElementById('out');
  var go = document.getElementById('go');
  function say(t) { out.textContent = t; }
  function error(res, body) {
    return (body && body.error && body.error.message) || ('The server said ' + res.status + '.');
  }
  form.addEventListener('submit', function (e) {
    e.preventDefault();
    if (!document.getElementById('c').checked) { say('Tick the box to confirm.'); return; }
    go.disabled = true;
    say('Signing in…');
    var username = document.getElementById('u').value.trim();
    var password = document.getElementById('p').value;
    fetch(server + '/api/auth/login', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ username: username, password: password, rememberMe: false })
    }).then(function (res) {
      return res.json().catch(function () { return null; }).then(function (body) {
        if (!res.ok) throw new Error(error(res, body));
        var ticket = body.tickets && body.tickets.ACCOUNT_DELETE;
        if (!ticket) throw new Error('This server cannot delete accounts from the web yet.');
        say('Deleting…');
        return fetch(server + '/api/users/me', {
          method: 'DELETE',
          headers: { 'Content-Type': 'application/json', Authorization: 'Bearer ' + body.accessToken },
          body: JSON.stringify({ ticket: ticket })
        });
      });
    }).then(function (res) {
      return res.json().catch(function () { return null; }).then(function (body) {
        if (!res.ok) throw new Error(error(res, body));
        form.reset();
        say('Your account has been deleted.');
      });
    }).catch(function (err) {
      say((err && err.message) || 'Something went wrong. Nothing was deleted.');
    }).then(function () { go.disabled = false; });
  });
})();
</script>

## If you sign in only with Google, or cannot sign in

Write to {{ site.grievance_name }} at <{{ site.grievance_email }}> from any
address, with your NexCall username. We may ask you to show the account is
yours before we delete it, and we delete it within 15 days of your request.

## What is deleted

- **At once, from the server:** your profile, contacts, sign-in sessions, push
  token, messages still waiting to be delivered (sent and received),
  attachments, your encrypted message backups, and your encryption keys.
- **Within 8 days:** the same data in our encrypted server backups.
- **On the phone** (when you delete in the app): your messages, call history,
  and your recovery key in Google Block Store.

## What is kept

- Messages you already sent are on the recipients' phones; we cannot reach them.
- Abuse reports stay, without the link to your account, until resolved and
  then 180 days.
- Call-quality reports carry no account id and expire after 90 days.
- Server logs are overwritten over time (see the [privacy policy](privacy)).
