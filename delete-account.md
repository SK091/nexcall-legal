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

If you no longer have the app, sign in below with your username (or email) and
password. Your account is deleted as soon as you confirm.

**Your password is not sent to us.** This page proves it to the server without
sending it, the same way the app does. One exception, and the page asks you
first: an account that has not yet signed in with the app's newer sign-in can
only be checked the old way, by sending the password once.

<form id="del" autocomplete="off">
  <label for="u">Username or email</label>
  <input id="u" name="u" required autocapitalize="none" spellcheck="false">
  <label for="p">Password</label>
  <input id="p" name="p" type="password" required>
  <label><input id="c" type="checkbox" style="width:auto"> I understand this cannot be undone.</label>
  <button id="go" type="submit">Delete my account permanently</button>
  <button id="plain" type="button" hidden>Send my password once and delete my account</button>
</form>
<p id="out" role="status"></p>
<noscript><p>This form needs JavaScript. Without it, write to us (below).</p></noscript>

<script type="module">
{% comment %}
ADR-091 step A. The page signs in over OPAQUE with the WebAssembly client in
assets/opaque (built from android/rust/nexcall-opaque-web; the same code the
app and the server run). A plain password is sent only for an account the
server says has no OPAQUE record, and only after the second button is pressed.

The client is handed the password, so the page does not run whatever is at
that address: it fetches the two files, checks a SHA-256 of each against the
values written here when the site was built (site/_data/opaque_web.json, from
`npm run build:opaque-web`), and runs exactly the bytes it checked.
{% endcomment %}
const server = 'https://{{ site.server_domain }}';
const ASSETS = '{{ site.baseurl }}/assets/opaque/';
const EXPECTED = {
  'nexcall_opaque_web.js': '{{ site.data.opaque_web.js_sha256 }}',
  'nexcall_opaque_web_bg.wasm': '{{ site.data.opaque_web.wasm_sha256 }}',
};
const NOT_CHECKED = 'This page could not check its own sign-in code, so it did not run it. Nothing was sent. ' +
  'Reload the page and try again; if it happens again, write to us.';

async function checked(name) {
  const res = await fetch(ASSETS + name, { cache: 'no-store' });
  if (!res.ok) throw new Error(NOT_CHECKED);
  const bytes = await res.arrayBuffer();
  const digest = new Uint8Array(await crypto.subtle.digest('SHA-256', bytes));
  const hex = Array.from(digest, (b) => b.toString(16).padStart(2, '0')).join('');
  if (!/^[0-9a-f]{64}$/.test(EXPECTED[name]) || hex !== EXPECTED[name]) throw new Error(NOT_CHECKED);
  return bytes;
}

let client = null;
/** The OPAQUE client, from bytes this page has checked. Loaded once. */
async function opaqueClient() {
  if (client) return client;
  const [js, wasm] = await Promise.all([checked('nexcall_opaque_web.js'), checked('nexcall_opaque_web_bg.wasm')]);
  const url = URL.createObjectURL(new Blob([js], { type: 'text/javascript' }));
  try {
    const mod = await import(url);
    await mod.default({ module_or_path: wasm });
    client = mod;
  } finally {
    URL.revokeObjectURL(url);
  }
  return client;
}
const form = document.getElementById('del');
const out = document.getElementById('out');
const go = document.getElementById('go');
const plain = document.getElementById('plain');
const say = (t) => { out.textContent = t; };
const b64 = (bytes) => btoa(String.fromCharCode.apply(null, bytes));
const unb64 = (text) => Uint8Array.from(atob(text), (c) => c.charCodeAt(0));
const WRONG = 'Wrong username or password.';

async function post(path, body, token) {
  const headers = { 'Content-Type': 'application/json' };
  if (token) headers.Authorization = 'Bearer ' + token;
  const res = await fetch(server + path, { method: 'POST', headers, body: JSON.stringify(body) });
  const json = await res.json().catch(() => null);
  return { res, json };
}
const errorOf = (r) => (r.json && r.json.error && r.json.error.message) || ('The server said ' + r.res.status + '.');

/** True when the server says this account can only be checked by sending the password. */
async function needsThePasswordSent(username) {
  try {
    const r = await post('/api/auth/sign-in-method', { username });
    return r.res.ok && r.json && r.json.opaque === false;
  } catch (e) {
    return false;
  }
}

/** Signs in without sending the password. Returns the session, or throws a message for the person. */
async function signInWithoutSendingIt(username, password) {
  const { web_login_start, web_login_finish } = await opaqueClient();
  const pw = new TextEncoder().encode(password);
  try {
    const step = web_login_start(pw);
    const start = await post('/api/auth/opaque/login/start', { username, request: b64(step.message) });
    if (start.res.status === 401) throw new Error(WRONG);
    if (!start.res.ok) throw new Error(errorOf(start));
    let finalization;
    try {
      finalization = web_login_finish(step.state, pw, unb64(start.json.response));
    } catch (e) {
      // A wrong password is found out here, in the page. Nothing more is sent.
      throw new Error(WRONG);
    }
    const finish = await post('/api/auth/opaque/login/finish', {
      attemptId: start.json.attemptId, finalization: b64(finalization), rememberMe: false,
    });
    if (finish.res.status === 401) throw new Error(WRONG);
    if (!finish.res.ok) throw new Error(errorOf(finish));
    return finish.json;
  } finally {
    pw.fill(0);
  }
}

async function signInBySendingIt(username, password) {
  const r = await post('/api/auth/login', { username, password, rememberMe: false });
  if (!r.res.ok) throw new Error(errorOf(r));
  return r.json;
}

async function deleteWith(session) {
  const ticket = session.tickets && session.tickets.ACCOUNT_DELETE;
  if (!ticket) throw new Error('This server cannot delete accounts from the web yet.');
  say('Deleting…');
  const res = await fetch(server + '/api/users/me', {
    method: 'DELETE',
    headers: { 'Content-Type': 'application/json', Authorization: 'Bearer ' + session.accessToken },
    body: JSON.stringify({ ticket }),
  });
  const json = await res.json().catch(() => null);
  if (!res.ok) throw new Error(errorOf({ res, json }));
  form.reset();
  plain.hidden = true;
  say('Your account has been deleted.');
}

async function run(sendIt) {
  if (!document.getElementById('c').checked) { say('Tick the box to confirm.'); return; }
  const username = document.getElementById('u').value.trim();
  const password = document.getElementById('p').value;
  go.disabled = true;
  plain.disabled = true;
  try {
    if (sendIt) {
      say('Signing in…');
      await deleteWith(await signInBySendingIt(username, password));
      return;
    }
    say('Checking…');
    if (await needsThePasswordSent(username)) {
      plain.hidden = false;
      say('This account was made before passwords were protected. To delete it from this page, your password ' +
        'has to be sent to the server once. Press the second button to do that, or sign in once in the app ' +
        'first (it upgrades the account), or write to us.');
      return;
    }
    say('Signing in…');
    await deleteWith(await signInWithoutSendingIt(username, password));
  } catch (err) {
    say((err && err.message) || 'Something went wrong. Nothing was deleted.');
  } finally {
    go.disabled = false;
    plain.disabled = false;
  }
}

form.addEventListener('submit', (e) => { e.preventDefault(); plain.hidden = true; run(false); });
plain.addEventListener('click', () => run(true));
</script>

## If you sign in only with Google, or cannot sign in

Write to {{ site.grievance_name }} at <{{ site.grievance_email }}> from any
address, with your NexCall username. We may ask you to show the account is
yours before we delete it, and we delete it within 15 days of your request.

## What is deleted

- **At once, from the server:** your profile (with the stored code of your
  email), contacts, sign-ins and the Devices & sessions list, push token,
  security record, missed calls waiting for you, messages still waiting to be
  delivered (sent and received), attachments, your encrypted message and
  voice-note backups, your passkeys, every stored copy of your backup key, and
  your encryption keys.
- **Within 8 days:** the same data in our encrypted server backups.
- **On the phone** (when you delete in the app): your messages, call history,
  and your recovery key in Google Block Store.

## What is kept

- Your username, when you signed up and when you deleted the account, for 180
  days. Indian law (IT Rules 2021, Rule 3(1)(h)) requires this.
- Messages you already sent are on the recipients' phones; we cannot reach them.
- Abuse reports stay. One you filed no longer names you. One filed about you
  keeps your username and what was reported, until it is resolved and then
  180 days.
- Call-quality reports carry no account id and expire after 90 days.
- Server logs are overwritten over time (see the [privacy policy](privacy)).
