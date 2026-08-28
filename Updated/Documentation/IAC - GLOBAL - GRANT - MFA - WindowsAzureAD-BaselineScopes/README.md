# IAC - GLOBAL - GRANT - MFA - WindowsAzureAD-BaselineScopes

**State:** Report-only  
**Policy ID:** `ab659968-2e8a-4448-9710-d930aada3499`  
**Created:** 2026-08-28

---

## Intent

Closes the **directory baseline scope gap** created by the March 2026 Microsoft enforcement change.

When any "All resources" CA policy has **resource exclusions**, low-privilege directory scopes (`User.Read`, `openid`, `profile`, `email`, `offline_access`, `People.Read`) were previously exempt from enforcement. Microsoft has changed this — those scopes are now mapped to the **Windows Azure Active Directory** resource (`00000002-0000-0000-c000-000000000000`) as the enforcement audience.

This policy directly targets that resource, ensuring all token requests to Azure AD Graph directory scopes meet the same MFA requirement as the rest of the baseline — even when other "All resources" policies contain exclusions.

> **Microsoft documentation:**
> *"If the recommended baseline MFA policy without resource exclusions can't be configured because of business reasons, create a separate Conditional Access policy targeting Windows Azure Active Directory (00000002-0000-0000-c000-000000000000)."*
>
> 📖 [Conditional Access: Target resources — Protect directory information](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps#protect-directory-information)

---

## Policy Screenshot

![IAC - GLOBAL - GRANT - MFA - WindowsAzureAD-BaselineScopes](IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20WindowsAzureAD-BaselineScopes.png)

---

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users |
| **Excluded Users** | Break-glass group (`5628ad67-f9d1-4495-abe3-99dc8f9074f1`) |
| **Cloud Apps** | Windows Azure Active Directory (`00000002-0000-0000-c000-000000000000`) |
| **Conditions** | Client apps: all |
| **Grant Controls** | ✅ Require authentication strength: **Modern MFA + TAP** |
| **Session Controls** | — |

### Authentication Strength — Modern MFA + TAP

| Method | Notes |
|--------|-------|
| Windows Hello for Business | Phishing-resistant |
| FIDO2 security key | Phishing-resistant |
| Certificate-based (MFA) | Phishing-resistant |
| Temporary Access Pass (one-time) | Onboarding / recovery only |

---

## Why This Policy Is Needed

Microsoft's CA engine evaluates policies against the **resource** being accessed, not the client app. The Windows Azure Active Directory resource (`00000002-0000-0000-c000-000000000000`) is included in "All resources" but when excluded from a policy, it becomes **completely unprotected** — no CA enforcement at all.

This matters because nearly every application requests at minimum `User.Read` or `openid` scopes against this resource as part of the sign-in flow. Without this policy:

- Apps excluded from your "All resources" policies can read directory data without MFA
- Confidential client apps could enumerate users (`User.ReadBasic.All`), group memberships (`GroupMember.Read.All`), and hidden memberships (`Member.Read.Hidden`) without CA enforcement

---

## Deployment Notes

- Enable in **report-only first** and review sign-in logs for the `Windows Azure Active Directory` resource
- Entra Admin Center → Entra ID → Monitoring → Sign-in logs → Filter: Resource = `Windows Azure Active Directory`
- Verify no apps break before enabling
- Exclude the same break-glass group used across all baseline policies

---

## Related Policies

| Policy | Relationship |
|--------|-------------|
| IAC - GLOBAL - GRANT - MFA - AllUsers | Baseline "All resources" policy — this policy covers the Azure AD Graph resource for any exclusions in that policy |
| IAC - GLOBAL - GRANT - MFA - AllAdmins | Admin baseline — Azure AD Graph scoped here too |

---

## References

- [Conditional Access: Target resources](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps)
- [Protect directory information](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps#protect-directory-information)
- [Enforcement for baseline scopes (enforcement change)](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-enforcement-resource-exclusions)
- [Baseline MFA for all users](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-mfa-strength)
