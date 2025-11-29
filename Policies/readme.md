# Policy Change Document

## **GLOBAL Policies**

- `ACME - GLOBAL - GRANT - MFA - All-Users`   (Exclude Microsoft Rights Management: <https://office365itpros.com/2024/02/12/conditional-access-mfa-email/>)
- `ACME - GLOBAL - GRANT - MFA - All-Admins`
- `ACME - GLOBAL - GRANT - MFA-Passkeys - ADM-Users` (Note ensure you target ModernMFA with TAP, need TAP to register passkey)
- `ACME - GLOBAL - GRANT - MFA - External-Guest-Users`
- `ACME - GLOBAL - GRANT - RegisterSecurityInfoRequirements` (There are two options here. This is the lesser requiring MFA from anywhere but excluding trusted location)
- `ACME - GLOBAL - GRANT - ACME - Terms of Use`(Needed policy to create)
- `ACME - GLOBAL - GRANT  - Breakglass - TrustedLocations` (Breakglass policy for TOTP Account) This would be created with seperate accounts from your org if you use this method
- `ACME - GLOBAL - GRANT - MFA-Passkey - UserRegistration`
- `ACME - GLOBAL - BLOCK - DeviceCodeAuthFlow`
- `ACME - GLOBAL - BLOCK - Authentication Transfer`
- `ACME - GLOBAL - BLOCK - UnsupportedDevicePlatforms`
- `ACME - GLOBAL - BLOCK - Countries-NotAllowed`(Uses ACME-TrustedCountries) Remember to create the Trusted Country list for your use case
- `ACME - GLOBAL - BLOCK - Countries-NotAllowed-NoExclusions`(Uses ACME-BlockedCountries) Remember to create the BlockedCountry for full list of Countries to block no matter exclusions
- `ACME - GLOBAL - BLOCK - ServiceAccounts`
- `ACME - GLOBAL - BLOCK - LegacyAuthentication`
- `ACME - GLOBAL - BLOCK - RegisterSecurityInfoRequirements - ExludeTrustedLocation` (This policy blocks registration from anywhere but a trusted location)
- `ACME - GLOBAL - SESSION - AllUserPersistence-9-12Hours`
- `ACME - GLOBAL - SESSION - AdminPersistence-1Hour`
- `ACME - WORKLOAD - BLOCK - EntraConnectIDSync - ExcludeEntraConnectIP` (https://github.com/Cloud-Architekt/AzureAD-Attack-Defense/blob/main/EntraSyncAba.md/Requires 1 EntraIDPremium License)

---
## **APP Specific Policy**

- `ACME - APP - BLOCK - AVD-NonTrustedLocations`
- `ACME - APP - BLOCK - AVD - Exclude-AllowedAVDUsers`
- `ACME - APP - BLOCK - SharePoint-OneDrive-NonTrustedLocations`
- `ACME - APP - BLOCK - AVDUsers`
- `ACME - APP - BLOCK - Copilot`
- `ACME - APP - BLOCK - AzureDevOps`
- `ACME - APP - GRANT - MFA - AVDUsers` Failsafe policy in case users get through they have to provide MFA.



## **INTUNE Policies**

- `ACME - INTUNE  - GRANT - DeviceRegistration-TrustedLocation`
- `ACME - INTUNE  - GRANT - MobileApps-DesktopClients`
- `ACME - INTUNE  - SESSION - BYOD-Persistence`
- `ACME - INTUNE  - SESSION - BlockFileDownloads-UnmanagedDevices`
- `ACME - INTUNE  - GRANT - MobileDeviceAccessRequirements`
- `ACME - INTUNE - BLOCK- RequireCompliantDevice-NonTrustedLocations`
- `ACME - INTUNE - GRANT - RequireCompliantDevice`

---

## **P2 Policies**

- `ACME - P2 - GLOBAL - GRANT - HighRiskSignIns` (Require strong authentication)
- `ACME - P2 - GLOBAL - GRANT- HighRiskUsers`  (Require Password Reset)
- `ACME - P2 - GLOBAL - GRANT - MediumRiskSignIns`
- `ACME - P2 - GLOBAL - GRANT - MediumRiskUsers`
- `ACME - P2 - GLOBAL - BLOCK - RiskyUsers - RegisterSecurityInfoRequirements`
- `ACME - P2 - APP - SESSION - PIM - Reauthentication` https://www.welkasworld.com/post/conditional-access-essentials-authentication-contexts-secure-pim-resource-access#viewer-qpn0z109989

---

## **ZTCA Policies**

- `ACME - ZTCA - BLOCK - AdminPortal` (See notes below, some Enterprise apps may not be present and the policy may fail to be created via Inforcer)
- `ACME - ZTCA - GLOBAL - BLOCK - AllApps - Exclude-CA-Global`
- `ACME - ZTCA - INTUNE - BLOCK - AllApps - Exclude-TrustedLocation`

## **AGENT Policies**

- `ACME - AGENT - BLOCK - HighRiskAgents`
- `ACME - AGENT - BLOCK - NonTrustedAgents` (Security Attribute = AgentApproved)
