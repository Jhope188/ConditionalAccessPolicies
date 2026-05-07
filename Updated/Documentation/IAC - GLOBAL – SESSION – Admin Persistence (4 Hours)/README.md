# IAC - GLOBAL – SESSION – Admin Persistence (4 Hours)

**State:** Enabled  
**Policy ID:** `04b969aa-3e98-4e0f-8b32-2319b199b56a`

## Intent

Sets a 4-hour sign-in frequency for all admin-role users. After 4 hours of inactivity, admins must re-authenticate. Limits the window an attacker has to abuse a stolen admin session token. Non-persistent browser sessions enforced in admin contexts.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 11 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: browser |
| **Grant Controls** | — |
| **Session Controls** | Sign-in frequency: 4 hours, Persistent browser: never |

## Audit Findings

- ID: 04b969aa-3e98-4e0f-8b32-2319b199b56a
- [INFO]  Break-glass group excluded ✓
