# IAC - APP – BLOCK – AVD - NonTrustedLocations

**State:** Report-only  
**Policy ID:** `b13dd393-f644-45c8-81bf-aa7f4032ebd3`

## Intent

Blocks AVD access from non-trusted network locations even for authorized AVD users. Combines identity-based (group membership) and network-based (location) controls for Azure Virtual Desktop access.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | Windows 365, Azure Virtual Desktop |
| **Conditions** | Locations: All locations, Exclude locations: All trusted locations, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: b13dd393-f644-45c8-81bf-aa7f4032ebd3
- [INFO]  Policy is in report-only mode
- [HIGH]  Policy uses "All trusted locations" but 5 location(s) are NOT trusted
- [INFO]  Break-glass group excluded ✓
