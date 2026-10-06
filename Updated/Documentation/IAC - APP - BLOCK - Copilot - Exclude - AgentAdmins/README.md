# IAC - APP - BLOCK - Copilot - Exclude - AgentAdmins

**State:** Enabled  
**Policy ID:** `3e2ff4cb-9ed1-42bc-9714-c3d4abac55e2`

## Intent

Blocks access to Microsoft Copilot (Enterprise Copilot Platform and Security Copilot Portal) for all users by default. Only members of the AgentAdmins group are permitted to use these Copilot experiences — everyone else is denied, implementing a default-deny posture for Copilot access until users are explicitly approved.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | Enterprise Copilot Platform, Security Copilot Portal |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 3e2ff4cb-9ed1-42bc-9714-c3d4abac55e2
- [MEDIUM]  Policy is enabled (not report-only) — confirm testing/validation is complete before leaving in production
- [INFO]  Break-glass group excluded ✓

> **Note:** This policy was switched to **On** (from Report-only) by the policy owner for live testing and verification. Confirm scope and exclusions are validated, then keep enabled or revert to report-only as appropriate for your change process.


![IAC - APP - BLOCK - Copilot - Exclude - AgentAdmins](IAC%20-%20APP%20-%20BLOCK%20-%20Copilot%20-%20Exclude%20-%20AgentAdmins.png)
