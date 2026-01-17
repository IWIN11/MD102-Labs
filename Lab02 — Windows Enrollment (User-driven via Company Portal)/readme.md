# Lab 02 — Windows Enrollment (User-driven via Company Portal)

**Type:** LAB  
**Date:** 2026-01-16  
**Status:** Done (Enrollment + Intune validation complete)

---

## Goal (Target State)
Enroll a freshly installed **Windows 11 Pro** desktop into **Microsoft Intune** using **user-driven enrollment** (Company Portal), and validate the device appears in:
- **Intune admin center → Devices → All devices** (device list)
- **Intune device details** (Essentials)

---

## Environment
- **Tenant:** Aeris Lab  
- **Tenant domain:** aerislab.onmicrosoft.com  
- **Work account (org account):** aerislab@aerislab.onmicrosoft.com  
- **Device name:** Aeris-lab-win11-pc1  
- **Device type:** Windows 11 Pro desktop (fresh OS install)  
- **Notes:** Ownership expected to show as **Personal** in Intune for BYOD-style user-driven enrollment.

---

## Constraints / Boundaries
- **No Entra ID P1/P2** in this tenant → do not rely on Conditional Access or premium-only automatic enrollment flows.
- Primary approach is **user-driven enrollment** via **Company Portal** + **Access work or school**.

**Proof:** see Evidence Group D (Tenant boundary & MDM user scope).

---

## Deliverables
- A complete evidence set (screenshots) showing:
  1) local admin readiness  
  2) baseline config (time + rename)  
  3) org account connection  
  4) troubleshooting path when Intune list did not show  
  5) Company Portal enrollment flow  
  6) final validation in Intune

**Evidence map:** `evidence-index.md`

---

## Runbook (Step-by-step)

### Step 1 — Verify local admin readiness (endpoint controllability)
**Purpose:** confirm the device is locally controllable and recoverable before enrollment.  
**Evidence:** `lab02_01`–`lab02_03` (Local admin verification)

---

### Step 2 — Baseline config: correct time/date + stable device name
**Purpose:** avoid identity confusion during registration/enrollment and make the asset easy to find in Intune.  
**Actions:**
- Confirm time/date settings  
- Rename PC to `Aeris-lab-win11-pc1` (or confirm it matches)

**Evidence:**  
- `lab02_04` (Time/Date)  
- `lab02_05`–`lab02_06` (Rename PC)

---

### Step 3 — Connect the device to the organization account (user-driven path)
**Purpose:** establish the org account connection that triggers the enrollment path.  
**Actions (high level):**
- Use Windows “Access work or school” / “Connect” flow to add the work account.
- Confirm connected state is present (and that disconnect option exists).

**Evidence:**  
- `lab02_07`–`lab02_12` (Connect verification screens)  
- `lab02_27`–`lab02_28` (Access work or school connected state / account info)  
- `lab02_28_*_Sync` (if applicable)

---

### Step 4 — Troubleshooting: Intune device list not showing immediately
**Trigger/Symptom:** device did not appear in Intune “All devices” after connecting; multiple refresh attempts.  
**Checks performed:**
- Verify device is registered in Entra ID
- Verify MDM user scope setting
- Confirm licensing boundary (no Entra ID P1/P2)

**Evidence:**  
- `lab02_13` (All devices list not showing — troubleshooting)  
- `lab02_14` (Device registered in Entra ID)  
- `lab02_15` (Entra Mobility → MDM user scope = ALL)  
- `lab02_16` (No Entra ID P1/P2 — boundary proof)

---

### Step 5 — Complete enrollment with Company Portal (setup → connect → complete)
**Purpose:** complete the management setup so device becomes manageable by Intune.  
**Actions (high level):**
- Install/open Company Portal
- Sign in with `aerislab@aerislab.onmicrosoft.com`
- Complete “Set up your device” → “Connect to work” steps
- Return to Company Portal to confirm completion

**Evidence:**  
- `lab02_17` (Get Company Portal)  
- `lab02_18` (Log in with lab account)  
- `lab02_19`–`lab02_26` (Set up device flow: account added → connect to work → password → completed → verification)

---

### Step 6 — Validation: device is visible in Intune and shows correct details
**Success criteria:**
- Device appears in **Intune Devices list**
- Device details show expected values (Device name, Ownership, Primary user, Compliance, Last check-in)

**Evidence:**  
- `lab02_29` (Intune list shows Aeris-lab-win11-pc1)  
- `lab02_30` (Intune device details / Essentials)

---

## Outcome
- Windows device `Aeris-lab-win11-pc1` enrolled successfully via user-driven workflow.
- Device is visible in Intune with device details available for management actions and compliance state.

---

## Notes / Follow-up (optional)
- Next improvement: add one compliance policy and one configuration profile, then validate policy sync + compliance evaluation.
- Optional: document expected propagation delay (Entra registration vs Intune enrollment visibility).

