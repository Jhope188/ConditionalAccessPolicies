# IAC - GLOBAL – SESSION – All Users Persistence (9-12 Hours)

**State:** Report-only  
**Policy ID:** `ea9459a9-91b6-4d2b-b929-03781ac81d54`

## Intent

Sets sign-in frequency to 9-12 hours for all licensed internal users. Balances security (limits session token lifetime) with usability (avoids excessive re-authentication friction during a working day). Non-persistent browser sessions for unmanaged devices.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: browser |
| **Grant Controls** | — |
| **Session Controls** | Sign-in frequency: 12 hours, Persistent browser: never |

## Audit Findings

- ID: ea9459a9-91b6-4d2b-b929-03781ac81d54
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
