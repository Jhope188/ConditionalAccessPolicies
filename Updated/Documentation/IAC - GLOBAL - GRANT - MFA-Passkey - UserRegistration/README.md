# IAC - GLOBAL - GRANT - MFA-Passkey - UserRegistration

**State:** Report-only  
**Policy ID:** `30a1edce-e832-456b-b2c5-4b1098d3a9b3`

## Intent

Requires MFA completion before users can register new security information (passkeys, authenticator app, FIDO2 keys). Prevents an attacker who has stolen a password from registering their own MFA methods. Enforces the registration process through a secure, authenticated path.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | User actions: urn:user:registerdevice |
| **Conditions** | Platforms: iOS (exclude: macOS, windows), Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: 30a1edce-e832-456b-b2c5-4b1098d3a9b3
- [INFO]  Policy is in report-only mode
- [HIGH]  Platform condition only targets iOS — user-agent spoofing risk
- [INFO]  Break-glass group excluded ✓
