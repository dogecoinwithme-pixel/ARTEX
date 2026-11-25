# Coveo Public Bug Bounty — Intigriti

## Scope
- `*.cloud.coveo.com`
- `platform.cloud.coveo.com`
- `analytics.cloud.coveo.com`
- `knowledge.cloud.coveo.com`
- `commerce.cloud.coveo.com`
- `static.cloud.coveo.com`
- `https://docs.coveo.com`
- GitHub: `github.com/coveo`, `github.com/coveooss`, `github.com/coveord`

## Rules of engagement
- Required header: `X-Intigriti-Username: hackesteck`
- User-Agent: `Intigriti - hackesteck - <browser UA>`
- Max 5 requests/sec; 2FA required; ID check; no collaboration.
- Never exceed 5 organizations.

## Authentication model
- `platformTokens` — Bearer JWT for `/rest/*` (platform APIs).
- `searchTokens` — Bearer JWT scoped to a search organization.
- `apiKey` — Bearer; can carry `apiKeyQueryAuthentication` impersonation.
- `oauth2` — authorization code and legacy implicit (`v8`), scope `full`.

Platform token body: `{"sub": "...", "body": {"organizationId": "...", "privileges": [...]}}`.

## High-value areas
- Indexing Pipeline Extension sandbox escape (host/Kubernetes compromise, cross-tenant).
- Cross-organization BOLA/IDOR on `/rest/organizations/{organizationId}/...`.
- Search document permission-set violations.
- Commerce / Merchandising Hub.
- API key creation, rotation, exposure and impersonated query authentication.
- SAML identity provider configuration.
- Atlassian Connect app install/install lifecycle.
- OAuth/SAML authorization server.

## Out of scope / known
- Public demo organization tokens with limited privileges (EXECUTE_QUERY, EDIT_ANALYTICS_DATA).
- Stored XSS in Hosted Search Pages by a user with HTML edit privileges.
- Indexing Pipeline Extension code execution without sandbox escape.
- CORS misconfiguration without demonstrated impact.
- Admin UI hidden/disabled options reachable by direct API when the privilege is granted.
- Rate-limit bypass, missing cookie/security headers, username/email enumeration, email bombing.

## Local research state
- `bugbounty-edslawn-01` — `e6btrv6j9rcvoorg` (owner `hackesteck@intigriti.me`)
- `intigriti_researcher_trial` — `rli0z0b357cvoorg` (owner `hackesteck@intigriti.me`)
- Bearer token is stored locally only; never commit it.
