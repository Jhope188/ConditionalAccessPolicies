# IAC- ZTCA - GLOBAL - BLOCK - AllApps -Exclude CA-Global

**State:** Report-only  
**Policy ID:** `8417ec17-17f5-44c1-b937-85b1917f5d9e`

## Intent

Zero Trust CA policy that blocks all cloud app access by default, with only explicitly allowed exceptions. CA-Global exclusion group allows specific workloads and identities to operate outside this blanket block. Enforces explicit, verified access for all other traffic.

> ⚠️ **Incident Response Use Disclaimer:** This policy, and its companion (IAC - ZTCA - INTUNE - BLOCK - AllApps - ExcludeTrustedLocation), are designed and maintained as **incident response tooling**, not as standing production controls. The intent is to give responders a pre-built "kill switch" that, in the event of a major breach, can be enabled to immediately collapse the organization's access surface down to one trusted account operating from one trusted location — paired with an immediate credential/session revocation script to cut off attacker access as fast as possible. These policies must be carefully considered before enabling in a live production environment, and should be tested and rehearsed ahead of time. Building or tuning a policy like this in the middle of an active incident is not the goal — it should already exist, already be understood, and already be ready to flip on.

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
