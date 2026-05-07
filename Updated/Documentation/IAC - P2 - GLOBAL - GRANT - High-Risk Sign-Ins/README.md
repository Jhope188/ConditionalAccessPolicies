# IAC - P2 - GLOBAL - GRANT - High-Risk Sign-Ins

**State:** Report-only  
**Policy ID:** `53a8df0b-4658-4835-ace2-100b5d287aac`

## Intent

Requires MFA re-authentication and password change for sign-ins Entra Identity Protection assesses as high-risk. High-risk indicators include impossible travel, threat intelligence matches, and anomalous token characteristics. Requires Entra ID P2.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Sign-in risk: high, Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | Sign-in frequency: null null |

## Audit Findings

- ID: 53a8df0b-4658-4835-ace2-100b5d287aac
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
