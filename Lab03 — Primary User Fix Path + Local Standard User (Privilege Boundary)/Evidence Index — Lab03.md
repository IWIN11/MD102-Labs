# Evidence Index — Lab 03 (Primary User Fix Path + Standard User Validation)

**Type:** LAB  
**Date:** 2026-01-xx  
**Location:** `MD102-Labs/Lab03 — Primary User Fix Path + .../`

---

## Step 01 — Pre-check: Intune device list baseline
**What it proves:** Baseline portal visibility before changes.

### Evidence
- `Lab03_01_Pre_Intuneadmincenter_Devices_Windows_Aerislabwin11pc1.png`  
![](evidence/Lab03_01_Pre_Intuneadmincenter_Devices_Windows_Aerislabwin11pc1.png)

- `Lab03_02_Pre_Intuneadmincenter_Devices_Windows_Aerislabwin11pc1.png`  
![](evidence/Lab03_02_Pre_Intuneadmincenter_Devices_Windows_Aerislabwin11pc1.png)

---

## Step 02 — Entra ID: create Beta user
**What it proves:** Beta user exists in Entra ID and is ready for licensing/enrollment.

### Evidence
- `Lab03_04_Pre_Entraadmincenter_User_Newuser_.png`  
![](evidence/Lab03_04_Pre_Entraadmincenter_User_Newuser_.png)

- `Lab03_05_Pre_Entraadmincenter_User_Newuser_Beta.png`  
![](evidence/Lab03_05_Pre_Entraadmincenter_User_Newuser_Beta.png)

- `Lab03_06_Pre_Entraadmincenter_User_Newuser_Beta_completed.png`  
![](evidence/Lab03_06_Pre_Entraadmincenter_User_Newuser_Beta_completed.png)

- `Lab03_07_Pre_Entraadmincenter_User_Newuser_Beta_overview.png`  
![](evidence/Lab03_07_Pre_Entraadmincenter_User_Newuser_Beta_overview.png)

---

## Step 03 — Licensing: Usage location + license assignment (Beta)
**What it proves:** Beta is eligible for licensing (Usage location set) and license assignment flow is completed.

### Evidence
- `Lab03_07_Pre_MS365admincenter_AddLicenses_Beta_assgin.png`  
![](evidence/Lab03_07_Pre_MS365admincenter_AddLicenses_Beta_assgin.png)

- `Lab03_07_Pre_MS365admincenter_BetaLicenses_Check.png`  
![](evidence/Lab03_07_Pre_MS365admincenter_BetaLicenses_Check.png)

- `Lab03_07_Pre_MS365admincenter_UserBeta_LocationCanada_and_Licensesasgin.png`  
![](evidence/Lab03_07_Pre_MS365admincenter_UserBeta_LocationCanada_and_Licensesasgin.png)

- `Lab03_08_Pre_Intuneadmin_assgin.png`  
![](evidence/Lab03_08_Pre_Intuneadmin_assgin.png)

- `Lab03_09_Pre_Intuneadmin_Addassgin_Aerislab.png`  
![](evidence/Lab03_09_Pre_Intuneadmin_Addassgin_Aerislab.png)

- `Lab03_10_Button_still_gray.png`  
![](evidence/Lab03_10_Button_still_gray.png)

- `Lab03_24_Button_active_blue.png`  
![](evidence/Lab03_24_Button_active_blue.png)

- `Lab03_25_Button_active_blue_successful.png`  
![](evidence/Lab03_25_Button_active_blue_successful.png)

---

## Step 04 — Entra join: detach old connection + join with Beta + confirm AzureADJoined
**What it proves:** Device successfully joins Entra ID under Beta path; AzureADJoined state confirmed.

### Evidence
- `Lab03_03_Pre_ChangeAerislabwin11pc1_failed.png`  
![](evidence/Lab03_03_Pre_ChangeAerislabwin11pc1_failed.png)

- `Lab03_11_cmdrunasadmin_check_azureadjoin.png`  
![](evidence/Lab03_11_cmdrunasadmin_check_azureadjoin.png)

- `Lab03_12_azureadjoin_no.png`  
![](evidence/Lab03_12_azureadjoin_no.png)

- `Lab03_13_DetachOldConnection.png`  
![](evidence/Lab03_13_DetachOldConnection.png)

- `Lab03_14_DetachOldConnection_restart.png`  
![](evidence/Lab03_14_DetachOldConnection_restart.png)

- `Lab03_15_Join_to_EntraID_withBeta.png`  
![](evidence/Lab03_15_Join_to_EntraID_withBeta.png)

- `Lab03_16_Join_to_EntraID_with_Beta.png`  
![](evidence/Lab03_16_Join_to_EntraID_with_Beta.png)

- `Lab03_17_password_created_when_create_BetaUser.png`  
![](evidence/Lab03_17_password_created_when_create_BetaUser.png)

- `Lab03_18_change_usertype_to_standarduser_later.png`  
![](evidence/Lab03_18_change_usertype_to_standarduser_later.png)

- `Lab03_19_join_completed.png`  
![](evidence/Lab03_19_join_completed.png)

- `Lab03_20_AzureAdJoined_Yes.png`  
![](evidence/Lab03_20_AzureAdJoined_Yes.png)

---

## Step 05 — Company Portal + Intune validation
**What it proves:** Beta signs into Company Portal; device appears in Intune portal after enrollment/connection.

### Evidence
- `Lab03_21_companypotal_Beta.png`  
![](evidence/Lab03_21_companypotal_Beta.png)

- `Lab03_21_companypotal_signin_Beta.png`  
![](evidence/Lab03_21_companypotal_signin_Beta.png)

- `Lab03_22_Betaneeddownload_authenticatorApp_oncellphone.png`  
![](evidence/Lab03_22_Betaneeddownload_authenticatorApp_oncellphone.png)

- `Lab03_23_Beta_connected_successful.png`  
![](evidence/Lab03_23_Beta_connected_successful.png)

- `Lab03_23_Beta_showup_on_IntuneSide_successful.png`  
![](evidence/Lab03_23_Beta_showup_on_IntuneSide_successful.png)

---

## Step 06 — Local: add standard user (not Microsoft account)
**What it proves:** A local standard user is created via Windows UI (non-Microsoft account flow).

### Evidence
- `Lab03_26_setting_account_otheruser_add.png`  
![](evidence/Lab03_26_setting_account_otheruser_add.png)

- `Lab03_27_addstandarduser_not_MSaccount.png`  
![](evidence/Lab03_27_addstandarduser_not_MSaccount.png)

- `Lab03_28_addstandarduser_not_MSaccount.png`  
![](evidence/Lab03_28_addstandarduser_not_MSaccount.png)

- `Lab03_29_addstandarduser.png`  
![](evidence/Lab03_29_addstandarduser.png)

- `Lab03_29_addstandarduser_completed.png`  
![](evidence/Lab03_29_addstandarduser_completed.png)

---

## Step 07 — Local privilege validation: Beta is NOT admin (standard user)
**What it proves:** You can detect incorrect local admin membership, remove it, and re-validate standard user state.

### Evidence
- `Lab03_30_found_Beta_under_admingroup.png`  
![](evidence/Lab03_30_found_Beta_under_admingroup.png)

- `Lab03_31_delete_beta_from_admingroup.png`  
![](evidence/Lab03_31_delete_beta_from_admingroup.png)

- `Lab03_32_Beta_is_stduser.png`  
![](evidence/Lab03_32_Beta_is_stduser.png)

- `Lab03_33_Beta_is_stduser.png`  
![](evidence/Lab03_33_Beta_is_stduser.png)

