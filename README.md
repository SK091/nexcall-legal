# NexCall legal pages (GitHub Pages source)

Privacy policy, terms and the account-deletion page. Published from a separate
public repository with GitHub Pages; see ADR-047 for why and for the evidence
behind every statement. `_config.yml` holds the server domain and the
grievance contact, and `draft: true` puts a DRAFT banner on every page.

The deletion page calls the server from the browser, so the server's
`CORS_ORIGIN` must be set to this site's origin (for example
`https://<github-user>.github.io`).
