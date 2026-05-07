# IAC - GLOBAL – BLOCK - Legacy Authentication

**State:** Enabled  
**Policy ID:** `9eab445f-7f21-479a-85c9-29769512067e`

## Intent

Blocks all legacy authentication protocols — SMTP AUTH, POP3, IMAP, MAPI over HTTP, and older Office clients that cannot negotiate modern auth. These protocols cannot satisfy MFA and are the primary vector for credential spray attacks. Zero legitimate modern-app impact.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: exchangeActiveSync, other |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 9eab445f-7f21-479a-85c9-29769512067e
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓
