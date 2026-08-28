# IAC - P2 - GLOBAL - GRANT - High-Risk Users - Risk Remediation

**State:** Enabled  
**Policy ID:** `544cd9ef-5e37-4568-9ad8-b8e151be1814`  
**Created:** 2026-08-17  
**License Requirement:** Entra ID P2 (Identity Protection)

---

## Intent

Forces high-risk users (standard population) through **risk remediation** — a secure password change via SSPR — combined with phishing-resistant authentication and every-time re-authentication. When Entra Identity Protection flags a user as high-risk (leaked credentials, confirmed breach, anomalous activity), this policy ensures the compromise window is closed by requiring the user to prove identity and change their password before continuing.

This is the **standard-population** policy. Users in the EAM (External Authentication Method) group are excluded here and handled by a companion policy (`IAC - P2 - GLOBAL - GRANT - EAM - High-Risk Users - Risk Remediation`) that uses built-in MFA instead of an auth strength object.

> 📖 [Require password change for high-risk users — Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-risk-based-user)  
> 📖 [Risk-based Conditional Access policies best practices](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies)

---

## Policy Screenshot

![IAC - P2 - GLOBAL - GRANT - High-Risk Users - Risk Remediation](./%20IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20High-Risk%20Users%20-%20Risk%20Remediation.png)

---

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users |
| **Excluded Groups** | Break-glass (`5628ad67`), EAM group (`8d0564e5`) |
| **Cloud Apps** | All resources |
| **Conditions** | User risk: **High**, Client apps: all |
| **Grant Controls** | ✅ Auth strength: Modern MFA + TAP **AND** 🔑 Risk remediation |
| **Grant Operator** | AND |
| **Session Controls** | Sign-in frequency: **Every time** |

### Authentication Strength — Modern MFA + TAP

| Method | Notes |
|--------|-------|
| Windows Hello for Business | Phishing-resistant |
| FIDO2 security key | Phishing-resistant |
| Certificate-based (MFA) | Phishing-resistant |
| Temporary Access Pass (one-time) | Onboarding / recovery only |

### Why AND + Every Time?

- **AND operator**: Both auth strength AND risk remediation must be satisfied — proving identity is not enough, the password must also be changed
- **Every time SIF**: Prevents a compromised token from being replayed — the user must fully re-authenticate on every session until risk is dismissed
- **Risk remediation** (`riskRemediation`): The Graph API successor to `passwordChange` — requires the user to complete a secure password reset via SSPR, which dismisses the risk flag in Identity Protection

---

## Companion Policy

| Policy | Purpose |
|--------|---------|
| [IAC - P2 - GLOBAL - GRANT - EAM - High-Risk Users - Risk Remediation](../IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20EAM%20-%20High-Risk%20Users%20-%20Risk%20Remediation/README.md) | Same intent, targets EAM group only — uses built-in MFA instead of auth strength |

---

## Deployment Notes

- Requires **Entra ID P2** and **Identity Protection** to be enabled
- Requires **SSPR** to be configured — users cannot complete risk remediation without it
- The EAM group (`8d0564e5`) **must** be excluded here and covered by the companion policy — auth strength objects cannot be satisfied by external authentication methods
- Enable in **report-only first** and review Identity Protection sign-in logs before enforcing
- Break-glass accounts must be excluded to prevent lockout during incidents

---

## References

- [Require password change for high-risk users](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-risk-based-user)
- [Risk-based CA policy best practices](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies)
- [Authentication strength overview](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strengths)
- [Self-service password reset](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-howitworks)
