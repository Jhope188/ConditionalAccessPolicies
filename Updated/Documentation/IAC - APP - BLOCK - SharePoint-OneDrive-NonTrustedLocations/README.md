# IAC - APP - BLOCK - SharePoint-OneDrive-NonTrustedLocations

**State:** Report-only  
**Policy ID:** `1f960ec9-885f-4032-a6b2-a5c559279274`

## Intent

Blocks access to SharePoint Online and OneDrive from network locations not listed in the Inforcer Trusted Locations named location. Protects sensitive collaboration content from being accessed from untrusted or unknown networks.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (4 exclusions) |
| **Cloud Apps** | Office 365 SharePoint Online |
| **Conditions** | Locations: All locations, Exclude locations: All trusted locations, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 1f960ec9-885f-4032-a6b2-a5c559279274
- [INFO]  Policy is in report-only mode
- [HIGH]  Policy uses "All trusted locations" but 5 location(s) are NOT trusted
- [INFO]  Break-glass group excluded ✓
