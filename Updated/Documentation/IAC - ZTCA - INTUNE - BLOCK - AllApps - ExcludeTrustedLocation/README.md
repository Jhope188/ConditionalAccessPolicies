# IAC - ZTCA - INTUNE - BLOCK - AllApps - ExcludeTrustedLocation

**State:** Report-only  
**Policy ID:** `2dd84b12-7900-40f0-b192-027c20aaa83f`

## Intent

Zero Trust CA policy that blocks all app access from devices that are not Intune-compliant, excluding trusted locations. Enforces device compliance as a condition for all resource access in a Zero Trust Architecture posture.

> ⚠️ **Incident Response Use Disclaimer:** This policy, and its companion (IAC- ZTCA - GLOBAL - BLOCK - AllApps -Exclude CA-Global), are designed and maintained as **incident response tooling**, not as standing production controls. The intent is to give responders a pre-built "kill switch" that, in the event of a major breach, can be enabled to immediately collapse the organization's access surface down to one trusted account operating from one trusted location — paired with an immediate credential/session revocation script to cut off attacker access as fast as possible. These policies must be carefully considered before enabling in a live production environment, and should be tested and rehearsed ahead of time. Building or tuning a policy like this in the middle of an active incident is not the goal — it should already exist, already be understood, and already be ready to flip on.

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
