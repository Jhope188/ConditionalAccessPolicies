# IAC - GLOBAL - BLOCK - Unsupported Device Platforms

**State:** Enabled  
**Policy ID:** `9e21fa64-8d9a-4e62-81da-9abce8859a0c`

## Intent

Restricts access from device platforms that cannot satisfy CA grant controls — such as unmanaged Linux desktops and legacy operating systems. Reduces unmanaged device risk without impacting managed Windows, macOS, iOS, and Android endpoints.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Platforms: all (exclude: android, iOS, windows, macOS), Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 9e21fa64-8d9a-4e62-81da-9abce8859a0c
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓
