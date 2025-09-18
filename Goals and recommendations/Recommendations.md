# Understand Zone Redundancy Recommendations in Resilience Manager

## Overview

Resilience Manager provides zone redundancy (ZR) recommendations to help improve the availability and resiliency of Azure services. This guide explains how to interpret and act on these recommendations across compute, container, data, and networking resources.

---

## Compute Resources

### Virtual Machines

- **Recommendation**: Use Availability Zones or convert to VMSS.
- **Evaluation Logic**:
  - Checks zone alignment of VM, public IPs, and attached disks.
- **Redeployment/Downtime**: Yes, in most cases.

### Virtual Machine Scale Sets (VMSS)

- **Recommendation**: Deploy across 3+ zones with SKU capacity >= 2.
- **Evaluation Logic**:
  - Checks zone distribution and SKU capacity.
- **Redeployment/Downtime**: Yes

### App Services

- **Recommendation**: Use zone-supported App Service Plan or App Service Environment (ASE).
- **Evaluation Logic**:
  - Checks zone redundancy property.
- **Redeployment/Downtime**: Yes for unsupported SKUs

---

## Container Resources

### Azure Kubernetes Service (AKS)

- **Recommendation**: Use zone-redundant agent pools.
- **Evaluation Logic**:
  - Checks agent pool distribution across zones.
- **Redeployment/Downtime**: Yes

### Azure Container Registry

- **Recommendation**: Use Premium SKU.
- **Evaluation Logic**:
  - Checks SKU type.
- **Redeployment/Downtime**: No

---

## Data Services

### Azure SQL Database

- **Recommendation**: Enable zone redundancy.
- **Evaluation Logic**:
  - Checks zone redundancy property.
- **Redeployment/Downtime**: Brief disconnect

### Azure SQL Managed Instance

- **Recommendation**: Enable zone redundancy.
- **Evaluation Logic**:
  - Checks zone redundancy property.
- **Redeployment/Downtime**: Brief disconnect

### Cosmos DB

- **Recommendation**: Enable ZR for multi-region accounts.
- **Evaluation Logic**:
  - Checks write-enabled replicas.
- **Redeployment/Downtime**: Minor if any

### PostgreSQL

- **Recommendation**: Enable HA with zone redundancy.
- **Evaluation Logic**:
  - Checks HA mode property.
- **Redeployment/Downtime**: Yes

### MySQL

- **Recommendation**: Enable HA with zone redundancy.
- **Evaluation Logic**:
  - Checks HA mode property.
- **Redeployment/Downtime**: Yes

### Redis Cache

- **Recommendation**: Enable zone redundancy.
- **Evaluation Logic**:
  - Checks zonal allocation policy.
- **Redeployment/Downtime**: Yes for unsupported SKUs

---

## Storage, Messaging, and Networking

### Storage Account

- **Recommendation**: Enable zone redundancy.
- **Evaluation Logic**:
  - Checks for ZRS configuration.
- **Redeployment/Downtime**: Yes in some cases

### Service Bus

- **ZR Status**: Yes (default)
- **Action**: No changes needed

### Load Balancer

- **ZR Status**: Yes (Standard SKU)
- **Action**: No changes needed

### Application Gateway

- **ZR Status**: Yes (V2 SKU)
- **Action**: No changes needed

### IP Address

- **ZR Status**: Yes (soon)
- **Action**: No changes needed

### Azure Firewall

- **Recommendation**: Deploy across multiple AZs.
- **Evaluation Logic**:
  - Checks AZ deployment.
- **Redeployment/Downtime**: Yes

### ExpressRoute

- **Recommendation**: Implement Site Resiliency.
- **Evaluation Logic**:
  - Checks SKU suffix.
- **Redeployment/Downtime**: Yes, managed by product team
