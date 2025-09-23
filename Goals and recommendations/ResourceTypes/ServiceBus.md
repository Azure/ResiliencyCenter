# Azure Service Bus Zone Resiliency

All Service Bus tiers support [availability zones](https://learn.microsoft.com/azure/reliability/availability-zones-overview), providing fault-isolated locations within the same Azure region. Service Bus manages three copies of the messaging store (1 primary and 2 secondary). Service Bus keeps all three copies in sync for data and management operations. If the primary copy fails, one of the secondary copies is promoted to primary with no perceived downtime. If applications see transient disconnects from Service Bus, the [retry logic](https://learn.microsoft.com/azure/architecture/best-practices/retry-service-specific#service-bus) in the SDK automatically reconnects to Service Bus.

When you use availability zones, **both metadata and data (messages)** are replicated across data centers in the availability zone.

> [!NOTE]
> The availability zones support is only available in [Azure regions](https://learn.microsoft.com/azure/reliability/availability-zones-region-support) where availability zones are present.

When you create a namespace, the support for availability zones (if available in the selected region) is automatically enabled for the namespace. There's no extra cost for using this feature and you can't disable or enable this feature after namespace creation.

> [!NOTE]
> Previously it was required to set the property `zoneRedundant` to `true` to enable availability zones, however this behavior has changed to enable availability zones by default. Existing namespaces are being migrated to availability zones where possible, and the property `zoneRedundant` is being deprecated. The property `zoneRedundant` might still show as `false`, even when availability zones has been enabled.
> Existing namespaces that are being migrated:
> - Currently does not have availability zones enabled.
> - The [region supports availability zones](https://learn.microsoft.com/azure/reliability/availability-zones-region-support).
> - The region has sufficient availability zone capacity.