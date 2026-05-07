# IAC - ZTCA - INTUNE - BLOCK - AllApps - ExcludeTrustedLocation

**State:** Report-only  
**Policy ID:** `2dd84b12-7900-40f0-b192-027c20aaa83f`

## Intent

Zero Trust CA policy that blocks all app access from devices that are not Intune-compliant, excluding trusted locations. Enforces device compliance as a condition for all resource access in a Zero Trust Architecture posture.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: All trusted locations, Client apps: all, Device filter: device.isCompliant -eq True -or device.trustType -eq "ServerAD" -or device.trustType -eq "Workplace" |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 2dd84b12-7900-40f0-b192-027c20aaa83f
- [HIGH]  Device Registration Service bypasses location-based conditions
- [INFO]  Policy is in report-only mode
- [HIGH]  Policy uses "All trusted locations" but 5 location(s) are NOT trusted
- [MEDIUM]  1 guest/external user type(s) excluded
- [INFO]  Break-glass group excluded ✓
