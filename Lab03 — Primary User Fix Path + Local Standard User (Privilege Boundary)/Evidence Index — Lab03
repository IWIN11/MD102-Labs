# Evidence Index — Lab 03 (Primary User / Join State + Local Standard User)

**Type:** LAB  
**Date:** 2026-01-23  
**Location:** `MD102-Labs/Lab03 — <your lab folder name>/`

---

## Step 01 — Baseline: device record exists in Intune
**What it proves:** You establish a reproducible baseline by confirming the target Windows device is visible in Intune before making changes.

### Evidence
- `Lab03 01 Pre Intuneadmincenter Devices Windows Aerislabwin11pc1.png`  
![](evidence/Lab03%2001%20Pre%20Intuneadmincenter%20Devices%20Windows%20Aerislabwin11pc1.png)

- `Lab03 02 Pre Intuneadmincenter Devices Windows Aerislabwin11pc1.png`  
![](evidence/Lab03%2002%20Pre%20Intuneadmincenter%20Devices%20Windows%20Aerislabwin11pc1.png)

---

## Step 02 — Capture the initial block (failed change / blocked state)
**What it proves:** You document a real failure state upfront (production-grade troubleshooting practice), instead of rewriting history after remediation.

### Evidence
- `Lab03 03 Pre ChangeAerislabwin11pc1 failed.png`  
![](evidence/Lab03%2003%20Pre%20ChangeAerislabwin11pc1%20failed.png)

---

## Step 03 — Create employee identity (beta) in Entra ID
**What it proves:** You can create a managed employee identity in Entra ID as a prerequisite for predictable endpoint ownership/association in enterprise environments.

### Evidence
- `Lab03 04 Pre Entraadmincenter User Newuser .png`  
![](evidence/Lab03%2004%20Pre%20Entraadmincenter%20User%20Newuser%20.png)

- `Lab03 05 Pre Entraadmincenter User Newuser Beta.png`  
![](evidence/Lab03%2005%20Pre%20Entraadmincenter%20User%20Newuser%20Beta.png)

- `Lab03 06 Pre Entraadmincenter User Newuser Beta completed.png`  
![](evidence/Lab03%2006%20Pre%20Entraadmincenter%20User%20Newuser%20Beta%20completed.png)

- `Lab03 06 Pre Entraadmincenter User Newuser Beta overview.png`  
![](evidence/Lab03%2006%20Pre%20Entraadmincenter%20User%20Newuser%20Beta%20overview.png)

---

## Step 04 — Make beta usable: fix Usage location + assign license
**What it proves:** You can resolve a common admin blocker (Usage location) and complete license assignment so the employee identity becomes operationally usable.

### Evidence
- `Lab03 07 Pre MS365admincenter BetaLicenses Check.png`  
![](evidence/Lab03%2007%20Pre%20MS365admincenter%20BetaLicenses%20Check.png)

- `Lab03 07 Pre MS365admincenter AddLicenses Beta assgin.png`  
![](evidence/Lab03%2007%20Pre%20MS365admincenter%20AddLicenses%20Beta%20assgin.png)

- `Lab03 07 Pre MS365admincenter UserBeta LocationCanada and Licensesasgin.png`  
![](evidence/Lab03%2007%20Pre%20MS365admincenter%20UserBeta%20LocationCanada%20and%20Licensesasgin.png)

---

## Step 05 — Troubleshooting signal: verify join state (AzureAdJoined)
**What it proves:** You validate the device join state with command evidence (dsregcmd signal), which explains why some device-level controls may be unavailable depending on enrollment/join posture.

### Evidence
- `Lab03 11 cmdrunasadmin check azureadjoin.png`  
![](evidence/Lab03%2011%20cmdrunasadmin%20check%20azureadjoin.png)

- `Lab03 12 azureadjoin no.png`  
![](evidence/Lab03%2012%20azureadjoin%20no.png)

- `Lab03 13 DetachOldConnection.png` *(if applicable)*  
![](evidence/Lab03%2013%20DetachOldConnection.png)

- `Lab03 14 DetachOldConnection restart.png` *(if applicable)*  
![](evidence/Lab03%2014%20DetachOldConnection%20restart.png)

---

## Step 06 — Intune-side action: assignment captured
**What it proves:** You capture an Intune-side admin action as part of the workflow (not only identity work), ensuring the lab reflects real administrative operations.

### Evidence
- `Lab03 08 Pre Intuneadmin assgin.png`  
![](evidence/Lab03%2008%20Pre%20Intuneadmin%20assgin.png)

---

## Step 07 — Windows local standard user (employee simulation)
**What it proves:** You can create a local Standard user to simulate a corporate endpoint where IT retains admin control while end-users operate under least privilege.

### Evidence
- `Lab03 26 setting account otheruser add.png`  
![](evidence/Lab03%2026%20setting%20account%20otheruser%20add.png)

- `Lab03 27 addstandarduser not MSaccount.png`  
![](evidence/Lab03%2027%20addstandarduser%20not%20MSaccount.png)

- `Lab03 28 addstandarduser not MSaccount.png`  
![](evidence/Lab03%2028%20addstandarduser%20not%20MSaccount.png)

- `Lab03 29 addstandarduser.png`  
![](evidence/Lab03%2029%20addstandarduser.png)

- `Lab03 29 addstandarduser completed.png`  
![](evidence/Lab03%2029%20addstandarduser%20completed.png)

---

## Step 08 — Least privilege enforcement: remove beta from local Administrators + verify final membership
**What it proves:** You can detect and correct a least-privilege violation (user accidentally in local Administrators), then prove the final state using command/group membership evidence.

### Evidence
- `Lab03 30 found Beta under admingroup.png`  
![](evidence/Lab03%2030%20found%20Beta%20under%20admingroup.png)

- `Lab03 31 delete beta from admingroup.png`  
![](evidence/Lab03%2031%20delete%20beta%20from%20admingroup.png)

- `Lab03 32 Beta is stduser.png`  
![](evidence/Lab03%2032%20Beta%20is%20stduser.png)

- `Lab03 33 Beta is stduser.png`  
![](evidence/Lab03%2033%20Beta%20is%20stduser.png)

