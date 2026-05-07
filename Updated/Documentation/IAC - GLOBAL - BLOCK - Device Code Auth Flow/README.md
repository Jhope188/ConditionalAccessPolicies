# IAC - GLOBAL - BLOCK - Device Code Auth Flow

**State:** Enabled  
**Policy ID:** `8b42eda3-6917-4ab4-afb2-e32c37520f9b`

## Intent

Blocks the OAuth 2.0 device code flow across all users and apps. Device code phishing (Storm-2372 pattern) exploits this flow to bypass MFA by tricking users into entering codes on attacker-controlled pages. Blocking this eliminates that attack vector. Exceptions for documented DevOps pipelines should use the CA-Azure-DevOps exclusion group.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 8b42eda3-6917-4ab4-afb2-e32c37520f9b
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓
