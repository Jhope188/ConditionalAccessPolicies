# IAC - ZTCA - GLOBAL – BLOCK – Admin Portal

**State:** Report-only  
**Policy ID:** `fafaa50c-0b61-4ac6-a589-f9a1120b2f9e`

## Intent

Blocks access to Microsoft admin portals (Azure Portal, Entra Admin Center, Intune, Purview, M365 Admin, Defender) for non-admin users. Prevents accidental or unauthorized access to admin interfaces from standard user accounts.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | Inforcer Integration, Azure Resource Manager, MicrosoftAdminPortals, Microsoft Purview Platform, My Staff |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: fafaa50c-0b61-4ac6-a589-f9a1120b2f9e
- [HIGH]  4 app(s) excluded from this policy (1 high-risk)
- [INFO]  Policy is in report-only mode
- [LOW]  1 guest/external user type(s) excluded
- [INFO]  Break-glass group excluded ✓
