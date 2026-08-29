# IAC - P2 - GLOBAL - GRANT - Medium-Risk Users - Risk Remediation

## Overview

| Field | Value |
|-------|-------|
| **Policy Name** | IAC - P2 - GLOBAL - GRANT - Medium-Risk Users - Risk Remediation |
| **Category** | P2 / Identity Protection |
| **License** | Entra ID P2 |
| **Control Type** | GRANT |
| **Priority** | Recommended |

## Intent

Requires authentication strength and risk remediation for users flagged as medium-risk by Entra Identity Protection. Medium user risk typically indicates credential exposure in data breaches or anomalous behaviour patterns. This policy replaces the legacy "Require password change" approach with risk remediation, which supports both password-based and passwordless (FIDO2, Windows Hello for Business) users. Requires Entra ID P2.

## Why Risk Remediation Instead of Password Change

The legacy `Require password change` grant control does not support passwordless users. Users enrolled in FIDO2, Windows Hello for Business, or External Authentication Methods (EAM) such as Duo cannot complete a password change flow and will be permanently blocked. `Require risk remediation` automatically routes users to the correct remediation path based on their registered authentication methods.

> **Note for EAM users (Duo, Okta, Ping):** This policy uses an authentication strength object. EAM providers are not supported in authentication strength objects. If your organisation uses an External Authentication Method, a companion policy scoped to the EAM group using the built-in `Require MFA` control (not an auth strength) is required — see `IAC - P2 - GLOBAL - GRANT - EAM - High-Risk Users - Risk Remediation`.

## Policy Configuration

| Component | Value |
|-----------|-------|
| **Users** | All users |
| **Excluded Users** | Break-glass group, EAM users group |
| **Cloud Apps** | All cloud apps |
| **Conditions** | User risk: medium, Client apps: all |
| **Grant Controls** | 🔐 Authentication strength (Modern MFA + TAP) AND 🔑 Require risk remediation |
| **Session Controls** | — |

## MS Learn References

- [Identity Protection risk policies](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-policies)
- [Require risk remediation (preview)](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-policies#require-risk-remediation-with-microsoft-managed-remediation-preview)
- [Configure risk policies](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies)
