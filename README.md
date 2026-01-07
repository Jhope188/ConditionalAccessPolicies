# ConditionalAccessPolicies
Defense in Depth CA Policies
- <https://youtu.be/RA4BYQjLAAU?si=pSz4zeTOGYJf3iP3>

##Conditional Access Baseline 


## Conditional Access (ACME) Policy Naming Documentation

**Helpful Policy Links**
* <https://github.com/kennethvs/cabaseline202510/tree/main>
* <https://www.vansurksum.com/2025/10/12/configuring-conditional-access-for-guest-users-allowing-only-office-365-and-essential-apps/>
* <https://www.vansurksum.com/2020/06/26/limit-access-to-outlook-web-access-and-sharepoint-online-and-onedrive-using-conditional-access-app-enforced-restrictions/>
* <https://danielchronlund.com/2020/11/09/dctoolbox-powershell-module-for-microsoft-365-security-conditional-access-automation-and-more/>


ACME - [Scope] - [Control Type] - [Target] - [Descriptor/Notes]

- **Scope**: GLOBAL, APP, INTUNE, P2, ZTCA, AGENT, WORKLOAD, etc.
- **Control Type**: BLOCK, GRANT, SESSION.
- **Target**: Describes target of the policy (e.g., MFA, Device Code Auth Flow, Legacy Authentication).
- **Additional Descriptor/Notes**: Further description or exception details and Exclusions if requred


### Prefix
- **ACME** → Identifies this as a Customer Tenant CA policy and or deployed from Inforcer as an ACME Standard Policy

### Scope

- **GLOBAL** → Applies to all clients and all applications in the tenant.
- **APP** → Specific to one enterprise application or client.
- **INTUNE** → Applies to Intune-managed devices or mobile/desktop management.
- **P2** → Policies tied to Microsoft Entra ID Premium P2 features (e.g., risk-based CA).
- **ZTCA** → Zero Trust Conditional Access policies.
- **Workload** → Service Principal policy scope to secure Enterprise Apps.
- **AGENT** → Applies to Microsoft Entra **Agent Identities**, including cloud sync agents, connectors, workload agents, token protection agents, and other non-human agent identity objects listed under Entra ID → *Agent ID*.


### Control Type
- **BLOCK** → Prevents access entirely.(Typical of Least privelage policy and has an Excluded group that is explicitly allowed access)
- **GRANT** → Allows access but with conditions (e.g., MFA, compliant device).
- **SESSION** → Configures session-level restrictions (e.g., persistence, sign-in frequency).

### Target
- Describes **what** is being affected.
- **Examples**:  
  - `MFA`
  - `DeviceCodeAuthFlow`
  - `LegacyAuthentication`
  - `SignIn`
  - `SharePoint-OneDrive`
  - `AVDUsers`
  - `Countries`
  - `Breakglass`
  - `Service Accounts`
  - `APPS: Inforcer/DevOps/Copilot`
  - `Terms Of Use` 

  ### Descriptor / Notes
- Used for **exceptions, exclusions, or extra detail**.
- Always use `Exclude-` when naming a policy with explicit exclusions.
- **Examples**:  
  - `Exclude-TrustedEntraSyncIPs`
  - `Exclude-AVD-ExternalUsers`
  - `NonTrustedLocations`



### ACME - GLOBAL - GRANT - MFA - External-Guest-Users
- Applies to all apps/clients.
- Grants access only if MFA is satisfied.
- Targets external and guest users.

### ACME - APP - BLOCK - AzureDevOps(Or other Apps)
- Applies to Azure DevOps enterprise app only.
- Blocks access for all unless explicitly excluded.

### ACME - APP - BLOCK - AVD - Exclude-AllowedAVDUsers

- Applies to select Ent App/clients.
- Blocks AVD access except for `AllowedAVDUsers` group.(Typically this is AVDUsers/AVD-ExternalUsers)


## 4. Best Practices

1. **Keep it concise but descriptive** — each segment should quickly tell an admin *what the policy does* without opening it.
2. **Hyphenate multi-word segments** — improves sorting and readability (`NonTrustedLocations` instead of `Non Trusted Locations`).
3. **Always include exclusion descriptor** — never leave exceptions hidden only in the policy config.
4. **Use consistent casing** — TitleCase or CamelCase for clarity.

---

## **GLOBAL Policies**

- `ACME - GLOBAL - GRANT - MFA - All-Users`   (Exclude Microsoft Rights Management: <https://office365itpros.com/2024/02/12/conditional-access-mfa-email/>)
- `ACME - GLOBAL - GRANT - MFA - All-Admins`
- `ACME - GLOBAL - GRANT - MFA-Passkeys - ADM-Users` (Note ensure you target ModernMFA with TAP, need TAP to register passkey)
- `ACME - GLOBAL - GRANT - MFA - External-Guest-Users`
- `ACME - GLOBAL - GRANT - RegisterSecurityInfoRequirements` (There are two options here. This is the lesser requiring MFA from anywhere but excluding trusted location)
- `ACME - GLOBAL - GRANT - ACME - Terms of Use`(Needed policy to create)
- `ACME - GLOBAL - GRANT  - Breakglass - TrustedLocations` (Breakglass policy for TOTP Account)
- `ACME - GLOBAL - GRANT - MFA-Passkey - UserRegistration`
- `ACME - GLOBAL - BLOCK - DeviceCodeAuthFlow`
- `ACME - GLOBAL - BLOCK - Authentication Transfer`
- `ACME - GLOBAL - BLOCK - UnsupportedDevicePlatforms`
- `ACME - GLOBAL - BLOCK - Countries-NotAllowed`(Uses ACME-TrustedCountries)
- `ACME - GLOBAL - BLOCK - Countries-NotAllowed-NoExclusions`(Uses ACME-BlockedCountries)
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
  

  




### ACME - GLOBAL - GRANT - MFA-Passkeys - ADM-Users

- **Scope:** GLOBAL (All Applications)
- **Control Type:** GRANT
- **Authentication Requirement:** MFA using Passkeys (FIDO2)
- **Target Group:** `ACME-ADM-Users-Dynamic`
- **Purpose:** Enforces passkey-based MFA for all ADM accounts across all applications.
- **Exclusions:** None by default, but may use `ACME-Passkey-ADM-User-Exclusions` if exceptions are required.

### ACME - GLOBAL - GRANT - MFA - External-Guest-Users

- **Scope:** GLOBAL (All Applications)
- **Control Type:** GRANT
- **Authentication Requirement:** MFA
- **Target Group:** All External and Guest Users
- **Purpose:** Enforces MFA for all external collaborators and guest accounts accessing resources in the tenant.
- **Exclusion Group:** None by default, but can be paired with `ACME-External-Guest-User-Exclusions` if exceptions are required.




## **APP Specific Policies**

- `ACME - APP - BLOCK - AVD-NonTrustedLocations`
  - **Scope:** APP (AVD)
  - **Control Type:** BLOCK
  - **Target:** Non-trusted location sign-ins for Azure Virtual Desktop.
  - **Purpose:** Prevents AVD access from locations not marked as trusted.

- `ACME - APP - BLOCK - AVD - Exclude-AllowedAVDUsers`
  - **Scope:** APP (AVD)
  - **Control Type:** BLOCK
  - **Target:** Non-trusted location sign-ins for AVD, excluding `AVDUsers and AVD-ExternalUsers`.
  - **Purpose:** Applies stricter location restrictions to AVD but allows access for approved external users.

- `ACME - APP - BLOCK - SharePoint-OneDrive-NonTrustedLocations`
  - **Scope:** APP (SharePoint / OneDrive)
  - **Control Type:** BLOCK
  - **Target:** SharePoint and OneDrive sign-ins from non-trusted locations.
  - **Purpose:** Prevents data access from locations not designated as trusted.

- `ACME - APP - BLOCK - AVDUsers`
  - **Scope:** APP (AVD)
  - **Control Type:** BLOCK
  - **Target:** All AVD users.
  - **Purpose:** Restricts AVD access entirely for targeted user groups.

- `ACME - APP - BLOCK - Copilot`
  - **Scope:** APP (Microsoft Copilot)
  - **Control Type:** BLOCK
  - **Target:** All users unless explicitly excluded.
  - **Purpose:** Prevents access to Microsoft Copilot enterprise app.

- `ACME - APP - BLOCK - AzureDevOps`
  - **Scope:** APP (Azure DevOps)
  - **Control Type:** BLOCK
  - **Target:** All users unless explicitly excluded.
  - **Purpose:** Prevents access to Azure DevOps enterprise app unless targeted by an approved group (e.g., `ACME-Azure-DevOps`).

```
Connect-MgGraph -Scopes "Application.ReadWrite.All"
$ServicePrincipalID=@{
“AppId” = “499b84ac-1321-427f-aa17-267ca6975798” #AzureDevOps
}
New-MgServicePrincipal -BodyParameter $ServicePrincipalId | Format-List id, DisplayName, AppId, SignInAudience

#Update your policies to include "Azure DevOps"
# → App ID: 499b84ac-1321-427f-aa17-267ca6975798

Azure Credential Configuration Endpoint Service(Allow Passkeys: https://nathanmcnulty.com/blog/2025/09/improving-passkey-registration-experiences/ )
# → App ID: ea890292-c8c8-4433-b5ea-b09d0668e1a6

Connect-MgGraph -Scopes "Application.ReadWrite.All"
$ServicePrincipalID=@{
“AppId” = “d4ebce55-015a-49b5-a083-c84d1797ae8c” #MicrosoftIntuneEnrollment
}
New-MgServicePrincipal -BodyParameter $ServicePrincipalId | Format-List id, DisplayName, AppId, SignInAudience


$ServicePrincipalID=@{
“AppId” = “44660504c-45b3-4674-a709-71951a6b0763” #Microsoft Invitation Acceptance Portal 
}
New-MgServicePrincipal -BodyParameter $ServicePrincipalId | Format-List id, DisplayName, AppId, SignInAudienc


$ServicePrincipalID=@{
“AppId” = “44660504c-45b3-4674-a709-71951a6b0763” #Microsoft Invitation Acceptance Portal 
}
New-MgServicePrincipal -BodyParameter $ServicePrincipalId | Format-List id, DisplayName, AppId, SignInAudienc

New-MgServicePrincipal -BodyParameter @{ AppId = "44660504c-45b3-4674-a709-71951a6b0763" }

$appId = "44660504c-45b3-4674-a709-71951a6b0763"
$sp = Get-MgServicePrincipal -AppId $appId -ErrorAction SilentlyContinue

if (-not $sp) {
    New-MgServicePrincipal -AppId $appId
} else {
    Write-Host "Service principal already exists: $($sp.DisplayName)"
}


$ServicePrincipalID=@{
“AppId” = “c2b688fe-48c0-464b-a89c-67041aa8fcb2” #MicrosoftDefenderATP MAM
}
New-MgServicePrincipal -BodyParameter $ServicePrincipalId | Format-List id, DisplayName, AppId, SignInAudience

```


### ACME - AGENT - CA - Require Token Protection for Agent Identities

- **Policy Name:** `ACME - AGENT - CA - RequireTokenProtection`
- **Scope:** AGENT
- **Target:** All Agent Identities (Entra ID → Agent ID → All Agent Identities)
- **Purpose:** Ensures all Microsoft Entra agent identities (Cloud Sync Agents, Connector Agents, Token Protection Agents, etc.) use Token Protection to mitigate token replay attacks.
- **Grant Controls:** Require Token Protection
- **Conditions:**
  - **Identity Type:** Workload / Agent Identity
  - **Client App:** All modern authentication clients
  - **Sign-in Risk:** Not required
- **Exclusions:**  
  - Break-glass agent identities (if any exist)
- **Benefits:**  
  - Enforces strong protection for all non-human agent authentications
  - Prevents compromised or replayed agent tokens from being reused

### ACME - AGENT - BLOCK - HighRiskAgents

- **Policy Name:** `ACME - AGENT - BLOCK - HighRiskAgents`
- **Scope:** AGENT
- **Target:** All Agent Identities flagged as **High Risk** in Microsoft Entra ID.
- **Purpose:** Blocks all authentication attempts from agent identities that Entra classifies as High Risk, preventing compromised agents from accessing any resource.
- **Grant Controls:** Block Access
- **Conditions:**
  - **Identity Type:** Agent Identity
  - **Risk Level:** High Agent Risk
  - **Client App:** All modern authentication clients
- **Exclusions:**
  - Designated break-glass or monitoring agents (if applicable)
- **Benefits:**
  - Prevents compromised agent identities from authenticating
  - Reduces automated compromise pathways and lateral movement

### ACME - AGENT - BLOCK - NonTrustedAgents

- **Policy Name:** `ACME - AGENT - BLOCK - NonTrustedAgents`
- **Scope:** AGENT
- **Target:** All Agent Identities that **do not** have the required security attribute `AgentApproved = true`.
- **Purpose:** Ensures only approved, security-vetted agents are allowed to authenticate. Any agent missing the required approval attribute is blocked.
- **Grant Controls:** Block Access
- **Conditions:**
  - **Identity Type:** Agent Identity
  - **Security Attribute:** `AgentApproved != true`
  - **Client App:** All modern authentication clients
- **Exclusions:**
  - Optional break-glass or emergency agent identities
- **Benefits:**
  - Enforces an allowlist model for trusted agent identities
  - Blocks rogue, misconfigured, or unapproved agents from authenticating



---


## Naming Conventions for Conditional Access and Groups

This document outlines clear, consistent, and scalable naming conventions tailored for managing Conditional Access (CA) and internal groups within Microsoft Entra.

[Scope]-[Technology/Service]-[Target]-[Descriptor(Optional)]

## Naming Convention Structure

### Components Explained:

- **Scope:**  
  - `CA`: Conditional Access specific groups.(These groups can be replicated with Inforcer)
  - `ACME`: Internal operational groups for targeting internal services, users, or devices.

- **Technology/Service:**  
  Identifies targeted services or technology (e.g., `Azure`, `M365`, `DevOps`, `Intune`, `W365`, `Exchange`).

- **Target:**  
  Defines who or what is targeted by the policy/group (`Users`, `Devices`, `Apps`, `Roles`, `Exclusion`, `Guests`, `Admins`).

- **Descriptor (Optional):**  
  Optional additional clarity (`Privileged`, `HighRisk`, `Compliance`).

---

## Examples

### Conditional Access (CA) Groups:

- `CA-DeviceExclusions`
- `CA-GlobalExclusions`
- `CA-GuestExclusions`
- `CA-ServiceAccounts`
- `CA-TravelingUsers`
- `CA-Azure-DevOps-Users`
- `CA-InternalLicensedUsers`
- `CA-AgentIdentities`
  



### Internal Operational (ACME) Groups:

- `ACME-W365-Users`
- `ACME-W365-Devices`
- `ACME-Intune-Devices`
- `ACME-Exchange-Admins-Privileged`
- `ACME-M365-Compliance-Users`

---


## Detailed Examples for Immediate Implementation

| **Group Name**              | **Description / Purpose**                                                                                                   | **Usage in CA Policies**                                                                                      | **Type**           | **Membership**                      |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------- |
| **CA-DeviceExclusions**     | Devices excluded from Conditional Access evaluations — typically service devices, shared kiosks, or troubleshooting devices. | Used as an *Exclude group* in device compliance or registration policies (e.g., INTUNE or GLOBAL GRANT).      | Conditional Access | **Assigned or Dynamic (deviceId)**  |
| **CA-GlobalExclusions**     | Universal exclusion group for emergency break-glass or exception accounts.                                                   | Excluded from **all** CA policies to prevent accidental lockout of admin access.                              | Conditional Access | **Assigned (manual)**               |
| **CA-GuestExclusions**      | Guest or external users exempt from specific policies (e.g., certain apps, trusted partners).                                | Excluded in guest-blocking or MFA-required policies for trusted external collaborators.                       | Conditional Access | **Assigned**                        |
| **CA-ServiceAccounts**      | Service or automation accounts that cannot perform MFA or Conditional Access prompts.                                        | Excluded in policies enforcing MFA or interactive sign-in requirements.                                       | Conditional Access | **Assigned (manually approved)**    |
| **CA-TravelingUsers**       | Internal users traveling or connecting from high-risk geolocations who require temporary policy exceptions.                  | Temporarily excluded from location-based block policies (e.g., NonTrustedLocations).                          | Conditional Access | **Assigned (temporary membership)** |
| **CA-Azure-DevOps-Users**   | Authorized users who can access **Azure DevOps** enterprise app.                                                             | Used to **include** or **exclude** users in app-specific policies (e.g., `ACME - APP - BLOCK - AzureDevOps`). | Conditional Access | **Assigned**                        |
| **CA-InternalLicensedUsers**| Internal members with active Microsoft 365 or Entra ID licenses. Used to scope CA policies to valid, licensed workforce accounts while excluding guests and unlicensed objects. | Included in *baseline CA policies* (e.g., Require MFA, Require Compliant Device) to target legitimate users only. | Conditional Access | **Dynamic (based on license status)** |


---

## Special Scenario Example

| Policy or Group                           | Description                                         |
|-------------------------------------------|-----------------------------------------------------|
| **CA Policy: ACME-GLOBAL-BLOCK-AzureDevOps**   | Blocks Azure Devops  access globally                      |
| **Exclude Group: ACME-Azure-DevOps**      | Azure DevOps authorized internal users              |

This leverages existing internal operational groups (`ACME`) for exclusions rather than creating separate Conditional Access-specific groups.

---

# Conditional Access (CA) Groups

These groups are used to include or exclude specific users, devices, or accounts in Conditional Access (CA) policies.  
All names follow the `CA-[Scope/Target]-[Descriptor]` structure.

---

### CA-DeviceExclusions

- **Group Name:** `CA-DeviceExclusions`
- **Scope:** Conditional Access
- **Target:** Devices
- **Purpose:** Contains devices excluded from Conditional Access enforcement (e.g., trusted lab devices, testing endpoints, or legacy hardware).
- **Usage Example:** Exclude from CA policies enforcing compliance or MFA for specific test or service devices.
- **Membership Type:** Assigned (manually managed)

---

### CA-GlobalExclusions

- **Group Name:** `CA-GlobalExclusions`
- **Scope:** Conditional Access
- **Target:** Global  (Users)
- **Purpose:** Master exclusion group used across all CA policies for emergency, break-glass, or trusted administrative accounts.
- **Usage Example:** Added as an exclusion to every major CA policy to prevent lockouts.
- **Membership Type:** Assigned (manually managed, tightly controlled)

---

### CA-GuestExclusions

- **Group Name:** `CA-GuestExclusions`
- **Scope:** Conditional Access
- **Target:** Guest Users
- **Purpose:** Used to exclude specific guest accounts (external users, vendors, or partners) from global or app-specific CA policies.
- **Usage Example:** Applied to CA policies enforcing MFA or location-based restrictions for guests.
- **Membership Type:** Assigned (manually managed)

---

### CA-ServiceAccounts

- **Group Name:** `CA-ServiceAccounts`
- **Scope:** Conditional Access
- **Target:** Service or Automation Accounts
- **Purpose:** Identifies accounts used by services, automation scripts, or integrations that may not support MFA or device compliance.
- **Usage Example:** Exclude from user-based MFA or device-based Conditional Access policies.
- **Membership Type:** Assigned (manually managed)

---

### CA-TravelingUsers

- **Group Name:** `CA-TravelingUsers`
- **Scope:** Conditional Access
- **Target:** Users
- **Purpose:** Identifies users frequently traveling or logging in from multiple countries. Used to relax or modify Conditional Access policies that might otherwise block them.
- **Usage Example:** Exclude from location-based blocking policies or grant specific access for mobile work scenarios.
- **Membership Type:** Assigned (manually managed)

---

### CA-Azure-DevOps-Users

- **Group Name:** `CA-Azure-DevOps-Users`
- **Scope:** Conditional Access
- **Technology/Service:** Azure DevOps
- **Target:** Users
- **Purpose:** Contains users authorized to access the Azure DevOps enterprise application.
- **Usage Example:** Included in policies that grant or exclude Azure DevOps access, such as `ACME - APP - BLOCK - AzureDevOps`.
- **Membership Type:** Assigned (manually managed)

---

 ### CA-InternalLicensedUsers

- **Group Name:** `CA-InternalLicensedUsers`
- **Scope:** Conditional Access
- **Target:** Internal licensed users (`userType = Member`)
- **Purpose:** Identifies all internal users with an active Microsoft 365 or Entra ID license. Used to scope Conditional Access policies to production workforce accounts only, excluding guests, service, or unlicensed users.
- **Usage Example:** Include in baseline Conditional Access policies such as *Require MFA* or *Require Compliant Device*.
- **Membership Type:** Dynamic (auto-populated based on license status)
- **Dynamic Membership Rule (KQL):**
  
```KUSTO
//licensed user P1
(user.assignedPlans -any (assignedPlan.servicePlanId -eq "41781fb2-bc02-4b7c-bd55-b576c07bb09d" and assignedPlan.capabilityStatus -eq "Enabled"))

//licensed user P1 synced from on prem
(user.assignedPlans -any (assignedPlan.servicePlanId -eq "41781fb2-bc02-4b7c-bd55-b576c07bb09d" and assignedPlan.capabilityStatus -eq "Enabled"))-and (user.dirSyncEnabled -eq true)

//P2 Licensed User
(user.assignedPlans -any (assignedPlan.servicePlanId -eq "eec0eb4f-6444-4f95-aba0-50c24d67f998" -and assignedPlan.capabilityStatus -eq "Enabled")


 ```

---

## Exsisting Policies to align

ACME Sync - Restrict Sign In

### ACME - APP - BLOCK - SignIn - Exclude-TrustedACMESyncIPs

- **Scope:** APP (Customer Tenant Sync)
- **Control Type:** BLOCK
- **Target:** Sign-ins
- **Purpose:** Blocks all sign-ins for the Customer Tenant Sync application from all locations except trusted Customer Tenant Sync IP addresses.
- **Exclusion Condition:** Named location in Entra ID containing Trusted Customer Tenant Sync IP ranges.


GSA - WebFilter Block Potentially Harmful

### ACME - APP - BLOCK - GSAWebFilter-PotentiallyHarmful

- **Scope:** APP (GSA WebFilter)
- **Control Type:** BLOCK
- **Target:** Potentially harmful or suspicious web traffic
- **Purpose:** Prevents users from accessing websites or domains flagged as potentially harmful by the GSA WebFilter.
- **Exclusion Group:** None by default; can be paired with a group like `ACME-WebFilter-Exclusions` for testing or exceptions.Currently this is only targeting the below group `GlobalSecureAccess`





## Best Practices for Scalability & Maintenance: GROUP CONFIGURATION

- Prioritize reusing existing internal (`ACME`) groups for exclusions.
- Create dedicated `CA-*` groups only when necessary for unique scenarios.
- Ensure consistency in formatting, naming, and documentation within Entra.

### ACME-Passkey-Users

- **Group Name:** `ACME-Passkey-Users`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology:** Passkey Authentication
- **Target:** Users
- **Purpose:** Targets internal users utilizing Passkey-based authentication methods.
- **Usage Example:** Can be used for targeted Conditional Access policies, authentication rules, or specific policy exclusions.

### ACME-ADM-Users-Dynamic

- **Group Name:** `ACME-ADM-Users-Dynamic`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Administrative Accounts (`ADM`)
- **Target:** Users
- **Descriptor:** Dynamic
- **Purpose:** Automatically includes all user accounts ending with `.adm` in their `userPrincipalName` or `onPremisesSamAccountName` for administrative targeting in Conditional Access or security policies.
- **Usage Example:** Targeting CA policies for privileged accounts, restricting risky sign-ins, or applying stricter MFA requirements.

```
(user.userPrincipalName -contains ".adm") -or (user.onPremisesSamAccountName -contains ".adm")
```

---

#### Example Dynamic Membership Rule (userPrincipalName match)
kusto
(user.userPrincipalName -contains ".adm")



### ACME-Internal-Users-Office

- **Group Name:** `ACME-Internal-Users-Office`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Internal Users
- **Target:** Office-based Users
- **Purpose:** Targets internal users accessing resources primarily from company office locations or corporate networks.
- **Usage Example:** Enforcing Conditional Access policies or network access rules specifically for users physically located at company premises.



### ACME-Internal-Users-Remote

- **Group Name:** `ACME-Internal-Users-Remote`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Internal Users
- **Target:** Remote Users
- **Purpose:** Targets internal users accessing resources remotely, from non-corporate or external networks.
- **Usage Example:** Applying Conditional Access policies, enhanced MFA requirements, VPN restrictions, or compliance controls tailored specifically for remote work scenarios.


### ACME-W365-Devices-Dynamic

- **Group Name:** `ACME-W365-Devices-Dynamic`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Windows 365 Cloud PCs (`W365`)
- **Target:** Devices
- **Descriptor:** Dynamic
- **Purpose:** Dynamic membership group automatically including all Windows 365 Cloud PC devices managed in Entra ID based on defined membership rules.
- **Usage Example:** Targeting Conditional Access policies, device-compliance policies, or management rules specifically for dynamically managed Windows 365 devices.
- **Membership Rule Example:**  
  ```azuread
  (device.deviceModel -contains "Cloud PC")


 ### ACME-AVD-Host-Dynamic

- **Group Name:** `ACME-AVD-Host-Dynamic`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Azure Virtual Desktop (AVD – RDSH / Windows 10 & 11 Multi-session)
- **Target:** Devices
- **Descriptor:** Dynamic
- **Purpose:** Dynamic membership group that automatically includes all Azure Virtual Desktop RDSH session host devices (Windows 10/11 multi-session) registered in Microsoft Entra ID.
- **Usage Example:**  
  Used for targeting Conditional Access device exclusions, Intune compliance policies, Defender configuration, monitoring, or security controls specific to Azure Virtual Desktop session hosts.
- **Membership Rule Example:**  
  ```azuread
  (device.deviceOSType -eq "Windows") and (device.operatingSystemSKU -eq "ServerRdsh")
  ```
 

### ACME-DUO-EAM-Users-Dynamic

- **Group Name:** `ACME-DUO-EAM-Users-Dynamic`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** DUO Endpoint Access Management (`DUOEAM`)
- **Target:** Users
- **Descriptor:** Dynamic
- **Purpose:** Dynamically includes all internal users who are designated for DUO EAM Conditional Access policies or authentication requirements.
- **Usage Example:** Targeting Conditional Access policies requiring DUO MFA or device compliance verification.

---

#### Membership Rule (ExtAttribute1 Contains Identifier)
```kusto
(user.extensionAttribute1 -eq "DUO")`Could be any other External Authentication method`

```

### ACME-MTO-Sync-User-Dynamic

- **Group Name:** `ACME-MTO-Sync-User-Dynamic`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Multitenant Orginization sync with ACME (`MTO-Sync`)
- **Target:** Users
- **Descriptor:** Dynamic
- **Purpose:** Dynamically includes all internal users who are designated for Multitenant Sync configuration with ACME.
- **Usage Example:** Targeting Conditional Access policies requiring DUO MFA or device compliance verification.

---

#### Membership Rule (ExtAttribute1 Contains Identifier)
```kusto
(user.extensionAttribute1 -eq "MTO")
```




### ACME-DUO-EAM-User-Exclusions

- **Group Name:** `ACME-DUOEAM-User-Exclusions`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** DUO Endpoint Access Management (`DUO`)
- **Target:** User Exclusions
- **Purpose:** Identifies users explicitly excluded from DUO EAM Conditional Access policies.
- **Usage Example:** Used as exclusions in Conditional Access policies to exempt specific users (e.g., admins or service accounts) from DUO MFA or access rules.

### ACME-Inforcer-Admin

- **Group Name:** `ACME-Inforcer-Admin`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Inforcer Application
- **Target:** Admin Users
- **Purpose:** Grants full administrative access to the Inforcer app, including configuration changes, policy management, and user provisioning.
- **Usage Example:** Assign this group in Entra to allow admin-level privileges for Inforcer app administration.

---

### ACME-Inforcer-Engineer

- **Group Name:** `ACME-Inforcer-Engineer`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Inforcer Application
- **Target:** Engineer Users
- **Purpose:** Provides engineering-level access to the Inforcer app, typically for implementing, troubleshooting, and maintaining integrations or technical configurations. Required for client onboarding
- **Usage Example:** Targeted for technical staff who require elevated but not full administrative rights in Inforcer.

---

### ACME-Inforcer-ReadOnly

- **Group Name:** `ACME-Inforcer-ReadOnly`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Inforcer Application
- **Target:** Read-Only Users
- **Purpose:** Grants view-only access to the Inforcer app, enabling users to review configurations, logs, or reports without making changes.
- **Usage Example:** Assign to auditors, compliance officers, or staff who only need to monitor Inforcer without modification rights.


### ACME-JIT-Users-Dynamic

- **Group Name:** `ACME-JIT-Users-Dynamic`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Just-In-Time (JIT) Access
- **Target:** Users
- **Descriptor:** Dynamic
- **Purpose:** Dynamically includes all users whose UPN contains `_jit`, indicating they are designated for Just-In-Time access workflows.
- **Usage Example:** Targeting Conditional Access policies that require additional verification, device compliance, or security conditions before allowing JIT elevation.
- **Membership Rule:**
  ```kusto
  (user.userPrincipalName -contains "_jit")

### ACME-Azure-DevOps-Users

- **Group Name:** `ACME-Azure-DevOps-Users`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Azure DevOps
- **Target:** Users
- **Purpose:** Contains internal users who are authorized to access Azure DevOps. Typically used to include members in Conditional Access policies granting access to the Azure DevOps enterprise app or to exclude them from blocking policies.
- **Usage Example:** 
  - Inclusion in a policy that allows Azure DevOps access.
  - Exclusion from app-specific block policies such as `ACME - APP - BLOCK - AzureDevOps`.
- **Membership Type:** Assigned (manually managed to ensure access is only granted to approved individuals).



### ACME-Disabled-Users-Dynamic

- **Group Name:** `ACME-Disabled-Users-Dynamic`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Entra ID (Microsoft Azure AD)
- **Target:** Users
- **Descriptor:** Dynamic
- **Purpose:** Dynamically includes all accounts in Entra ID that are disabled (sign-in blocked). Intended for monitoring, reporting, or applying specific Conditional Access policies.
- **Usage Example:** 
  - Used in compliance reports to track inactive or disabled accounts.
  - Exclude from active user access policies to reduce unnecessary evaluation.
- **Membership Rule:**
  ```kusto
  (user.accountEnabled -eq false)
  ```


### ACME-Guest-Users-Dynamic

- **Group Name:** `ACME-Guest-Users-Dynamic`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Entra ID (Microsoft Azure AD)
- **Target:** Guest Users
- **Descriptor:** Dynamic
- **Purpose:** Dynamically includes all guest accounts in Entra ID. Useful for applying guest-specific Conditional Access policies, monitoring external access, and excluding guests from internal-only resources.
- **Usage Example:** 
  - Apply stricter Conditional Access controls for guest accounts.
  - Separate reporting for external collaborators.
  - Exclude guests from policies intended for internal users.
- **Membership Rule:**
  ```
  kusto
  (user.userType -eq "Guest")

### ACME-AUTH-SMS-TEMP

- **Group Name:** `ACME-AUTH-SMS-TEMP`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Authentication Methods
- **Target:** SMS Authentication
- **Descriptor:** TEMP
- **Purpose:** Temporary group used for testing SMS authentication as an MFA method.
- **Usage Example:** Applied to Conditional Access test policies that require SMS authentication for sign-in validation.
- **Notes:** 
  - This group is **temporary** and should be retired once testing is complete. 
  - For production readiness, replace with `ACME-AUTH-SMS-Users` (or `ACME-AUTH-SMS-Dynamic` if membership is automated).


### ACME-PIM-GlobalAdmins

- **Group Name:** `ACME-PIM-GlobalAdmins`
- **Scope:** Internal Operational Group (`ACME`)
- **Technology/Service:** Entra ID Privileged Identity Management (PIM)
- **Target:** Global Administrators
- **Descriptor:** PIM
- **Purpose:** Used for Privileged Identity Management of the Global Administrator role. Membership in this group allows just-in-time (JIT) activation of Global Admin privileges rather than persistent assignment.
- **Usage Example:** 
  - Assign this group to the Global Administrator directory role as a PIM-eligible group.
  - Members must activate their privileges via PIM with MFA, justification, and time-limited access.
- **Best Practices:**
  - Pair with Conditional Access policies enforcing MFA and compliant devices for activation.
  - Regularly review group membership to ensure only approved admins are included.
  - Create an exclusion group (e.g., `ACME-PIM-GlobalAdmins-Exclusions`) for break-glass accounts.
