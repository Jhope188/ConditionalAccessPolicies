# IAC - APP – BLOCK – AVD - Exclude - AllowedAVDUsers

**State:** Report-only  
**Policy ID:** `9bc2ad69-4aed-4242-807d-788446196b8b`

## Intent

Blocks access to Azure Virtual Desktop for users not in the AllowedAVDUsers group. AVD is a high-privilege remote access surface — access should be explicitly granted to a defined set of users rather than open to all.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (4 exclusions) |
| **Cloud Apps** | Windows 365, Azure Virtual Desktop |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 9bc2ad69-4aed-4242-807d-788446196b8b
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
