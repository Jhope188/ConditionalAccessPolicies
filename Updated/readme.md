# Conditional Access Policy Review

**Generated:** August 28, 2026  
**Tenant:** ConditionalAccessFans.onmicrosoft.com  
**Total Policies:** 37

---

## Table of Contents

1. [IAC - GLOBAL - BLOCK - Device Code Auth Flow](#iac-global-block-device-code-auth-flow)

2. [IAC - GLOBAL - GRANT - MFA - AllAdmins](#iac-global-grant-mfa-alladmins)

3. [IAC - GLOBAL - BLOCK - Legacy Authentication](#iac-global-block-legacy-authentication)

4. [IAC - GLOBAL - BLOCK - Countries not Allowed](#iac-global-block-countries-not-allowed)

5. [IAC - GLOBAL - BLOCK - Countries not Allowed - NoExclusions](#iac-global-block-countries-not-allowed-noexclusions)

6. [IAC - GLOBAL - GRANT - MFA - AllUsers](#iac-global-grant-mfa-allusers)

7. [IAC - GLOBAL - BLOCK - Authentication Transfer](#iac-global-block-authentication-transfer)

8. [IAC - GLOBAL - BLOCK - Unsupported Device Platforms](#iac-global-block-unsupported-device-platforms)

9. [IAC - GLOBAL - GRANT - BreakGlass - TrustedLocations](#iac-global-grant-breakglass-trustedlocations)

10. [IAC - GLOBAL - GRANT - MFA-Passkey - UserRegistration](#iac-global-grant-mfa-passkey-userregistration)

11. [IAC - GLOBAL - GRANT - MFA-Passkeys - ADM-Users](#iac-global-grant-mfa-passkeys-adm-users)

12. [IAC - GLOBAL - SESSION - Windows - TokenProtection](#iac-global-session-windows-tokenprotection)

13. [IAC - GLOBAL - BLOCK - Service Accounts](#iac-global-block-service-accounts)

14. [IAC - GLOBAL - SESSION - Admin Persistence (4 Hours)](#iac-global-session-admin-persistence-4-hours)

15. [IAC - GLOBAL - SESSION - All Users Persistence (9-12 Hours)](#iac-global-session-all-users-persistence-9-12-hours)

16. [IAC - APP - BLOCK - SharePoint-OneDrive-NonTrustedLocations](#iac-app-block-sharepoint-onedrive-nontrustedlocations)

17. [IAC - APP - inforcer - RequireMFA](#iac-app-inforcer-requiremfa)

18. [IAC - APP - BLOCK - AVD - Exclude - AllowedAVDUsers](#iac-app-block-avd-exclude-allowedavdusers)

19. [IAC - APP - BLOCK - AVD - NonTrustedLocations](#iac-app-block-avd-nontrustedlocations)

20. [IAC - AGENT - BLOCK - HighRiskAgent](#iac-agent-block-highriskagent)

21. [IAC - AGENT - BLOCK - NonTrustedAgents](#iac-agent-block-nontrustedagents)

22. [IAC - INTUNE - GRANT - RequireCompliantDevice](#iac-intune-grant-requirecompliantdevice)

23. [IAC - INTUNE - GRANT - Device Registration from trusted location](#iac-intune-grant-device-registration-from-trusted-location)

24. [IAC - ZTCA - GLOBAL - BLOCK - Admin Portal](#iac-ztca-global-block-admin-portal)

25. [IAC - ZTCA - INTUNE - BLOCK - AllApps - ExcludeTrustedLocation](#iac-ztca-intune-block-allapps-excludetrustedlocation)

26. [IAC- ZTCA - GLOBAL - BLOCK - AllApps -Exclude CA-Global](#iac-ztca-global-block-allapps-exclude-ca-global)

27. [IAC - APP - SESSION - O365 - Timeoutsettings](#iac-app-session-o365-timeoutsettings)

28. [IAC - P2 - GLOBAL - GRANT - High-Risk Sign-Ins](#iac-p2-global-grant-high-risk-sign-ins)

29. [IAC - P2 - GLOBAL - GRANT - Medium-Risk Sign-Ins](#iac-p2-global-grant-medium-risk-sign-ins)

30. [IAC - P2 - GLOBAL - BLOCK - RiskyUsers - RegisterSecurityInfo](#iac-p2-global-block-riskyusers-registersecurityinfo)

31. [IAC - P2 - APP - SESSION - PIM - Reauthentication](#iac-p2-app-session-pim-reauthentication)

32. [IAC - GLOBAL - GRANT - MFA - B2B-Guest](#iac-global-grant-mfa-b2b-guest)

33. [IAC - GLOBAL - GRANT - MFA - Mixed-Guests](#iac-global-grant-mfa-mixed-guests)

34. [IAC - GLOBAL - GRANT - MFA - WindowsAzureAD-BaselineScopes](#iac-global-grant-mfa-windowsazuread-baselinescopes)

35. [IAC - P2 - GLOBAL - GRANT - High-Risk Users - Risk Remediation](#iac-p2-global-grant-high-risk-users-risk-remediation)

36. [IAC - P2 - GLOBAL - GRANT - EAM - High-Risk Users - Risk Remediation](#iac-p2-global-grant-eam-high-risk-users-risk-remediation)

37. [IAC - P2 - GLOBAL - GRANT - Medium-Risk Users - Risk Remediation](#iac-p2-global-grant-medium-risk-users-risk-remediation)


---

# IAC - GLOBAL - BLOCK - Device Code Auth Flow

**State:** Enabled  
**Policy ID:** `8b42eda3-6917-4ab4-afb2-e32c37520f9b`

## Intent

Blocks the OAuth 2.0 device code flow across all users and apps. Device code phishing (Storm-2372 pattern) exploits this flow to bypass MFA by tricking users into entering codes on attacker-controlled pages. Blocking this eliminates that attack vector. Exceptions for documented DevOps pipelines should use the CA-Azure-DevOps exclusion group.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 8b42eda3-6917-4ab4-afb2-e32c37520f9b
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL - BLOCK - Device Code Auth Flow](Documentation/IAC%20-%20GLOBAL%20-%20BLOCK%20-%20Device%20Code%20Auth%20Flow/IAC%20-%20GLOBAL%20-%20BLOCK%20-%20Device%20Code%20Auth%20Flow.png)


---


# IAC - GLOBAL - GRANT - MFA - AllAdmins

**State:** Enabled  
**Policy ID:** `f893f39f-2ab3-4f1e-a8e1-9a2b9589a9ce`

## Intent

Requires MFA for all users holding admin directory roles (scoped via ADM-Users-Dynamic). Admin accounts are the highest-value targets — this policy ensures every privileged action requires a second factor. Applies phishing-resistant authentication strength where configured.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 43 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: f893f39f-2ab3-4f1e-a8e1-9a2b9589a9ce
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL - GRANT - MFA - AllAdmins](Documentation/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20AllAdmins/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20AllAdmins.png)


---


# IAC - GLOBAL - BLOCK - Legacy Authentication

**State:** Enabled  
**Policy ID:** `9eab445f-7f21-479a-85c9-29769512067e`

## Intent

Blocks all legacy authentication protocols — SMTP AUTH, POP3, IMAP, MAPI over HTTP, and older Office clients that cannot negotiate modern auth. These protocols cannot satisfy MFA and are the primary vector for credential spray attacks. Zero legitimate modern-app impact.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: exchangeActiveSync, other |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 9eab445f-7f21-479a-85c9-29769512067e
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL – BLOCK - Legacy Authentication](Documentation/IAC%20-%20GLOBAL%20–%20BLOCK%20-%20Legacy%20Authentication/IAC%20-%20GLOBAL%20–%20BLOCK%20-%20Legacy%20Authentication.png)


---


# IAC - GLOBAL - BLOCK - Countries not Allowed

**State:** Enabled  
**Policy ID:** `f3f4ad30-86a8-4e29-8ec9-4efab1a459f5`

## Intent

Blocks sign-in from countries on the Inforcer Blocked Countries named location. Targeted blocklist — only blocks named high-risk countries, permits everything else. Lower lockout risk than an allowlist approach. Only the CA-Breakglass group is excluded.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: IAC - AllowedCountries, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: f3f4ad30-86a8-4e29-8ec9-4efab1a459f5
- [HIGH]  Device Registration Service bypasses location-based conditions
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL – BLOCK – Countries not Allowed](Documentation/IAC%20-%20GLOBAL%20–%20BLOCK%20–%20Countries%20not%20Allowed/IAC%20-%20GLOBAL%20–%20BLOCK%20–%20Countries%20not%20Allowed.png)


---


# IAC - GLOBAL - BLOCK - Countries not Allowed - NoExclusions

**State:** Enabled  
**Policy ID:** `1eaf943a-abad-4c77-b101-0c5342fc1044`

## Intent

Blocks sign-in from blocked countries with no group exclusions whatsoever — not even service accounts. Intended as a hardened complement to the standard blocked-countries policy for scenarios where any exclusion creates unacceptable risk.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: IAC - Blocked Countries, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 1eaf943a-abad-4c77-b101-0c5342fc1044
- [HIGH]  Device Registration Service bypasses location-based conditions
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL – BLOCK – Countries not Allowed - NoExclusions](Documentation/IAC%20-%20GLOBAL%20–%20BLOCK%20–%20Countries%20not%20Allowed%20-%20NoExclusions/IAC%20-%20GLOBAL%20–%20BLOCK%20–%20Countries%20not%20Allowed%20-%20NoExclusions.png)


---


# IAC - GLOBAL - GRANT - MFA - AllUsers

**State:** Report-only  
**Policy ID:** `a66e8427-e5e7-4072-bfd1-7e99db7a7dc4`

## Intent

Baseline MFA requirement for all licensed internal users (CA-P1InternalLicensedUsers). The broadest user-facing policy in the stack — requires completion of MFA on every sign-in. Should be enabled last in Phase 1 after confirming all users have a capable authentication method.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | All cloud apps (2 exclusions) |
| **Conditions** | Client apps: all |
| **Grant Controls** | ✅ Require MFA |
| **Session Controls** | — |

## Audit Findings

- ID: a66e8427-e5e7-4072-bfd1-7e99db7a7dc4
- [MEDIUM]  2 app(s) excluded from "All resources" — verify low-privilege scope enforcement rollout
- [MEDIUM]  2 app(s) excluded from this policy
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL - GRANT - MFA - AllUsers](Documentation/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20AllUsers/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20AllUsers.png)


---


# IAC - GLOBAL - BLOCK - Authentication Transfer

**State:** Report-only  
**Policy ID:** `fa005ec2-4940-49c8-b4e7-b58e66ef481c`

## Intent

Blocks the authentication transfer flow, which allows session tokens to be moved between devices. This flow is a vector for token theft and lateral movement. Legitimate use cases are minimal — block broadly.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: fa005ec2-4940-49c8-b4e7-b58e66ef481c
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL - BLOCK - Authentication Transfer](Documentation/IAC%20-%20GLOBAL%20-%20BLOCK%20-%20Authentication%20Transfer/IAC%20-%20GLOBAL%20-%20BLOCK%20-%20Authentication%20Transfer.png)


---


# IAC - GLOBAL - BLOCK - Unsupported Device Platforms

**State:** Enabled  
**Policy ID:** `9e21fa64-8d9a-4e62-81da-9abce8859a0c`

## Intent

Restricts access from device platforms that cannot satisfy CA grant controls — such as unmanaged Linux desktops and legacy operating systems. Reduces unmanaged device risk without impacting managed Windows, macOS, iOS, and Android endpoints.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Platforms: all (exclude: android, iOS, windows, macOS), Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 9e21fa64-8d9a-4e62-81da-9abce8859a0c
- [MEDIUM]  Broad policy with exclusions — review for gaps
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL - BLOCK - Unsupported Device Platforms](Documentation/IAC%20-%20GLOBAL%20-%20BLOCK%20-%20Unsupported%20Device%20Platforms/IAC%20-%20GLOBAL%20-%20BLOCK%20-%20Unsupported%20Device%20Platforms.png)


---


# IAC - GLOBAL - GRANT - BreakGlass - TrustedLocations

**State:** Report-only  
**Policy ID:** `1588fdc7-f34a-468e-8023-4d788ef5d226`

## Intent

Allows break-glass accounts to authenticate only from trusted network locations. Adds a location-based constraint to emergency access — even if break-glass credentials are compromised, they cannot be used from arbitrary internet locations.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: IAC - Trusted Locations (IP), Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: 1588fdc7-f34a-468e-8023-4d788ef5d226
- [HIGH]  Device Registration Service bypasses location-based conditions
- [INFO]  Policy is in report-only mode
- [MEDIUM]  Named location "IAC - Trusted Locations (IP)" is not marked as trusted
- [MEDIUM]  Break-glass group not excluded (report-only policy)


![IAC - GLOBAL - GRANT - BreakGlass - TrustedLocations](Documentation/IAC%20-%20GLOBAL%20-%20GRANT%20-%20BreakGlass%20-%20TrustedLocations/IAC%20-%20GLOBAL%20-%20GRANT%20-%20BreakGlass%20-%20TrustedLocations.png)


---


# IAC - GLOBAL - GRANT - MFA-Passkey - UserRegistration

**State:** Report-only  
**Policy ID:** `30a1edce-e832-456b-b2c5-4b1098d3a9b3`

## Intent

Requires MFA completion before users can register new security information (passkeys, authenticator app, FIDO2 keys). Prevents an attacker who has stolen a password from registering their own MFA methods. Enforces the registration process through a secure, authenticated path.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | User actions: urn:user:registerdevice |
| **Conditions** | Platforms: iOS (exclude: macOS, windows), Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: 30a1edce-e832-456b-b2c5-4b1098d3a9b3
- [INFO]  Policy is in report-only mode
- [HIGH]  Platform condition only targets iOS — user-agent spoofing risk
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL - GRANT - MFA-Passkey - UserRegistration](Documentation/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA-Passkey%20-%20UserRegistration/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA-Passkey%20-%20UserRegistration.png)


---


# IAC - GLOBAL - GRANT - MFA-Passkeys - ADM-Users

**State:** Report-only  
**Policy ID:** `a53c4c2b-b577-4d88-b64d-36b92f8f3ca0`

## Intent

Requires admin-role users to authenticate using a passkey (FIDO2 or device-bound passkey) specifically. Elevates the authentication requirement for privileged accounts beyond standard MFA — passkeys are phishing-resistant by design and cannot be intercepted or replayed.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: a53c4c2b-b577-4d88-b64d-36b92f8f3ca0
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL - GRANT - MFA-Passkeys - ADM-Users](Documentation/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA-Passkeys%20-%20ADM-Users/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA-Passkeys%20-%20ADM-Users.png)


---


# IAC - GLOBAL - SESSION - Windows - TokenProtection

**State:** Report-only  
**Policy ID:** `8bb25c6a-ed35-4556-bed4-b3aaa14e192b`

## Intent

Cryptographically binds access tokens to the specific Windows device that authenticated, preventing token replay attacks even if a token is exfiltrated from memory or disk. Requires Entra ID P2. Scoped to Windows Entra-joined and Hybrid Entra-joined devices only.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | Office 365 Exchange Online, Office 365 SharePoint Online, Windows 365, Azure Virtual Desktop, Microsoft Teams Services |
| **Conditions** | Platforms: windows, Client apps: mobileAppsAndDesktopClients, Device filter: device.systemLabels -contains "CloudPC" -and device.trustType -eq "AzureAD" |
| **Grant Controls** | — |
| **Session Controls** | — |

## Audit Findings

- ID: 8bb25c6a-ed35-4556-bed4-b3aaa14e192b
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL - SESSION - Windows - TokenProtection](Documentation/IAC%20-%20GLOBAL%20-%20SESSION%20-%20Windows%20-%20TokenProtection/IAC%20-%20GLOBAL%20-%20SESSION%20-%20Windows%20-%20TokenProtection.png)


---


# IAC - GLOBAL - BLOCK - Service Accounts

**State:** Report-only  
**Policy ID:** `99eabebd-877c-4800-aa15-d389b8767760`

## Intent

Blocks sign-in for non-interactive service accounts (members of CA-ServiceAccounts) from interactive sign-in flows. Service accounts should authenticate via managed identities, workload identities, or certificate-based flows — not through user-interactive sessions.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 1 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: IAC - Trusted Locations (IP), Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 99eabebd-877c-4800-aa15-d389b8767760
- [HIGH]  Device Registration Service bypasses location-based conditions
- [INFO]  Policy is in report-only mode
- [MEDIUM]  Named location "IAC - Trusted Locations (IP)" is not marked as trusted
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL – BLOCK – Service Accounts](Documentation/IAC%20-%20GLOBAL%20–%20BLOCK%20–%20Service%20Accounts/IAC%20-%20GLOBAL%20–%20BLOCK%20–%20Service%20Accounts.png)


---


# IAC - GLOBAL - SESSION - Admin Persistence (4 Hours)

**State:** Enabled  
**Policy ID:** `04b969aa-3e98-4e0f-8b32-2319b199b56a`

## Intent

Sets a 4-hour sign-in frequency for all admin-role users. After 4 hours of inactivity, admins must re-authenticate. Limits the window an attacker has to abuse a stolen admin session token. Non-persistent browser sessions enforced in admin contexts.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 11 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: browser |
| **Grant Controls** | — |
| **Session Controls** | Sign-in frequency: 4 hours, Persistent browser: never |

## Audit Findings

- ID: 04b969aa-3e98-4e0f-8b32-2319b199b56a
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL – SESSION – Admin Persistence (4 Hours)](Documentation/IAC%20-%20GLOBAL%20–%20SESSION%20–%20Admin%20Persistence%20(4%20Hours)/IAC%20-%20GLOBAL%20–%20SESSION%20–%20Admin%20Persistence%20(4%20Hours).png)


---


# IAC - GLOBAL - SESSION - All Users Persistence (9-12 Hours)

**State:** Report-only  
**Policy ID:** `ea9459a9-91b6-4d2b-b929-03781ac81d54`

## Intent

Sets sign-in frequency to 9-12 hours for all licensed internal users. Balances security (limits session token lifetime) with usability (avoids excessive re-authentication friction during a working day). Non-persistent browser sessions for unmanaged devices.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: browser |
| **Grant Controls** | — |
| **Session Controls** | Sign-in frequency: 12 hours, Persistent browser: never |

## Audit Findings

- ID: ea9459a9-91b6-4d2b-b929-03781ac81d54
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - GLOBAL – SESSION – All Users Persistence (9-12 Hours)](Documentation/IAC%20-%20GLOBAL%20–%20SESSION%20–%20All%20Users%20Persistence%20(9-12%20Hours)/IAC%20-%20GLOBAL%20–%20SESSION%20–%20All%20Users%20Persistence%20(9-12%20Hours).png)


---


# IAC - APP - BLOCK - SharePoint-OneDrive-NonTrustedLocations

**State:** Report-only  
**Policy ID:** `1f960ec9-885f-4032-a6b2-a5c559279274`

## Intent

Blocks access to SharePoint Online and OneDrive from network locations not listed in the Inforcer Trusted Locations named location. Protects sensitive collaboration content from being accessed from untrusted or unknown networks.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (4 exclusions) |
| **Cloud Apps** | Office 365 SharePoint Online |
| **Conditions** | Locations: All locations, Exclude locations: All trusted locations, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 1f960ec9-885f-4032-a6b2-a5c559279274
- [INFO]  Policy is in report-only mode
- [HIGH]  Policy uses "All trusted locations" but 5 location(s) are NOT trusted
- [INFO]  Break-glass group excluded ✓


![IAC - APP - BLOCK - SharePoint-OneDrive-NonTrustedLocations](Documentation/IAC%20-%20APP%20-%20BLOCK%20-%20SharePoint-OneDrive-NonTrustedLocations/IAC%20-%20APP%20-%20BLOCK%20-%20SharePoint-OneDrive-NonTrustedLocations.png)


---


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


![IAC - APP - inforcer - RequireMFA](Documentation/IAC%20-%20APP%20-%20inforcer%20-%20RequireMFA/IAC%20-%20APP%20-%20inforcer%20-%20RequireMFA.png)


---


# IAC - APP - BLOCK - AVD - Exclude - AllowedAVDUsers

**State:** Report-only  
**Policy ID:** `9bc2ad69-4aed-4242-807d-788446196b8b`

## Intent

Blocks access to Azure Virtual Desktop for users not in the AllowedAVDUsers group. AVD is a high-privilege remote access surface — access should be explicitly granted to a defined set of users rather than open to all.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (4 exclusions) |
| **Cloud Apps** | Windows 365, Azure Virtual Desktop |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 9bc2ad69-4aed-4242-807d-788446196b8b
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - APP – BLOCK – AVD - Exclude - AllowedAVDUsers](Documentation/IAC%20-%20APP%20–%20BLOCK%20–%20AVD%20-%20Exclude%20-%20AllowedAVDUsers/IAC%20-%20APP%20–%20BLOCK%20–%20AVD%20-%20Exclude%20-%20AllowedAVDUsers.png)


---


# IAC - APP - BLOCK - AVD - NonTrustedLocations

**State:** Report-only  
**Policy ID:** `b13dd393-f644-45c8-81bf-aa7f4032ebd3`

## Intent

Blocks AVD access from non-trusted network locations even for authorized AVD users. Combines identity-based (group membership) and network-based (location) controls for Azure Virtual Desktop access.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | Windows 365, Azure Virtual Desktop |
| **Conditions** | Locations: All locations, Exclude locations: All trusted locations, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: b13dd393-f644-45c8-81bf-aa7f4032ebd3
- [INFO]  Policy is in report-only mode
- [HIGH]  Policy uses "All trusted locations" but 5 location(s) are NOT trusted
- [INFO]  Break-glass group excluded ✓


![IAC - APP – BLOCK – AVD - NonTrustedLocations](Documentation/IAC%20-%20APP%20–%20BLOCK%20–%20AVD%20-%20NonTrustedLocations/IAC%20-%20APP%20–%20BLOCK%20–%20AVD%20-%20NonTrustedLocations.png)


---


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


![IAC - AGENT - BLOCK - HighRiskAgent](Documentation/IAC%20-%20AGENT%20-%20BLOCK%20-%20HighRiskAgent/IAC%20-%20AGENT%20-%20BLOCK%20-%20HighRiskAgent.png)


---


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


![IAC - AGENT - BLOCK - NonTrustedAgents](Documentation/IAC%20-%20AGENT%20-%20BLOCK%20-%20NonTrustedAgents/IAC%20-%20AGENT%20-%20BLOCK%20-%20NonTrustedAgents.png)


---


# IAC - INTUNE - GRANT - RequireCompliantDevice

**State:** Report-only  
**Policy ID:** `660ab461-0de5-4b00-baea-ec7325280f60`

## Intent

Requires devices to be marked as compliant in Microsoft Intune before accessing corporate resources. Compliant devices must meet all configured compliance policies (encryption, OS version, antivirus, etc.). Enforces that only managed, healthy devices get access.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: All trusted locations, Client apps: all |
| **Grant Controls** | 📱 Require compliant device OR 💻 Require hybrid Azure AD joined |
| **Session Controls** | — |

## Audit Findings

- ID: 660ab461-0de5-4b00-baea-ec7325280f60
- [HIGH]  Grant controls use "OR" — weakest control is effective
- [HIGH]  Device Registration Service bypasses location-based conditions and compliant/hybrid-joined device requirement
- [MEDIUM]  Policy does not require MFA
- [INFO]  Policy is in report-only mode
- [HIGH]  Policy uses "All trusted locations" but 5 location(s) are NOT trusted


![IAC - INTUNE - GRANT - RequireCompliantDevice](Documentation/IAC%20-%20INTUNE%20-%20GRANT%20-%20RequireCompliantDevice/IAC%20-%20INTUNE%20-%20GRANT%20-%20RequireCompliantDevice.png)


---


# IAC - INTUNE - GRANT - Device Registration from trusted location

**State:** Report-only  
**Policy ID:** `aeb49474-5250-4b65-8b0a-56c47127ee0f`

## Intent

Requires devices to be registered with Entra ID (Intune enrollment) only from trusted network locations. Prevents device registration from unknown or untrusted networks, reducing the risk of attacker-controlled devices being enrolled in the tenant.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | User actions: urn:user:registerdevice |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Multifactor authentication |
| **Session Controls** | — |

## Audit Findings

- ID: aeb49474-5250-4b65-8b0a-56c47127ee0f
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - INTUNE – GRANT – Device Registration from trusted location](Documentation/IAC%20-%20INTUNE%20–%20GRANT%20–%20Device%20Registration%20from%20trusted%20location/IAC%20-%20INTUNE%20–%20GRANT%20–%20Device%20Registration%20from%20trusted%20location.png)


---


# IAC - ZTCA - GLOBAL - BLOCK - Admin Portal

**State:** Report-only  
**Policy ID:** `fafaa50c-0b61-4ac6-a589-f9a1120b2f9e`

## Intent

Blocks access to Microsoft admin portals (Azure Portal, Entra Admin Center, Intune, Purview, M365 Admin, Defender) for non-admin users. Prevents accidental or unauthorized access to admin interfaces from standard user accounts.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (3 exclusions) |
| **Cloud Apps** | Inforcer Integration, Azure Resource Manager, MicrosoftAdminPortals, Microsoft Purview Platform, My Staff |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: fafaa50c-0b61-4ac6-a589-f9a1120b2f9e
- [HIGH]  4 app(s) excluded from this policy (1 high-risk)
- [INFO]  Policy is in report-only mode
- [LOW]  1 guest/external user type(s) excluded
- [INFO]  Break-glass group excluded ✓


![IAC - ZTCA - GLOBAL – BLOCK – Admin Portal](Documentation/IAC%20-%20ZTCA%20-%20GLOBAL%20–%20BLOCK%20–%20Admin%20Portal/IAC%20-%20ZTCA%20-%20GLOBAL%20–%20BLOCK%20–%20Admin%20Portal.png)


---


# IAC - ZTCA - INTUNE - BLOCK - AllApps - ExcludeTrustedLocation

**State:** Report-only  
**Policy ID:** `2dd84b12-7900-40f0-b192-027c20aaa83f`

## Intent

Zero Trust CA policy that blocks all app access from devices that are not Intune-compliant, excluding trusted locations. Enforces device compliance as a condition for all resource access in a Zero Trust Architecture posture.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (2 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Locations: All locations, Exclude locations: All trusted locations, Client apps: all, Device filter: device.isCompliant -eq True -or device.trustType -eq "ServerAD" -or device.trustType -eq "Workplace" |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 2dd84b12-7900-40f0-b192-027c20aaa83f
- [HIGH]  Device Registration Service bypasses location-based conditions
- [INFO]  Policy is in report-only mode
- [HIGH]  Policy uses "All trusted locations" but 5 location(s) are NOT trusted
- [MEDIUM]  1 guest/external user type(s) excluded
- [INFO]  Break-glass group excluded ✓


![IAC - ZTCA - INTUNE - BLOCK - AllApps - ExcludeTrustedLocation](Documentation/IAC%20-%20ZTCA%20-%20INTUNE%20-%20BLOCK%20-%20AllApps%20-%20ExcludeTrustedLocation/IAC%20-%20ZTCA%20-%20INTUNE%20-%20BLOCK%20-%20AllApps%20-%20ExcludeTrustedLocation.png)


---


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


![IAC- ZTCA - GLOBAL - BLOCK - AllApps -Exclude CA-Global](Documentation/IAC-%20ZTCA%20-%20GLOBAL%20-%20BLOCK%20-%20AllApps%20-Exclude%20CA-Global/IAC-%20ZTCA%20-%20GLOBAL%20-%20BLOCK%20-%20AllApps%20-Exclude%20CA-Global.png)


---


# IAC - APP - SESSION - O365 - Timeoutsettings

**State:** Report-only  
**Policy ID:** `c5133041-079f-45ec-b27a-20268546077f`

## Intent

Applies session timeout controls to Office 365 applications. Configures sign-in frequency and browser session persistence settings for Exchange, Teams, SharePoint, and other O365 workloads to reduce the risk of abandoned authenticated sessions.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | Office365 |
| **Conditions** | Platforms: all (exclude: android, iOS, macOS, linux), Client apps: browser, Device filter: device.isCompliant -eq True -and device.trustType -eq "ServerAD" |
| **Grant Controls** | — |
| **Session Controls** | — |

## Audit Findings

- ID: c5133041-079f-45ec-b27a-20268546077f
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - APP - SESSION - O365 - Timeoutsettings](Documentation/IAC%20-%20APP%20-%20SESSION%20-%20O365%20-%20Timeoutsettings/IAC%20-%20APP%20-%20SESSION%20-%20O365%20-%20Timeoutsettings.png)


---


# IAC - P2 - GLOBAL - GRANT - High-Risk Sign-Ins

**State:** Report-only  
**Policy ID:** `53a8df0b-4658-4835-ace2-100b5d287aac`

## Intent

Requires MFA re-authentication and password change for sign-ins Entra Identity Protection assesses as high-risk. High-risk indicators include impossible travel, threat intelligence matches, and anomalous token characteristics. Requires Entra ID P2.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Sign-in risk: high, Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | Sign-in frequency: null null |

## Audit Findings

- ID: 53a8df0b-4658-4835-ace2-100b5d287aac
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - P2 - GLOBAL - GRANT - High-Risk Sign-Ins](Documentation/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20High-Risk%20Sign-Ins/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20High-Risk%20Sign-Ins.png)


---


# IAC - P2 - GLOBAL - GRANT - Medium-Risk Sign-Ins

**State:** Report-only  
**Policy ID:** `180ab5a3-d3ae-4457-9ef1-e3c06f5dfbfc`

## Intent

Requires MFA for sign-ins assessed as medium-risk by Entra Identity Protection. Medium-risk indicators include unfamiliar sign-in properties and atypical travel. Softer response than high-risk — MFA without forced password change. Requires Entra ID P2.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Sign-in risk: medium, Client apps: all |
| **Grant Controls** | ✅ Require MFA |
| **Session Controls** | — |

## Audit Findings

- ID: 180ab5a3-d3ae-4457-9ef1-e3c06f5dfbfc
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - P2 - GLOBAL - GRANT - Medium-Risk Sign-Ins](Documentation/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20Medium-Risk%20Sign-Ins/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20Medium-Risk%20Sign-Ins.png)


---


# IAC - P2 - GLOBAL - BLOCK - RiskyUsers - RegisterSecurityInfo

**State:** Report-only  
**Policy ID:** `768858bd-a5ad-47de-8acb-5e815cde0857`

## Intent

Blocks high-risk and medium-risk users from registering new security information (MFA methods, passkeys). Prevents an attacker who has compromised a risky account from registering their own authentication methods to maintain persistent access. Requires Entra ID P2.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | User actions: urn:user:registersecurityinfo |
| **Conditions** | User risk: high, medium, Client apps: all |
| **Grant Controls** | 🚫 Block access |
| **Session Controls** | — |

## Audit Findings

- ID: 768858bd-a5ad-47de-8acb-5e815cde0857
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - P2 - GLOBAL - BLOCK - RiskyUsers - RegisterSecurityInfo](Documentation/IAC%20-%20P2%20-%20GLOBAL%20-%20BLOCK%20-%20RiskyUsers%20-%20RegisterSecurityInfo/IAC%20-%20P2%20-%20GLOBAL%20-%20BLOCK%20-%20RiskyUsers%20-%20RegisterSecurityInfo.png)


---


# IAC - P2 - APP - SESSION - PIM - Reauthentication

**State:** Report-only  
**Policy ID:** `a6b3b754-9079-48f0-abb2-9e79b2f41095`

## Intent

Requires reauthentication (authentication context c1 — PIM-ReAuthentication) when accessing Privileged Identity Management to activate roles. Ensures that PIM role activations always trigger a fresh authentication challenge, preventing session reuse for privilege escalation.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users (1 exclusions) |
| **Cloud Apps** | — |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | Sign-in frequency: null null |

## Audit Findings

- ID: a6b3b754-9079-48f0-abb2-9e79b2f41095
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓


![IAC - P2 - APP - SESSION - PIM - Reauthentication](Documentation/IAC%20-%20P2%20-%20APP%20-%20SESSION%20-%20PIM%20-%20Reauthentication/IAC%20-%20P2%20-%20APP%20-%20SESSION%20-%20PIM%20-%20Reauthentication.png)


---


# IAC - GLOBAL - GRANT - MFA - B2B-Guest

**State:** Report-only  
**Policy ID:** `f25f94e0-98b6-41be-b9d6-68cb781004a4`

## Intent

Requires MFA for external B2B collaboration users (formal partner/guest accounts with a home tenant). Separate from the mixed-guest policy to allow different authentication strength requirements for formal B2B relationships vs ad hoc guests.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 0 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | 🛡️ Auth strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: f25f94e0-98b6-41be-b9d6-68cb781004a4
- [INFO]  Policy is in report-only mode
- [MEDIUM]  Guest users required to satisfy Authentication strength: Modern MFA + TAP — may need Cross-Tenant Access Settings


![IAC - GLOBAL - GRANT - MFA - B2B-Guest](Documentation/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20B2B-Guest/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20B2B-Guest.png)


---


# IAC - GLOBAL - GRANT - MFA - Mixed-Guests

**State:** Report-only  
**Policy ID:** `e0fabad3-bd0f-42e4-a901-51ef7ab8889c`

## Intent

Requires MFA for all guest users including ad hoc guests without a formal home tenant relationship. Catches guests that don't qualify as B2B collaboration users and ensures all external identities must complete MFA before accessing resources.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | 0 specific user/group/role targets |
| **Cloud Apps** | All cloud apps |
| **Conditions** | Client apps: all |
| **Grant Controls** | ✅ Require MFA |
| **Session Controls** | — |

## Audit Findings

- ID: e0fabad3-bd0f-42e4-a901-51ef7ab8889c
- [INFO]  Policy is in report-only mode
- [HIGH]  Guest users required to satisfy MFA — may need Cross-Tenant Access Settings


![IAC - GLOBAL - GRANT - MFA - Mixed-Guests](Documentation/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20Mixed-Guests/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20Mixed-Guests.png)


---

# IAC - GLOBAL - GRANT - MFA - WindowsAzureAD-BaselineScopes

**State:** Report-only  
**Policy ID:** `ab659968-2e8a-4448-9710-d930aada3499`  
**Created:** 2026-08-28

## Intent

Closes the **directory baseline scope gap** created by the March 2026 Microsoft enforcement change. When any "All resources" CA policy has resource exclusions, low-privilege directory scopes (`User.Read`, `openid`, `profile`, `email`, `offline_access`, `People.Read`) were previously exempt from enforcement. Microsoft has changed this — those scopes are now mapped to the **Windows Azure Active Directory** resource (`00000002-0000-0000-c000-000000000000`) as the enforcement audience.

This policy directly targets that resource, ensuring all token requests to Azure AD Graph directory scopes meet the same MFA requirement as the rest of the baseline — even when other "All resources" policies contain exclusions.

> **Microsoft documentation:** *"If the recommended baseline MFA policy without resource exclusions can't be configured because of business reasons, create a separate Conditional Access policy targeting Windows Azure Active Directory (00000002-0000-0000-c000-000000000000)."*  
> 📖 [Conditional Access: Target resources — Protect directory information](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps#protect-directory-information)

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users |
| **Excluded Users** | Break-glass group (`5628ad67-f9d1-4495-abe3-99dc8f9074f1`) |
| **Cloud Apps** | Windows Azure Active Directory (`00000002-0000-0000-c000-000000000000`) |
| **Conditions** | Client apps: all |
| **Grant Controls** | ✅ Require authentication strength: Modern MFA + TAP |
| **Session Controls** | — |

## Audit Findings

- ID: ab659968-2e8a-4448-9710-d930aada3499
- [INFO]  Policy is in report-only mode
- [INFO]  Break-glass group excluded ✓
- [INFO]  Closes Azure AD Graph directory scope gap for tenants with resource exclusions in All resources policies

![IAC - GLOBAL - GRANT - MFA - WindowsAzureAD-BaselineScopes](Documentation/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20WindowsAzureAD-BaselineScopes/IAC%20-%20GLOBAL%20-%20GRANT%20-%20MFA%20-%20WindowsAzureAD-BaselineScopes.png)


---

# IAC - P2 - GLOBAL - GRANT - High-Risk Users - Risk Remediation

**State:** Enabled  
**Policy ID:** `544cd9ef-5e37-4568-9ad8-b8e151be1814`  
**License Requirement:** Entra ID P2

## Intent

Forces high-risk users (standard population) through risk remediation — a secure password change via SSPR — combined with phishing-resistant authentication and every-time re-authentication. Closes the compromise window when Entra Identity Protection flags a user as high-risk.

The EAM group is excluded and handled by a companion policy using built-in MFA instead of an auth strength object.

> 📖 [Require password change for high-risk users](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-risk-based-user)  
> 📖 [Risk-based CA policy best practices](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies)

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users |
| **Excluded Groups** | Break-glass (`5628ad67`), EAM group (`8d0564e5`) |
| **Cloud Apps** | All resources |
| **Conditions** | User risk: High, Client apps: all |
| **Grant Controls** | ✅ Auth strength: Modern MFA + TAP AND 🔑 Risk remediation |
| **Grant Operator** | AND |
| **Session Controls** | Sign-in frequency: Every time |

## Audit Findings

- ID: 544cd9ef-5e37-4568-9ad8-b8e151be1814
- [INFO]  Break-glass group excluded ✓
- [INFO]  EAM group excluded — covered by companion EAM policy

![IAC - P2 - GLOBAL - GRANT - High-Risk Users - Risk Remediation](Documentation/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20High-Risk%20Users%20-%20Risk%20Remediation/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20High-Risk%20Users%20-%20Risk%20Remediation.png)


---

# IAC - P2 - GLOBAL - GRANT - EAM - High-Risk Users - Risk Remediation

**State:** Enabled  
**Policy ID:** `bb6a814e-808a-467c-9475-06f89140ce99`  
**License Requirement:** Entra ID P2

## Intent

Companion to the standard high-risk risk-remediation policy. Targets users enrolled in External Authentication Methods (EAM) who cannot satisfy a custom authentication strength object. Uses built-in MFA + risk remediation with every-time sign-in frequency.

> 📖 [Require password change for high-risk users](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-risk-based-user)  
> 📖 [External authentication methods](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-external-method-manage)

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | EAM group only (`8d0564e5-ab28-4283-9a94-9883c581adde`) |
| **Excluded Groups** | Break-glass (`5628ad67`), Additional exclusion (`b63c3682`) |
| **Cloud Apps** | All resources |
| **Conditions** | User risk: High, Client apps: all |
| **Grant Controls** | ✅ Require MFA AND 🔑 Risk remediation |
| **Grant Operator** | AND |
| **Session Controls** | Sign-in frequency: Every time |

## Audit Findings

- ID: bb6a814e-808a-467c-9475-06f89140ce99
- [INFO]  Break-glass group excluded ✓
- [INFO]  Companion to IAC - P2 - GLOBAL - GRANT - High-Risk Users - Risk Remediation

![IAC - P2 - GLOBAL - GRANT - EAM - High-Risk Users - Risk Remediation](Documentation/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20EAM%20-%20High-Risk%20Users%20-%20Risk%20Remediation/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20EAM%20-%20High-Risk%20Users%20-%20Risk%20Remediation.png)


---


# IAC - P2 - GLOBAL - GRANT - Medium-Risk Users - Risk Remediation

**State:** Report-only  
**License Requirement:** Entra ID P2

## Intent

Requires authentication strength and risk remediation for users flagged as medium-risk by Entra Identity Protection. Replaces the legacy `passwordChange` pattern — risk remediation supports both password-based and passwordless (FIDO2, Windows Hello for Business) users.

> 📖 [Configure risk policies](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies)  
> 📖 [Require risk remediation (preview)](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-policies#require-risk-remediation-with-microsoft-managed-remediation-preview)

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users |
| **Excluded Groups** | Break-glass (`5628ad67`), EAM users (`b63c3682`) |
| **Cloud Apps** | All resources |
| **Conditions** | User risk: Medium, Client apps: all |
| **Grant Controls** | 🔐 Authentication strength (Modern MFA + TAP) AND 🔑 Risk remediation |
| **Grant Operator** | AND |
| **Session Controls** | — |

## Audit Findings

- [INFO]  Break-glass group excluded ✓
- [MEDIUM]  All guest/external user type(s) excluded
- [INFO]  EAM users excluded — companion EAM policy required for this user population

![IAC - P2 - GLOBAL - GRANT - Medium-Risk Users - Risk Remediation](Documentation/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20Medium-Risk%20Users%20-%20Risk%20Remediation/IAC%20-%20P2%20-%20GLOBAL%20-%20GRANT%20-%20Medium-Risk%20Users%20-%20Risk%20Remediation.png)


---

