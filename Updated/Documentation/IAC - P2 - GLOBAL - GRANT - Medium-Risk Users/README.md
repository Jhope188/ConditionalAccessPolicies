# IAC - P2 - GLOBAL - GRANT - Medium-Risk Users

**State:** Report-only  
**Policy ID:** `7475b373-0544-4ee8-8827-cff35009136d`

## Intent

Requires MFA and secure password change for users assessed as medium-risk by Entra Identity Protection. Medium user risk typically indicates credential exposure in data breaches. Requires Entra ID P2.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | User risk: medium, Client apps: all |
| **Grant Controls** | ✅ Require MFA AND 🔑 Require password change |
| **Session Controls** | — |

## Audit Findings

- ID: 7475b373-0544-4ee8-8827-cff35009136d
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
