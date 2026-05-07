# IAC - GLOBAL - GRANT - MFA-Passkeys - ADM-Users

**State:** Report-only  
**Policy ID:** `a53c4c2b-b577-4d88-b64d-36b92f8f3ca0`

## Intent

Requires admin-role users to authenticate using a passkey (FIDO2 or device-bound passkey) specifically. Elevates the authentication requirement for privileged accounts beyond standard MFA — passkeys are phishing-resistant by design and cannot be intercepted or replayed.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: a53c4c2b-b577-4d88-b64d-36b92f8f3ca0
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
