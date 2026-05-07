# IAC - INTUNE - GRANT - RequireCompliantDevice

**State:** Report-only  
**Policy ID:** `660ab461-0de5-4b00-baea-ec7325280f60`

## Intent

Requires devices to be marked as compliant in Microsoft Intune before accessing corporate resources. Compliant devices must meet all configured compliance policies (encryption, OS version, antivirus, etc.). Enforces that only managed, healthy devices get access.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: All trusted locations, Client apps: all |
| **Grant Controls** | 📱 Require compliant device OR 💻 Require hybrid Azure AD joined |
| **Session Controls** | — |

## Audit Findings

- ID: 660ab461-0de5-4b00-baea-ec7325280f60
- [HIGH]  Grant controls use "OR" — weakest control is effective
- [HIGH]  Device Registration Service bypasses location-based conditions and compliant/hybrid-joined device requirement
- [MEDIUM]  Policy does not require MFA
- [INFO]  Policy is in report-only mode
- [HIGH]  Policy uses "All trusted locations" but 5 location(s) are NOT trusted
