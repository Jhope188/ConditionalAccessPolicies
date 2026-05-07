# IAC - INTUNE – GRANT – Device Registration from trusted location

**State:** Report-only  
**Policy ID:** `aeb49474-5250-4b65-8b0a-56c47127ee0f`

## Intent

Requires devices to be registered with Entra ID (Intune enrollment) only from trusted network locations. Prevents device registration from unknown or untrusted networks, reducing the risk of attacker-controlled devices being enrolled in the tenant.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | User actions: urn:user:registerdevice |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Multifactor authentication |
| **Session Controls** | — |

## Audit Findings

- ID: aeb49474-5250-4b65-8b0a-56c47127ee0f
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
