# IAC - P2 - GLOBAL - GRANT - Medium-Risk Sign-Ins

**State:** Report-only  
**Policy ID:** `180ab5a3-d3ae-4457-9ef1-e3c06f5dfbfc`

## Intent

Requires MFA for sign-ins assessed as medium-risk by Entra Identity Protection. Medium-risk indicators include unfamiliar sign-in properties and atypical travel. Softer response than high-risk — MFA without forced password change. Requires Entra ID P2.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Sign-in risk: medium, Client apps: all |
| **Grant Controls** | ✅ Require MFA |
| **Session Controls** | — |

## Audit Findings

- ID: 180ab5a3-d3ae-4457-9ef1-e3c06f5dfbfc
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
