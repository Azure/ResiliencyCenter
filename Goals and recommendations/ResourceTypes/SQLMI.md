# Azure SQL Managed Instance Zone Resiliency

You can enable zone redundancy for an existing SQL managed instance by using the Azure portal, PowerShell, Azure CLI, and REST API.

## Enable zone redundancy for an existing instance 

### Azure portal

To update your zone redundancy configuration for an existing SQL managed instance by using the Azure portal, follow these steps.

1. Go to your [SQL managed instance](https://portal.azure.com/#view/HubsExtension/BrowseResource/resourceType/Microsoft.Sql%2FmanagedInstances) resource in the Azure portal.
2. On the **Compute + storage** pane:

   1. To enable zone redundancy, first ensure the **Backup storage redundancy** under **Backup** is set to `Zone-redundant` or `Geo-zone-redundant`. If it's not already, choose your new backup storage redundancy option and apply your settings. Wait for the operation to complete, and then refresh your page before enabling zone redundancy.
   2. Under **Compute Hardware**, use the **Zone redundancy** toggle to either enable or disable zone redundancy.

### PowerShell

To update an existing SQL managed instance to be zone-redundant by using PowerShell, use the `-ZoneRedundant` switch when using the [Set-AzSqlInstance](/powershell/module/az.sql/set-azsqlinstance) command. For a full PowerShell sample, review [Use PowerShell to create a SQL managed instance](scripts/create-configure-managed-instance-powershell.md).

Omit `-ZoneRedundant` if you want to disable zone redundancy for your existing SQL managed instance.

### Azure CLI

To update an existing SQL managed instance to be zone-redundant by using the Azure CLI, set the `--zone-redundant` parameter to `true` when using the [az sql mi update](/cli/azure/sql/mi#az-sql-mi-update) command. For a full Azure CLI sample, review [Create an Azure SQL Managed Instance using the Azure CLI](scripts/create-configure-managed-instance-cli.md).

Set `--zone-redundant` to `false` if you want to disable zone redundancy for your existing SQL managed instance.

### REST API

To update an existing SQL managed instance to be zone-redundant by using the REST API, set the `zoneRedundant` parameter to `true` when using the [Managed Instances - Update](/rest/api/sql/managed-instances/update) command.

Set `zoneRedundant` to `false` if you want to disable zone redundancy for your existing SQL managed instance.

---

## Check zone redundancy

You can check the current zone redundancy setting for your SQL managed instance by using the Azure portal, PowerShell, Azure CLI, and the REST API.

### Azure portal

To check the zone redundancy configuration for an existing SQL managed instance by using the Azure portal, follow these steps.

1. Go to your [SQL managed instance](https://portal.azure.com/#view/HubsExtension/BrowseResource/resourceType/Microsoft.Sql%2FmanagedInstances) resource in the Azure portal.
2. On the **Compute + storage** page under settings, check the **Zone redundancy** toggle in the **Compute Hardware** section.

### PowerShell

To check the zone redundancy configuration for an existing SQL managed instance, validate the existence, or absence, of the `Zone-redundant` switch when using the [Get-AzSqlInstance](/powershell/module/az.sql/get-azsqlinstance) PowerShell command.

If the `Zone-redundant` switch is visible, zone redundancy is enabled.

### Azure CLI

To check the zone redundancy configuration for an existing SQL managed instance, validate what the `--zone-redundant` parameter is set to when using the [az sql mi show](/cli/azure/sql/mi#az-sql-mi-show) PowerShell command.

Zone redundancy is enabled if `--zone-redundant` is set to `true`.

### REST API

To check the zone redundancy configuration for an existing SQL managed instance, validate what the`zoneRedundant` parameter is set to when using the [Managed Instances - Get](/rest/api/sql/managed-instances/get) REST API command

Zone redundancy is enabled if `zoneRedundant` is set to `true`.

---

## Supported regions

Review [zone redundancy availability by region](region-availability.md#zone-redundancy) for Azure SQL Managed Instance.