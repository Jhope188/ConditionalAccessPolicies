# IAC - GLOBAL - GRANT - BreakGlass - TrustedLocations

**State:** Report-only  
**Policy ID:** `1588fdc7-f34a-468e-8023-4d788ef5d226`

## Intent

Allows break-glass accounts to authenticate only from trusted network locations. Adds a location-based constraint to emergency access — even if break-glass credentials are compromised, they cannot be used from arbitrary internet locations.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: IAC - Trusted Locations (IP), Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: 1588fdc7-f34a-468e-8023-4d788ef5d226
- [HIGH]  Device Registration Service bypasses location-based conditions
- [INFO]  Policy is in report-only mode
- [MEDIUM]  Named location "IAC - Trusted Locations (IP)" is not marked as trusted
- [MEDIUM]  Break-glass group not excluded (report-only policy)
