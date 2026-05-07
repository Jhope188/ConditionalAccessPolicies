# IAC - GLOBAL - GRANT - MFA - AllAdmins

**State:** Enabled  
**Policy ID:** `f893f39f-2ab3-4f1e-a8e1-9a2b9589a9ce`

## Intent

Requires MFA for all users holding admin directory roles (scoped via ADM-Users-Dynamic). Admin accounts are the highest-value targets — this policy ensures every privileged action requires a second factor. Applies phishing-resistant authentication strength where configured.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 43 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: f893f39f-2ab3-4f1e-a8e1-9a2b9589a9ce
- [INFO]  Break-glass group excluded ✓
