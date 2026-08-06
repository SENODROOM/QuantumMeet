# SSO / OIDC plan (E-401 light)

## Target

Org-scoped SSO via **OIDC** first (Azure AD / Google Workspace / Okta); SAML as stretch for legacy IdPs.

## Prerequisites

- Orgs GA (`FEATURE_ORGS=1`, E-205)
- Stable `user.email` + org membership

## Spike steps

1. Pick IdP for staging (Auth0 / Clerk / raw `openid-client`).
2. Map IdP `sub` + email → QuantumMeet user; auto-join org by domain claim.
3. Keep password login for non-SSO orgs.
4. Document logout / session revocation.

SCIM (E-402) deferred until SSO accepted.
