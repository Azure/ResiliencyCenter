# Public IP Address Zone Resiliency

> [!IMPORTANT]
> We're updating Standard non-zonal IPs to be zone-redundant by default on a region by region basis. This means that in the following regions, all IPs created (except zonal) are zone-redundant.
> Region availability: Central Korea, Central Mexico, Central Canada, Central Poland, Central Israel, Central France, Central Qatar, East Asia, East US 2, East Norway, Italy North, Sweden Central, South Africa North, South Brazil, West Central Germany, West US 2, Central Spain, North Europe, UK South, Australia East, UAE North, Central US, Switzerland North, India Central, East Japan, West Japan, East US, West Europe, South US, North US
> 

Standard SKU Public IPs can be created as non-zonal, zonal, or zone-redundant in [regions that support availability zones](https://learn.microsoft.com/azure/reliability/availability-zones-region-support). Basic SKU Public IPs don't have any zones and are created as non-zonal. Once created, a public IP address can't change its availability zone.

| Value | Behavior |
| --- | --- |
| Non-zonal |  A non-zonal public IP address is placed into a zone for you by Azure and doesn't give a guarantee of redundancy. |
| Zonal  |	 A zonal IP is tied to a specific availability zone, and shares fate with the health of the zone. |
| Zone-redundant	| A zone-redundant IP is created in all zones for a region and can survive any single zone failure. |