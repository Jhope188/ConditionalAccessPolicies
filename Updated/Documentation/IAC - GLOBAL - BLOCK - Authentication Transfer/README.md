# IAC - GLOBAL - BLOCK - Authentication Transfer

**State:** Report-only  
**Policy ID:** `fa005ec2-4940-49c8-b4e7-b58e66ef481c`

## Intent

Blocks the authentication transfer flow, which allows session tokens to be moved between devices. This flow is a vector for token theft and lateral movement. Legitimate use cases are minimal — block broadly.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: fa005ec2-4940-49c8-b4e7-b58e66ef481c
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
