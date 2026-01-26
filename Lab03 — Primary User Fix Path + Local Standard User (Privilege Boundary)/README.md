# Lab03 — Primary User Fix Path + Standard User Validation

**Type:** LAB  
**Date:** 2026-01-23  
**Status:** Done  
**Note:** Evidence filenames reflect the capture sequence during troubleshooting; the step numbers reflect the logical remediation narrative.
---

## Goal (Target State)
1. Create a cloud user **Beta** in Entra ID and assign Intune license correctly (Usage location + license assignment).
2. Join the Windows 11 device to Entra ID with the Beta account and validate it appears in Intune.
3. Validate **Beta is a Standard user locally** (not in local Administrators), with observable permission differences.

---

## Environment
- Tenant: Aeris Lab  
- Tenant domain: `aerislab.onmicrosoft.com`
- Device: Aeris-lab-win11-pc1 (Windows 11 Pro)
- Work account used for join/enrollment: Beta (Entra ID user)

---

## Constraints / Boundaries
- Intune Plan 1 tenant (no Entra ID P1/P2 assumptions)

---

## Deliverables
- Evidence set (screenshots) in `/evidence`
- Evidence map: `evidence-index.md`

---

## Runbook (Step-by-step)

### Step 01 — Pre-check: Intune device list baseline (Primary user not editable on PC1)

**Purpose:** Capture the baseline state in Intune before any changes, and document the initial issue: **PC1’s Primary user could not be edited**, which does not match typical enterprise operational needs. **Primary user (Intune)** is the device’s assigned user record used for ownership and some user-scoped management contexts; the issue here is that the **Change** action was disabled.  

**Evidence:** Lab03_01–Lab03_03

![](./evidence/Lab03_01_Pre_Intuneadmincenter_Devices_Windows_Aerislabwin11pc1.png)
![](./evidence/Lab03_02_Pre_Intuneadmincenter_Devices_Windows_Aerislabwin11pc1.png)
![](./evidence/Lab03_03_Pre_ChangeAerislabwin11pc1_failed.png)


### Step 02 — Validate permissions: Intune admin role still cannot edit Primary user

**Purpose:** Confirm whether assigning Intune administrator permissions to the Aeris Lab account resolves the issue. 
##Result:## the **Change Primary user** control remained disabled after role assignment, so further investigation moved to **device join/enrollment state** rather than continuing RBAC changes.

**Evidence:** Lab03_11–Lab03_13

![](./evidence/Lab03_11_Pre_Intuneadmin_assgin.png)
![](./evidence/Lab03_12_Pre_Intuneadmin_Addassgin_Aerislab.png)
![](./evidence/Lab03_13_Button_still_gray.png)


### Step 03 — Device state check on PC1: AzureADJoined = No

**Purpose:** Verify PC1’s join state to identify why user assignment actions are blocked. Observation: **AzureADJoined = No**, suggesting the device is not properly joined/registered in Entra ID for expected identity-bound management behavior.  

**Evidence:** Lab03_14–Lab03_15

![](./evidence/Lab03_14_cmdrunasadmin_check_azureadjoin.png)
![](./evidence/Lab03_15_azureadjoin_no.png)


### Step 04 — Create Beta user in Entra ID

**Purpose:** Create a dedicated test user for controlled enrollment and role/permission validation.  

**Evidence:** Lab03_04–Lab03_07

![](./evidence/Lab03_04_Pre_Entraadmincenter_User_Newuser_.png)
![](./evidence/Lab03_05_Pre_Entraadmincenter_User_Newuser_Beta.png)
![](./evidence/Lab03_06_Pre_Entraadmincenter_User_Newuser_Beta_completed.png)
![](./evidence/Lab03_07_Pre_Entraadmincenter_User_Newuser_Beta_overview.png)


### Step 05 — Fix licensing: Usage location + license assignment (Beta)

**Purpose:** Ensure Beta can be successfully licensed by setting **Usage location**, then completing the license assignment flow (resolving “invalid usage location” / assignment blockers).  

**Evidence:** Lab03_08–Lab03_10

![](./evidence/Lab03_08_Pre_MS365admincenter_AddLicenses_Beta_assgin.png)
![](./evidence/Lab03_09_Pre_MS365admincenter_BetaLicenses_Check.png)
![](./evidence/Lab03_10_Pre_MS365admincenter_UserBeta_LocationCanada_and_Licensesasgin.png)


### Step 06 — Detach old connection and join device to Entra ID using Beta

**Purpose:** Remove the previous linkage as needed, complete **Entra ID join** using Beta, and confirm the device reports **AzureADJoined = Yes**.  

**Evidence:** Lab03_16–Lab03_23

![](./evidence/Lab03_16_DetachOldConnection.png)
![](./evidence/Lab03_17_DetachOldConnection_restart.png)
![](./evidence/Lab03_18_Join_to_EntraID_withBeta.png)
![](./evidence/Lab03_19_Join_to_EntraID_with_Beta.png)
![](./evidence/Lab03_20_password_created_when_create_BetaUser.png)
![](./evidence/Lab03_21_change_usertype_to_standarduser_later.png)
![](./evidence/Lab03_22_join_completed.png)
![](./evidence/Lab03_23_AzureAdJoined_Yes.png)


### Step 07 — Company Portal sign-in and Intune validation

**Purpose:** Sign in to Company Portal with Beta and validate the device is successfully enrolled and visible in Intune (device list + device details).  

**Evidence:** Lab03_24–Lab03_29

![](./evidence/Lab03_24_companypotal_signin_Beta.png)
![](./evidence/Lab03_25_Betaneeddownload_authenticatorApp_oncellphone.png)
![](./evidence/Lab03_26_Beta_connected_successful.png)
![](./evidence/Lab03_27_Beta_showup_on_IntuneSide_successful.png)
![](./evidence/Lab03_28_Button_active_blue.png)
![](./evidence/Lab03_29_Button_active_blue_successful.png)


### Step 08 — Add a local standard user (non-Microsoft account)

**Purpose:** Create a local (non-cloud) standard user account to support controlled local access and to test standard-user operational scenarios on a managed endpoint.  

**Evidence:** Lab03_30–Lab03_34

![](./evidence/Lab03_30_setting_account_otheruser_add.png)
![](./evidence/Lab03_31_addstandarduser_not_MSaccount.png)
![](./evidence/Lab03_32_addstandarduser_not_MSaccount.png)
![](./evidence/Lab03_33_addstandarduser.png)
![](./evidence/Lab03_34_addstandarduser_completed.png)


### Step 09 — Fix local privilege: remove Beta from Administrators; confirm standard

**Purpose:** Enforce least privilege by removing Beta from the local **Administrators** group and confirming Beta operates as a **standard user** on the managed endpoint.  

**Evidence:** Lab03_35–Lab03_38

![](./evidence/Lab03_35_found_Beta_under_admingroup.png)
![](./evidence/Lab03_36_delete_beta_from_admingroup.png)
![](./evidence/Lab03_37_Beta_is_stduser.png)
![](./evidence/Lab03_38_Beta_is_stduser.png)



---

## Outcome
- Beta user created, licensed, and used to join device to Entra ID.
- Device appears in Intune and shows expected presence after Company Portal sign-in.
- Local privilege verified: Beta is standard user (not in Administrators).

