# Lab03 — Primary User Fix Path + Standard User Validation
Evidence gallery: see [Evidence Index](./evidence-index.md)

**Type:** LAB  
**Date:** 2026-01-23  
**Status:** Done  

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

### Step 01 — Pre-check: Intune device list baseline
Purpose: capture baseline state before changes.  
Evidence: Lab03_01–Lab03_02

### Step 02 — Create Beta user in Entra ID
Purpose: create a dedicated test user for enrollment and role validation.  
Evidence: Lab03_04–Lab03_07

### Step 03 — Fix licensing: Usage location + license assignment (Beta)
Purpose: ensure the user can be licensed; resolve “invalid usage location” / assignment flow.  
Evidence: Lab03_07 (license related) + Lab03_08–Lab03_10 + Lab03_24–Lab03_25

### Step 04 — Join device to Entra ID using Beta (and recover from old connection if needed)
Purpose: complete Entra join and confirm AzureADJoined state.  
Evidence: Lab03_11–Lab03_20

### Step 05 — Company Portal sign-in and Intune validation
Purpose: validate the enrolled device shows up in Intune portal/device list.  
Evidence: Lab03_21–Lab03_23

### Step 06 — Add local standard user (not Microsoft account)
Purpose: set up local user for standard permission testing.  
Evidence: Lab03_26–Lab03_29

### Step 07 — Fix local privilege: remove Beta from Administrators; confirm standard
Purpose: prove Beta is NOT local admin and is standard user.  
Evidence: Lab03_30–Lab03_33

---

## Outcome
- Beta user created, licensed, and used to join device to Entra ID.
- Device appears in Intune and shows expected presence after Company Portal sign-in.
- Local privilege verified: Beta is standard user (not in Administrators).

