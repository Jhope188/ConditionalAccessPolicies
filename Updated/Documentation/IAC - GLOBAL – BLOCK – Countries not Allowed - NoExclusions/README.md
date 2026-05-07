# IAC - GLOBAL – BLOCK – Countries not Allowed - NoExclusions

**State:** Enabled  
**Policy ID:** `1eaf943a-abad-4c77-b101-0c5342fc1044`

## Intent

Blocks sign-in from blocked countries with no group exclusions whatsoever — not even service accounts. Intended as a hardened complement to the standard blocked-countries policy for scenarios where any exclusion creates unacceptable risk.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: IAC - Blocked Countries, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 1eaf943a-abad-4c77-b101-0c5342fc1044
- [HIGH]  Device Registration Service bypasses location-based conditions
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓
