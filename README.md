# NexCall legal pages (GitHub Pages source)

Privacy policy, terms and the account-deletion page. Published from a separate
public repository with GitHub Pages; see ADR-047 for why and for the evidence
behind every statement. `_config.yml` holds the server domain and the
grievance contact, and `draft: true` puts a DRAFT banner on every page.

The deletion page calls the server from the browser, so the server's
`CORS_ORIGIN` must be set to this site's origin (for example
`https://<github-user>.github.io`).

## The deletion page signs in without sending the password

`delete-account.md` runs the same OPAQUE exchange as the app, in the browser,
with the WebAssembly client in `assets/opaque/` (ADR-091 step A). That client is
built from `android/rust/nexcall-opaque-web` (`npm run build:opaque-web` in
`backend/`), and `backend/tests/webOpaqueClient.test.js` fails when it was not
rebuilt after a change to `nexcall-opaque` or to the web crate. The page checks a
SHA-256 of both files before it runs them, against `_data/opaque_web.json`
(written by the build). When publishing, copy `assets/` and `_data/` too, from
the same commit. A plain password is sent only for an account the server says has no
OPAQUE record, and only after the page has said so and the second button was
pressed.

To try the page against a local server with a temporary database:
`node scripts/lab/site-delete-page-lab.js`.
