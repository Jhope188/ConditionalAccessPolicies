# IAC - GLOBAL - GRANT - MFA - AllUsers

**State:** Report-only  
**Policy ID:** `a66e8427-e5e7-4072-bfd1-7e99db7a7dc4`

## Intent

Baseline MFA requirement for all licensed internal users (CA-P1InternalLicensedUsers). The broadest user-facing policy in the stack — requires completion of MFA on every sign-in. Should be enabled last in Phase 1 after confirming all users have a capable authentication method.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | All cloud apps (2 exclusions) |
| **Conditions** | Client apps: all |
| **Grant Controls** | ✅ Require MFA |
| **Session Controls** | — |

## Audit Findings

- ID: a66e8427-e5e7-4072-bfd1-7e99db7a7dc4
- [MEDIUM]  2 app(s) excluded from "All resources" — verify low-privilege scope enforcement rollout
- [MEDIUM]  2 app(s) excluded from this policy
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
