# IAC - GLOBAL - GRANT - MFA - B2B-Guest

**State:** Report-only  
**Policy ID:** `f25f94e0-98b6-41be-b9d6-68cb781004a4`

## Intent

Requires MFA for external B2B collaboration users (formal partner/guest accounts with a home tenant). Separate from the mixed-guest policy to allow different authentication strength requirements for formal B2B relationships vs ad hoc guests.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 0 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: f25f94e0-98b6-41be-b9d6-68cb781004a4
- [INFO]  Policy is in report-only mode
- [MEDIUM]  Guest users required to satisfy Authentication strength: Modern MFA + TAP — may need Cross-Tenant Access Settings
