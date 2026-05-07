# IAC - GLOBAL – BLOCK – Countries not Allowed

**State:** Enabled  
**Policy ID:** `f3f4ad30-86a8-4e29-8ec9-4efab1a459f5`

## Intent

Blocks sign-in from countries on the Inforcer Blocked Countries named location. Targeted blocklist — only blocks named high-risk countries, permits everything else. Lower lockout risk than an allowlist approach. Only the CA-Breakglass group is excluded.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: IAC - AllowedCountries, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: f3f4ad30-86a8-4e29-8ec9-4efab1a459f5
- [HIGH]  Device Registration Service bypasses location-based conditions
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓
