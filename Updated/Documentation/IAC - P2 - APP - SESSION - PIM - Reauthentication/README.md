# IAC - P2 - APP - SESSION - PIM - Reauthentication

**State:** Report-only  
**Policy ID:** `a6b3b754-9079-48f0-abb2-9e79b2f41095`

## Intent

Requires reauthentication (authentication context c1 — PIM-ReAuthentication) when accessing Privileged Identity Management to activate roles. Ensures that PIM role activations always trigger a fresh authentication challenge, preventing session reuse for privilege escalation.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | — |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | Sign-in frequency: null null |

## Audit Findings

- ID: a6b3b754-9079-48f0-abb2-9e79b2f41095
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
