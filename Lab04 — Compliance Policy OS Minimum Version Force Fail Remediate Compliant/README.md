# Lab04 — Compliance Policy OS Minimum Version Force Fail Remediate Compliant

**Type:** LAB  
**Date:** 2026-01-27  
**Status:** Done  
**Device:** PC1 (Windows 11 Pro)

---

## Runbook (Step-by-step)

### 0) Baseline — Confirm Compliant
**Where:** Intune admin center → Devices → All devices → PC1 → Device compliance  
**Action:** Confirm current overall compliance state is **Compliant** (capture full page incl. last check-in).  
**Expected:** Compliance status = Compliant  
**Evidence:**  
![lab04_1_01_Baseline_Compliant](./evidences/lab04_1_01_Baseline_Compliant.png)

---

### 1) Prepare Assignment Target — Create Group + Add Member
**Where:** Entra admin center → Groups  
**Action:** Create a new group for policy assignment, then add **Beta** as a member.  
**Expected:** Group exists and Beta is in the group  
**Evidence:**  
![lab04_1_02_Entra_CreateGroup_ForAssignment](./evidences/lab04_1_02_Entra_CreateGroup_ForAssignment.png)  
![lab04_1_03_Entra_GroupMember_Beta](./evidences/lab04_1_03_Entra_GroupMember_Beta.png)

---

### 2) Record Current OS Version (for later comparison)
**Where:** PC1 → Settings / About (or winver)  
**Action:** Capture current OS version/build.  
**Expected:** OS version is recorded (baseline reference)  
**Evidence:**  
![lab04_1_04_Device_OSVersion_Current](./evidences/lab04_1_04_Device_OSVersion_Current.png)

---

### 3) Create Compliance Policy — Minimum OS Version (Force Fail)
**Where:** Intune admin center → Devices → Compliance policies → Create policy (Windows 10 and later)  
**Action:** Create a compliance policy and set **Minimum OS version** to a value higher than the current OS version.  
**Expected:** Policy created successfully and configured to force noncompliance  
**Evidence:**  
![lab04_1_05_Intune_device_compliance_createNewpolicy](./evidences/lab04_1_05_Intune_device_compliance_createNewpolicy.png)  
![lab04_1_06_Intune_device_compliance_createNewpolicy_complete](./evidences/lab04_1_06_Intune_device_compliance_createNewpolicy_complete.png)

---

### 4) Observe Grace Period (as captured)
**Where:** Intune / Compliance evaluation context  
**Action:** Capture the grace period signal/state as observed during the run.  
**Expected:** Grace period evidence present  
**Evidence:**  
![lab04_1_07_compliance_ingraceperiod=1](./evidences/lab04_1_07_compliance_ingraceperiod=1.png)

---

### 5) Trigger Device Sync
**Where:** PC1 → Access work or school → (work account) → Info → Sync  
**Action:** Trigger a manual sync and confirm it completes.  
**Expected:** Sync is triggered and completes successfully  
**Evidence:**  
![lab04_1_08_pc1_setting_account_accountworkorschool_info_sync](./evidences/lab04_1_08_pc1_setting_account_accountworkorschool_info_sync.png)  
![lab04_1_09_pc1_sync_success_and_ingraceperiod](./evidences/lab04_1_09_pc1_sync_success_and_ingraceperiod.png)

---

### 6) Validate Noncompliant + Reason (Minimum OS Version)
**Where:** Intune admin center → PC1 → Device compliance / Reports  
**Action:** Confirm device becomes **Noncompliant** and verify the reason is **Minimum OS version** not met.  
**Expected:** Status = Noncompliant; reason explicitly points to Minimum OS version  
**Evidence:**  
![lab04_1_10_viewreport_Noncompliant_Status](./evidences/lab04_1_10_viewreport_Noncompliant_Status.png)  
![lab04_1_11_MinOsVersion_noncompliant](./evidences/lab04_1_11_MinOsVersion_noncompliant.png)

---

### 7) Remediate — Revert Policy to Restore Compliance
**Where:** Intune admin center → Compliance policies → (the policy) → Edit  
**Action:** Edit policy and revert **Minimum OS version** to a compliant value; save changes.  
**Expected:** Policy saved successfully  
**Evidence:**  
![lab04_1_12_edit_comliancepolicy](./evidences/lab04_1_12_edit_comliancepolicy.png)  
![lab04_1_13_edit_comliancepolicy_completed](./evidences/lab04_1_13_edit_comliancepolicy_completed.png)

---

### 8) Sync Again + Confirm Compliant Restored
**Where:** PC1 sync + Intune device compliance page  
**Action:** Trigger sync again, then verify compliance returns to **Compliant**.  
**Expected:** Status = Compliant  
**Evidence:**  
![lab04_1_14_pc1_sync_updated](./evidences/lab04_1_14_pc1_sync_updated.png)  
![lab04_1_15_compliant_restored](./evidences/lab04_1_15_compliant_restored.png)

---

## Outcome
**Compliant → Noncompliant (Minimum OS version force fail) → Compliant (policy remediation)** verified with a complete evidence chain.

