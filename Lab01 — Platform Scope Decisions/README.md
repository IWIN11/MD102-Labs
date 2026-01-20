# Lab 01 — Platform Scope Decisions (Apple / Android)

## Purpose
Document platform enrollment decisions for this MD-102 lab environment to ensure the lab remains reproducible, low-risk, and aligned with tenant/device constraints.

## Decision Summary
- **Windows enrollment** is the primary scope and has been completed (see Lab 02).
- **Apple (iOS/iPadOS/macOS)** enrollment is **not performed in this iteration** due to device compatibility and enterprise ownership constraints.
- **Android enrollment** is considered optional; it will be added only if it can be executed with a clear BYOD boundary (Work Profile) and minimal impact to the personal device.

## Apple Enrollment Decision (Out of scope for this iteration)

### Constraint 1 — Test device OS compatibility
- Available Apple test device: **iPad mini 4**
- Current OS version: **iPadOS 15.8.5**
- Result: The device cannot install/run **Intune Company Portal** required for enrollment in this lab setup.

### Constraint 2 — APNs certificate ownership model (enterprise practice)
Managing iOS/macOS devices in Intune requires an **Apple MDM Push Certificate (APNs)**. In enterprise environments, the APNs certificate is typically created and renewed using an **organization-controlled Apple ID** to ensure continuity for annual renewal and ownership transfer.

### Conclusion
Apple enrollment is excluded from this iteration to avoid:
- non-reproducible results caused by legacy device limitations, and
- binding an APNs certificate lifecycle to a personal Apple ID.

## Android Enrollment Decision (Conditional)

### Preferred BYOD boundary
If Android enrollment is added, it will follow **Android Enterprise — Work Profile** to keep corporate management and apps isolated from personal data.

### Data boundary note
The lab will not require linking personal Canada/China phone identities. Enrollment uses a dedicated **Microsoft 365 test account** and is scoped to the Work Profile container.

## Evidence / References
- Environment readiness and tenant capability boundaries:  
  [00-Environment/00-ENV-SETUP.md](../00-Environment/00-ENV-SETUP.md)

- Windows enrollment evidence (primary platform):  
  https://github.com/IWIN11/MD102-Labs/tree/main/Lab02%20%E2%80%94%20Windows%20Enrollment%20(User-driven%20via%20Company%20Portal)
