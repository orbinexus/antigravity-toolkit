---
name: oauth2-sso-architect
description: Implements secure OAuth2 and OIDC social authentication (Google, GitHub, Apple, Microsoft) with PKCE flow, state validation, session rotation, and account linking.
---

# OAuth2 & Social SSO Authentication Architect

This skill directs the implementation of enterprise-grade, secure OAuth 2.0 and OpenID Connect (OIDC) authentication flows across web and mobile platforms.

## 1. Security Architecture & Flow Standards

1. **Mandatory PKCE (Proof Key for Code Exchange)**:
   - Always generate a cryptographically random `code_verifier` (43-128 chars) and derived `code_challenge` (SHA-256) for authorization code grants.
2. **CSRF State Verification**:
   - Store an encrypted, short-lived nonce/state token in an `HttpOnly`, `SameSite=Lax`, `Secure` cookie before redirecting to the Identity Provider (IdP).
   - Validate strict equivalence on callback before exchanging the authorization code.
3. **Session & Token Management**:
   - Store access tokens in encrypted memory or secure session stores; never expose raw JWTs to client-side `localStorage`.
   - Implement refresh token rotation: invalidating previous refresh tokens upon every renewal.

## 2. Account Linking & Identity Resolution
- Match authenticated email addresses only when verified by the provider (`email_verified: true`).
- Provide explicit UI confirmation before linking an external social provider to an existing password-authenticated account.
