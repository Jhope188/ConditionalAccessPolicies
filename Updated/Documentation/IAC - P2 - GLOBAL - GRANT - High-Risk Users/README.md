# IAC - P2 - GLOBAL - GRANT - High-Risk Users

**State:** Report-only  
**Policy ID:** `bb6a814e-808a-467c-9475-06f89140ce99`

## Intent

Blocks or requires password change for users whose account is flagged as high-risk by Entra Identity Protection (e.g., leaked credentials detected). Ensures compromised accounts cannot continue operating until risk is remediated. Requires Entra ID P2.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | User risk: high, Client apps: all |
| **Grant Controls** | ✅ Require MFA AND 🔑 Require password change |
| **Session Controls** | Sign-in frequency: null null |

## Audit Findings

- ID: bb6a814e-808a-467c-9475-06f89140ce99
- [INFO]  Policy is in report-only mode
- [MEDIUM]  All guest/external user type(s) excluded
- [INFO]  Break-glass group excluded ✓
