# Lab03 — Primary User Fix Path + Standard User Validation

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

### Step 01 — Pre-check: Intune device list baseline (Primary user not editable on PC1)
**Purpose:** Capture the baseline state in Intune before any changes, and document the initial issue: **PC1’s Primary user could not be edited**, which does not match typical enterprise operational needs.  
**Evidence:** Lab03_01–Lab03_03

### Step 02 — Validate permissions: Intune admin role still cannot edit Primary user
**Purpose:** Confirm whether assigning Intune administrator permissions to the Aeris Lab account resolves the issue. Result: **Primary user on PC1 remained non-editable**, indicating the blocker is not solely RBAC/role assignment.  
**Evidence:** Lab03_11–Lab03_13

### Step 03 — Device state check on PC1: AzureADJoined = No
**Purpose:** Verify PC1’s join state to identify why user assignment actions are blocked. Observation: **AzureADJoined = No**, suggesting the device is not properly joined/registered in Entra ID for expected identity-bound management behavior.  
**Evidence:** Lab03_14–Lab03_15

### Step 04 — Create Beta user in Entra ID
**Purpose:** Create a dedicated test user for controlled enrollment and role/permission validation.  
**Evidence:** Lab03_04–Lab03_07

### Step 05 — Fix licensing: Usage location + license assignment (Beta)
**Purpose:** Ensure Beta can be successfully licensed by setting **Usage location**, then completing the license assignment flow (resolving “invalid usage location” / assignment blockers).  
**Evidence:** Lab03_08–Lab03_10

### Step 06 — Detach old connection and join device to Entra ID using Beta
**Purpose:** Remove the previous linkage as needed, complete **Entra ID join** using Beta, and confirm the device reports **AzureADJoined = Yes**.  
**Evidence:** Lab03_16–Lab03_23

### Step 07 — Company Portal sign-in and Intune validation
**Purpose:** Sign in to Company Portal with Beta and validate the device is successfully enrolled and visible in Intune (device list + device details).  
**Evidence:** Lab03_24–Lab03_29

### Step 08 — Add a local standard user (non-Microsoft account)
**Purpose:** Create a local (non-cloud) standard user account to support controlled local access and to test standard-user operational scenarios on a managed endpoint.  
**Evidence:** Lab03_30–Lab03_34

### Step 09 — Fix local privilege: remove Beta from Administrators; confirm standard
**Purpose:** Enforce least privilege by removing Beta from the local **Administrators** group and confirming Beta operates as a **standard user** on the managed endpoint.  
**Evidence:** Lab03_35–Lab03_38


---

## Outcome
- Beta user created, licensed, and used to join device to Entra ID.
- Device appears in Intune and shows expected presence after Company Portal sign-in.
- Local privilege verified: Beta is standard user (not in Administrators).

