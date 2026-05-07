# IAC - GLOBAL - GRANT - MFA - Mixed-Guests

**State:** Report-only  
**Policy ID:** `e0fabad3-bd0f-42e4-a901-51ef7ab8889c`

## Intent

Requires MFA for all guest users including ad hoc guests without a formal home tenant relationship. Catches guests that don't qualify as B2B collaboration users and ensures all external identities must complete MFA before accessing resources.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 0 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | ✅ Require MFA |
| **Session Controls** | — |

## Audit Findings

- ID: e0fabad3-bd0f-42e4-a901-51ef7ab8889c
- [INFO]  Policy is in report-only mode
- [HIGH]  Guest users required to satisfy MFA — may need Cross-Tenant Access Settings
