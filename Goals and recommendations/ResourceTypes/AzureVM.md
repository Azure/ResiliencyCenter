# Ensuring Zonal Resiliency for Azure VMs and VMSS

## Overview

Zonal resiliency protects workloads from failures within a single availability zone by distributing resources across multiple zones within a region. This guide outlines the recommended steps for customers to configure their Azure VMs and VMSS for zonal resiliency.

---

## Scenario 1: Regional VM (Pre-requisite)

**Action Required**:

- Migrate your VM from a regional configuration to a zonal configuration.
- This requires re-deploying the VM into a zone-pinned setup.

**Why**:

- Regional VMs are vulnerable to zone-level failures. Zonal configuration isolates faults and enables faster recovery.

---

## Scenario 2: Standalone Zonal VM

**Steps to Achieve Zonal Resiliency**:

1. **Attach VM to VMSS Flex**:
   - Use [VMSS Flex](https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-attach-detach-vm) with zone spreading and at least two VM instances in 2 different zones.
2. **Configuration Settings**:
   - Disable strict zone balancing.
   - Enable automatic instance repair using the app-health extension.
3. **For Stateful Applications**:
   - Disable auto-OS upgrade and auto-scaling.
   - Implement application-level replication or use [shared ZRS data disk architecture](https://azure.microsoft.com/en-us/blog/improve-availability-with-zoneredundant-storage-for-azure-disk-storage/).
4. **Recovery Options**:
   - Use Azure Site Recovery (ASR) for cross-zone replication (PowerShell only, for VMs with LRS disks).

---

## Scenario 3: Multi-Zone VM

**Steps to Maintain Zonal Resiliency**:

1. **Attach VM to VMSS Flex**:
   - Use zone spreading with multiple VM instances.
2. **Configuration Settings**:
   - Disable strict zone balancing.
   - Enable automatic instance repair with app-health extension.
3. **For Stateful Applications**:
   - Disable auto-OS upgrade and auto-scaling.
   - Ensure support for application-level replication or shared ZRS data disk architecture.
4. **Recovery Options**:
   - ASR support is available via PowerShell only.

---

## Scenario 4: Regional VMSS (Pre-requisite)

**Action Required**:

- Migrate VMSS from regional to zonal configuration.
- This involves creating new VM instances and deleting existing ones.
- Recommended only for stateless applications.

---

## Scenario 5: Multi-Zone VMSS

**Steps to Maintain Zonal Resiliency**:

1. **Enable App-Health Extension**:
   - Monitor availability of applications and VM instances.
2. **Enable Automatic Instance Repairs**:
   - Ensure quick recovery from zonal failures.

---

## Summary Table

| Scenario               | Key Action Steps                                                                 |
|------------------------|----------------------------------------------------------------------------------|
| Regional VM            | Redeploy VM to zonal configuration                                               |
| Standalone Zonal VM    | Attach to VMSS Flex, enable zone spreading, configure app-health and replication |
| Multi-Zone VM          | Validate zone spreading, replication, and repair settings                        |
| Regional VMSS          | Migrate to zonal VMSS (stateless only)                                           |
| Multi-Zone VMSS        | Enable app-health extension and automatic repairs                                |

---
