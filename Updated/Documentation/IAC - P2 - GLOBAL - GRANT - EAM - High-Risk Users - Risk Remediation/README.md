# IAC - P2 - GLOBAL - GRANT - EAM - High-Risk Users - Risk Remediation

**State:** Enabled  
**Policy ID:** `bb6a814e-808a-467c-9475-06f89140ce99`  
**Created:** 2026-05-06  
**License Requirement:** Entra ID P2 (Identity Protection)

---

## Intent

Companion to `IAC - P2 - GLOBAL - GRANT - High-Risk Users - Risk Remediation`. Targets users enrolled in **External Authentication Methods (EAM)** who cannot satisfy a custom authentication strength object. Uses the built-in `mfa` control + `riskRemediation` instead, applying every-time sign-in frequency to fully close the compromise window for this population.

EAM users authenticate via a third-party MFA provider (e.g. Duo, Okta). Because custom auth strength objects do not accept EAM claims, a separate policy with the built-in `mfa` control is required to avoid blocking this population while still enforcing the same risk remediation requirement.

> 📖 [Require password change for high-risk users — Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-risk-based-user)  
> 📖 [Risk-based Conditional Access policies best practices](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies)

---

## Policy Screenshot

![IAC - P2 - GLOBAL - GRANT - EAM - High-Risk Users - Risk Remediation](IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20EAM%20-%20High-Risk%20Users%20-%20Risk%20Remediation.png)

---

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | EAM group only (`8d0564e5-ab28-4283-9a94-9883c581adde`) |
| **Excluded Groups** | Break-glass (`5628ad67`), Additional exclusion group (`b63c3682`) |
| **Cloud Apps** | All resources |
| **Conditions** | User risk: **High**, Client apps: all |
| **Grant Controls** | ✅ Require MFA **AND** 🔑 Risk remediation |
| **Grant Operator** | AND |
| **Session Controls** | Sign-in frequency: **Every time** |

### Why Built-in MFA Instead of Auth Strength?

Custom authentication strength objects evaluate specific credential combinations (FIDO2, WHfB, CBA). EAM providers satisfy the built-in `mfa` claim but are not enumerated in auth strength combination lists. Using the built-in `mfa` control here allows EAM-enrolled users to satisfy the policy using their external provider while still enforcing risk remediation.

### Why AND + Every Time?

- **AND operator**: Both MFA AND risk remediation must be satisfied — the password must be changed, not just MFA completed
- **Every time SIF**: Forces full re-authentication on every session until Identity Protection dismisses the risk
- **Risk remediation** (`riskRemediation`): Requires secure password reset via SSPR, which closes the Identity Protection risk flag

---

## Companion Policy

| Policy | Purpose |
|--------|---------|
| [IAC - P2 - GLOBAL - GRANT - High-Risk Users - Risk Remediation](../IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20High-Risk%20Users%20-%20Risk%20Remediation/README.md) | Standard population — uses auth strength (Modern MFA + TAP) |

---

## Deployment Notes

- Requires **Entra ID P2** and **Identity Protection** to be enabled
- Requires **SSPR** to be configured
- The EAM inclusion group (`8d0564e5`) must exactly match the group excluded from the companion standard policy — any user in both groups would be double-covered; any user in neither would have no risk remediation policy
- Enable in **report-only first**, validate with Identity Protection risky users report
- Break-glass accounts must be excluded

---

## References

- [Require password change for high-risk users](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-risk-based-user)
- [Risk-based CA policy best practices](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies)
- [External authentication methods](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-external-method-manage)
- [Self-service password reset](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-howitworks)
