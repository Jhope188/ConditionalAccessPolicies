# IAC - APP - SESSION - O365 - Timeoutsettings

**State:** Report-only  
**Policy ID:** `c5133041-079f-45ec-b27a-20268546077f`

## Intent

Applies session timeout controls to Office 365 applications. Configures sign-in frequency and browser session persistence settings for Exchange, Teams, SharePoint, and other O365 workloads to reduce the risk of abandoned authenticated sessions.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | Office365 |
| **Conditions** | Platforms: all (exclude: android, iOS, macOS, linux), Client apps: browser, Device filter: device.isCompliant -eq True -and device.trustType -eq "ServerAD" |
| **Grant Controls** | — |
| **Session Controls** | — |

## Audit Findings

- ID: c5133041-079f-45ec-b27a-20268546077f
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
