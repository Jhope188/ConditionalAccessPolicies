# IAC - P2 - GLOBAL - BLOCK - RiskyUsers - RegisterSecurityInfo

**State:** Report-only  
**Policy ID:** `768858bd-a5ad-47de-8acb-5e815cde0857`

## Intent

Blocks high-risk and medium-risk users from registering new security information (MFA methods, passkeys). Prevents an attacker who has compromised a risky account from registering their own authentication methods to maintain persistent access. Requires Entra ID P2.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | User actions: urn:user:registersecurityinfo |
| **Conditions** | User risk: high, medium, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 768858bd-a5ad-47de-8acb-5e815cde0857
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
