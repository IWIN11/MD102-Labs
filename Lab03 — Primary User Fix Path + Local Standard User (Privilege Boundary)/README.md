# Lab03 — Primary User Fix Path + Local Standard User (Privilege Boundary)
Evidence gallery: see Evidence Index

Type: LAB  
Date: 2026-01-23  
Status: Done (Local privilege boundary validated; device/user prerequisites documented)

---

## Goal (Target State)
Establish a clean, production-like identity + device setup so the Windows endpoint can be managed consistently, and demonstrate a clear **Admin vs Standard user** boundary:

- Create a real employee identity (**beta**) in Entra ID and make it usable (Usage location + license)
- Validate join state signals used for troubleshooting (AzureAdJoined YES/NO)
- Create a **local Standard user (beta)** on the same Windows device
- Prove least privilege by removing beta from local Administrators and validating final membership (command evidence)

---

## Environment
Tenant: Aeris Lab  
Tenant domain: aerislab.onmicrosoft.com  

Work identities:
- Admin / lab identity: Aeris (tenant admin context)
- Employee identity: beta (Entra ID user)

Device:
- Windows 11 Pro desktop (fresh OS install)
- Device name: Aeris-lab-win11-pc1 (or target Win11 desktop used in Lab02)

Notes:
- Some security/OS settings (e.g., Tamper Protection, manual time change) may be policy-managed and not suitable for proving privilege differences.
- For privilege validation, use **local group membership + command output** as authoritative evidence.

---

## Constraints / Boundaries
- Tenant licensing boundary applies (do not assume Entra ID P1/P2 features).
- Primary user changes and certain device settings can be blocked depending on join/enrollment state.
- Secure Desktop (UAC credential prompt) may be non-screenshotable; command evidence is used instead.

---

## Deliverables
A complete evidence set (screenshots) showing:
- Device baseline and initial blocked state
- Creation of Entra user beta
- Usage location + license assignment for beta
- Join-state checks (AzureAdJoined signal)
- Local standard user creation (beta)
- Least privilege enforcement: beta removed from local Administrators + final membership verified
Evidence map: evidence-index.md

---

## Runbook (Step-by-step)

### Step 1 — Baseline: confirm device exists and capture initial blocked state
Purpose: record the starting point before changes (what existed, what was blocked).  
Evidence:
- Lab03 01 Pre Intuneadmincenter Devices Windows Aerislabwin11pc1.png
  ![](./evidence/Lab03%2001%20Pre%20Intuneadmincenter%20Devices%20Windows%20Aerislabwin11pc1.png)
- Lab03 02 Pre Intuneadmincenter Devices Windows Aerislabwin11pc1.png
  ![](./evidence/Lab03%2002%20Pre%20Intuneadmincenter%20Devices%20Windows%20Aerislabwin11pc1.png)
- Lab03 03 Pre ChangeAerislabwin11pc1 failed.png
  ![](./evidence/Lab03%2003%20Pre%20ChangeAerislabwin11pc1%20failed.png)

---

### Step 2 — Create Entra employee identity (beta)
Purpose: create a realistic employee identity to associate with enrollment and later “Primary user / employee ownership” reasoning.  
Actions (high level):
- Entra admin center: create user beta
Evidence:
- Lab03 04 Pre Entraadmincenter User Newuser .png  
  ![](./evidence/Lab03%2004%20Pre%20Entraadmincenter%20User%20Newuser%20.png)
- Lab03 05 Pre Entraadmincenter User Newuser Beta.png  
  ![](./evidence/Lab03%2005%20Pre%20Entraadmincenter%20User%20Newuser%20Beta.png)
- Lab03 06 Pre Entraadmincenter User Newuser Beta completed.png  
  ![](./evidence/Lab03%2006%20Pre%20Entraadmincenter%20User%20Newuser%20Beta%20completed.png)
- Lab03 06 Pre Entraadmincenter User Newuser Beta overview.png  
  ![](./evidence/Lab03%2006%20Pre%20Entraadmincenter%20User%20Newuser%20Beta%20overview.png)

---

### Step 3 — Make beta usable: fix Usage location + assign license
Purpose: ensure beta can actually sign in and participate in management workflows (real production prerequisite).  
Actions (high level):
- Microsoft 365 admin center: check license state
- Set Usage location to Canada (required for some license assignment)
- Assign required license(s)
Evidence:
- Lab03 07 Pre MS365admincenter BetaLicenses Check.png  
  ![](./evidence/Lab03%2007%20Pre%20MS365admincenter%20BetaLicenses%20Check.png)
- Lab03 07 Pre MS365admincenter AddLicenses Beta assgin.png  
  ![](./evidence/Lab03%2007%20Pre%20MS365admincenter%20AddLicenses%20Beta%20assgin.png)
- Lab03 07 Pre MS365admincenter UserBeta LocationCanada and Licensesasgin.png  
  ![](./evidence/Lab03%2007%20Pre%20MS365admincenter%20UserBeta%20LocationCanada%20and%20Licensesasgin.png)

---

### Step 4 — Troubleshooting signal: verify join state (AzureAdJoined)
Purpose: confirm the device join state signal used to explain why certain device controls may be unavailable (e.g., primary user change).  
Actions (high level):
- Run join check command and capture result
Evidence:
- Lab03 11 cmdrunasadmin check azureadjoin.png  
  ![](./evidence/Lab03%2011%20cmdrunasadmin%20check%20azureadjoin.png)
- Lab03 12 azureadjoin no.png  
  ![](./evidence/Lab03%2012%20azureadjoin%20no.png)

Optional cleanup evidence (if used):
- Lab03 13 DetachOldConnection.png  
  ![](./evidence/Lab03%2013%20DetachOldConnection.png)
- Lab03 14 DetachOldConnection restart.png  
  ![](./evidence/Lab03%2014%20DetachOldConnection%20restart.png)

---

### Step 5 — Create local Standard user (beta) on Windows (employee simulation)
Purpose: simulate a corporate endpoint where IT has admin control and the employee has standard user privileges.  
Actions (high level):
- Windows 11 Settings → Accounts → Other users → Add account
- Create local user beta as Standard user
Evidence:
- Lab03 26 setting account otheruser add.png  
  ![](./evidence/Lab03%2026%20setting%20account%20otheruser%20add.png)
- Lab03 27 addstandarduser not MSaccount.png  
  ![](./evidence/Lab03%2027%20addstandarduser%20not%20MSaccount.png)
- Lab03 28 addstandarduser not MSaccount.png  
  ![](./evidence/Lab03%2028%20addstandarduser%20not%20MSaccount.png)
- Lab03 29 addstandarduser.png  
  ![](./evidence/Lab03%2029%20addstandarduser.png)
- Lab03 29 addstandarduser completed.png  
  ![](./evidence/Lab03%2029%20addstandarduser%20completed.png)

---

### Step 6 — Enforce least privilege: remove beta from local Administrators + validate final membership
Purpose: ensure the employee account is not accidentally admin, and produce a clean, auditable proof chain.  
Trigger/Symptom:
- “Standard user” could elevate/run admin actions → indicates beta might be in local Administrators.
Resolution (what was changed):
- Remove `AzureAD\Beta` from local Administrators group.
Post-check (verification):
- Confirm `AzureAD\Beta` not in Administrators; confirm current session identity and group membership.
Evidence:
- Lab03 30 found Beta under admingroup.png  
  ![](./evidence/Lab03%2030%20found%20Beta%20under%20admingroup.png)
- Lab03 31 delete beta from admingroup.png  
  ![](./evidence/Lab03%2031%20delete%20beta%20from%20admingroup.png)
- Lab03 32 Beta is stduser.png  
  ![](./evidence/Lab03%2032%20Beta%20is%20stduser.png)
- Lab03 33 Beta is stduser.png  
  ![](./evidence/Lab03%2033%20Beta%20is%20stduser.png)

---

## Outcome
- Entra employee identity **beta** created and made usable (Usage location set + license assigned).
- Join-state troubleshooting signal captured (AzureAdJoined = NO at the time of check).
- Local **Standard user beta** created on the Windows endpoint.
- Least privilege enforced: `AzureAD\Beta` removed from local Administrators and final membership validated with command evidence.

---

## Notes / Follow-up (optional)
- Some OS security controls are policy-managed and do not reliably demonstrate admin vs standard privilege differences; local group membership is used as authoritative evidence.
- Next step: build Compliance policy (Lab04/Level 4) and validate device state transitions (Compliant → Noncompliant → Compliant).
