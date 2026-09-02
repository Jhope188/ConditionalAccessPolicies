# IAC - INTUNE – GRANT – Device Registration - MFA Strength

**State:** Report-only  
**Policy ID:** `aeb49474-5250-4b65-8b0a-56c47127ee0f`

## Intent

Requires an authentication strength (Modern MFA + TAP) before a device can be registered with Entra ID (urn:user:registerdevice). Replaces the prior location-restricted version of this policy, which relied on trusted-location conditions that are silently not evaluated by the Device Registration Service.

The Device Registration Service (`01cb2876-7ebd-4aa4-9cc9-d28bd4d359a9`) only supports "Require multifactor authentication" as a grant control. Location, compliant-device, and hybrid-joined conditions are not evaluated for this service even though the Entra portal allows configuring them without error - the policy will appear to save successfully but those conditions have no effect on device registration. This was documented and MSRC-confirmed in research published by Fabian Bader (Cloudbrothers) following joint work with Dirk-jan Mollema at TROOPERS25 (VULN-153600).

> 📖 [Conditional Access: Target resources - Device registration](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps)

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (4 exclusions) |
| **Excluded Groups** | 2 standard exclusions, additional exclusion, break-glass group |
| **Cloud Apps** | User actions: urn:user:registerdevice |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: aeb49474-5250-4b65-8b0a-56c47127ee0f
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
- [INFO]  Replaces prior location-based version - Device Registration Service only enforces MFA, not location/compliance conditions
