# IAC - AGENT - BLOCK - NonTrustedAgents

**State:** Report-only  
**Policy ID:** `1d8beea4-2ea1-4758-8e22-d6310a60220a`

## Intent

Blocks sign-in for AI agent identities that are not in the approved/trusted agent set. Implements a default-deny posture for agent workload identities — only explicitly approved agents can authenticate.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 1d8beea4-2ea1-4758-8e22-d6310a60220a
- [INFO]  Policy is in report-only mode
- [MEDIUM]  Break-glass group not excluded (report-only policy)
