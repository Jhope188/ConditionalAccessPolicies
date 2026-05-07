# IAC - GLOBAL - SESSION - Windows - TokenProtection

**State:** Report-only  
**Policy ID:** `8bb25c6a-ed35-4556-bed4-b3aaa14e192b`

## Intent

Cryptographically binds access tokens to the specific Windows device that authenticated, preventing token replay attacks even if a token is exfiltrated from memory or disk. Requires Entra ID P2. Scoped to Windows Entra-joined and Hybrid Entra-joined devices only.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | Office 365 Exchange Online, Office 365 SharePoint Online, Windows 365, Azure Virtual Desktop, Microsoft Teams Services |
| **Conditions** | Platforms: windows, Client apps: mobileAppsAndDesktopClients, Device filter: device.systemLabels -contains "CloudPC" -and device.trustType -eq "AzureAD" |
| **Grant Controls** | — |
| **Session Controls** | — |

## Audit Findings

- ID: 8bb25c6a-ed35-4556-bed4-b3aaa14e192b
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
