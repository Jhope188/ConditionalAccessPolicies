# IAC - AGENT - BLOCK - HighRiskAgent

**State:** Report-only  
**Policy ID:** `0ab1380f-3863-40a5-ab97-24250e1cf44e`

## Intent

Blocks sign-in for AI agent identities assessed as high-risk by Entra Identity Protection. Agents with anomalous sign-in behavior, impossible travel, or threat intelligence matches are blocked from accessing resources until risk is cleared.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 0ab1380f-3863-40a5-ab97-24250e1cf44e
- [INFO]  Policy is in report-only mode
- [MEDIUM]  Break-glass group not excluded (report-only policy)
