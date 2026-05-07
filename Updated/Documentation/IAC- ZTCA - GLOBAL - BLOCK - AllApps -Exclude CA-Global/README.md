# IAC- ZTCA - GLOBAL - BLOCK - AllApps -Exclude CA-Global

**State:** Report-only  
**Policy ID:** `8417ec17-17f5-44c1-b937-85b1917f5d9e`

## Intent

Zero Trust CA policy that blocks all cloud app access by default, with only explicitly allowed exceptions. CA-Global exclusion group allows specific workloads and identities to operate outside this blanket block. Enforces explicit, verified access for all other traffic.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 8417ec17-17f5-44c1-b937-85b1917f5d9e
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
