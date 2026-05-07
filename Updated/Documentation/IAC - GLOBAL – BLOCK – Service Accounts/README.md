# IAC - GLOBAL – BLOCK – Service Accounts

**State:** Report-only  
**Policy ID:** `99eabebd-877c-4800-aa15-d389b8767760`

## Intent

Blocks sign-in for non-interactive service accounts (members of CA-ServiceAccounts) from interactive sign-in flows. Service accounts should authenticate via managed identities, workload identities, or certificate-based flows — not through user-interactive sessions.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: IAC - Trusted Locations (IP), Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 99eabebd-877c-4800-aa15-d389b8767760
- [HIGH]  Device Registration Service bypasses location-based conditions
- [INFO]  Policy is in report-only mode
- [MEDIUM]  Named location "IAC - Trusted Locations (IP)" is not marked as trusted
- [INFO]  Break-glass group excluded ✓
