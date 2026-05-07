# IAC - APP - inforcer - RequireMFA

**State:** Report-only  
**Policy ID:** `1d3a7677-a723-4c56-924c-2e1dc63df105`

## Intent

Requires MFA to access the Inforcer application specifically. Ensures that the management plane for tenant configuration (Inforcer itself) cannot be accessed without a second factor, regardless of broader MFA policy state.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | Inforcer Integration |
| **Conditions** | Locations: All locations, Client apps: all |
| **Grant Controls** | ✅ Require MFA |
| **Session Controls** | — |

## Audit Findings

- ID: 1d3a7677-a723-4c56-924c-2e1dc63df105
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
