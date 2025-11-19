# Tutorial: Create and Execute a Recovery Plan for Zonal Resiliency

## Pre-requisites

Ensure that all the pre-requisites in [this article](../Prerequisites.md) are met before proceeding.

## Introduction

The Recovery Plan enables efficient and seamless recovery by orchestrating recovery across multiple resources within an application. It allows you to:

- Define the order of recovery for resources within the application.
- Perform readiness checks to detect any drift in your applications, increasing the chances of successful recovery.

> [!NOTE]
> The Recovery Plan is an orchestrator and does not protect individual resources. To protect resources, configure Azure Site Recovery for VMs or Highly Available (HA) solutions for other resources.

The scope of the Recovery Plan is limited to **zonal recovery**. Regional recovery is not supported at this time.

## Recovery Plan Setup

### Steps to Set Up a Recovery Plan

1. **Create the Recovery Plan**

2. **Configure the Plan**

3. **Finalize the Plan**

### Step 1: Create the Recovery Plan

1. Navigate to the **Service Group**.

2. Select the **Recovery Plans** option.

   ![Screenshot for Recovery Plan option in Service Group](../img/01-Service%20Group%20View.png)

3. Click **Create recovery plan**.

   ![Screenshot for Create recovery plan option](../img/02-Create%20Recovery%20Plan.png)

4. Provide details such as the Plan name and description.

   ![Screenshot for Basics tab during recovery plan creation](../img/03-Basics%20RP%20creation.png)

5. [Optional] Select the managed identity to use. By default, the **System Managed Identity** is used. Click **Review + create**.

   ![Screenshot for Management tab during recovery plan creation](../img/04-Management%20RP%20creation.png)

6. Review the details and click **Create**.

> [!NOTE]
> To create a Recovery Plan within a Service Group, you need either the **Azure Resilience Management Recovery Contributor** or **Azure Resilience Management Recovery Administrator** role.

### Step 2: Configure the Plan

Once the Recovery Plan is created, configure it by:

- Adding resources from Service Groups.
- Managing resource protection.
- Defining the startup order of resources after recovery.
- Running readiness checks.

#### Steps to Configure the Plan

1. Navigate to the created Recovery Plan. The plan will be in the **Under Edit** state.

2. Click the **Configure Plan** tab.

   ![Screenshot for Configure Plan button](../img/05-Configure%20Plan%20button.png)

3. Click **Manage resource protection**.

   ![Screenshot for Configure Plan Tab](../img/06-Configure%20Plan%20Tab.png)

4. Review the resources in the Service Group:

   ![Screenshot for Manage Resources Protection](../img/07-Manage%20Resources%20Protection.png)

   - **Protection Solution**: Solutions like Azure Site Recovery or Zone-redundant storage.
   - **Protection Status**: Indicates whether the resource is protected.
   - **Active Location**: The region or zone where the resource is currently active.
   - **Recovery Location**: The disaster recovery or high availability location.
   - **Inclusion States**: Resources can be marked as Included, Highly Available, Excluded, or Needs Attention.

5. Click **Next** to define the **Start Group Order** for resource recovery.

   ![Screenshot for Group Order Tab](../img/08-Group%20order%20tab.png)

6. Click **Next** to configure **Group Actions** for automating actions at the group level.

7. Click **Next** to review the plan in the **Review + Update** tab. After reviewing, click **Update**.

   ![Screenshot for Review+update recovery plan](../img/09-Review%20and%20update%20tab.png)

### Step 3: Finalize the Plan

The plan remains in the **Under Edit** state until finalized. To finalize:

1. Ensure no resource is in the **Needs Attention** state. Run readiness checks to resolve issues.

2. Once all resources are ready, finalize the plan.

   ![Screenshot for Finalize recovery plan view](../img/10-Finalize%20recovery%20plan%20tab.png)

After successful finalization, the plan will be in the **Ready** state.

## Create and Order Groups in the Recovery Plan

Groups in the Recovery Plan define the order of resource recovery. By default, a **Default Group** is created, and Azure Site Recovery-protected VMs are added to it. You can:

- Create additional groups.
- Move resources between groups.
- Define the recovery sequence.

### Steps to Manage Groups

1. Click **Manage Groups**.

   ![Screenshot for Manage recovery plan group](../img/11-Manage%20recovery%20plan%20group.png)

2. Use the **Manage Group** context pane to:

   - Create new groups.
   - Rename groups.
   - Change the order of groups.

   ![Screenshot for Manage recovery plan group context pane](../img/12-Manage%20group%20context.png)

3. Move resources between groups by clicking the three dots next to the resource.

   ![Screenshot for moving resources across group](../img/14-Moving%20resources.png)

## Add Group Actions

Automate group-level actions by adding Azure Automation Runbooks as pre-scripts and post-scripts. If automation isn't possible, include manual steps. During failover, pre- and post-scripts run automatically, while manual actions pause the failover job until resumed.

### Steps to Add Group Actions

1. Navigate to **Configure Plan > Manage Resource Protection**.

2. Go to the **Group Action** tab and click the three dots for the group.

3. Add a script or manual step as needed.

   ![Screenshot for group action view](../img/15-Group%20action.png)

4. To add automated actions, click **Add Script** and configure the runbook scripts. Set a timeout (default: 60 minutes).

   ![Screenshot for adding pre and post script view](../img/16-pre%20post%20script.png)

5. To add manual steps, click **Add Manual Step**.

   ![Screenshot for adding manual actions view](../img/17-manual%20actions.png)

> [!NOTE]
> The Recovery Plan's Managed Identity requires the **Automation Job Operator** role to run automation scripts.

## Inclusion States

Resources in the Recovery Plan can have the following inclusion states:

- **Included**: Resources protected by Azure Site Recovery or custom scripts.
- **Highly Available**: Resources with high availability configurations.
- **Excluded**: Resources not included in the Recovery Plan.
- **Needs Attention**: Resources requiring configuration or protection.

> [!IMPORTANT]
> Resources marked as **Needs Attention** must be resolved by either including or excluding them from the plan.

## Plan States

A Recovery Plan can exist in the following states:

- **Under Edit**: The plan is being modified and not finalized.
- **Ready**: The plan is complete and ready for failover operations.
- **Warning**: Resources in the plan require attention.

## Execute Operations

You can execute the following operations from the **Execute** dropdown:

- **Failover**: Perform failover when the plan is in the Ready state.
- **Reprotect**: Reprotect resources after failover.
- **Readiness Checks**: Periodically check the readiness of the plan.

## Supported Resource Types

The following Azure services are supported by the Recovery Plan:

1. Azure VM

2. Azure VMSS

3. Azure SQL DB

4. Azure SQL MI

5. Azure Cosmos DB

6. Azure PostgreSQL-Flexible Server

7. Azure Service Bus

8. Azure Container Registry

9. AKS

10. Azure Storage Account

11. Azure Load Balancer

12. Azure App Gateway

13. Azure IP Address

14. Azure Firewall

15. App Services

16. Express Route

17. Redis Cache

18. MySQL