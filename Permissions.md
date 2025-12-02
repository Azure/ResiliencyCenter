# Permissions Required for Recovery Plans

## Introduction
This document outlines the permissions required to create and execute Recovery Plans in Azure Resiliency. Ensure that the necessary roles and access levels are assigned before proceeding.

## Required Permissions

### Service Group Access

1. **Recovery Contributor**: Required on the Service Group.
2. **Reader Access**: Required on the subscription or resource group that is a member of the Service Group. This ensures that underlying resources can be discovered.

### Virtual Machine (VM) Recovery Plans

For Recovery Plans containing VMs, the following additional permissions are required:

1. **Service Group Contributor**: Required on the Service Group.
2. **Microsoft.Relationship/ServiceGroupMember/write**: Required on the linked recovery resource (e.g., VM created during failover) to add the new VM to the Service Group.
3. **Site Recovery Operator**: Required on the Recovery Services vault used by the VM. This permission must be assigned to the managed identity of the Recovery Plan.

### Custom Runbooks

For users utilizing custom runbooks in the Recovery Plan:

1. **Automation Job Operator**: Required on the associated Automation Account.

### Zone Redundancy

1. **Contributor Access**: Required on resources to enable zone redundancy before creating and executing the Recovery Plan.