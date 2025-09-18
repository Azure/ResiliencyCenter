# Azure Database for PostgreSQL Flexible Server Zone Resiliency

This article describes how to enable or disable high availability (HA) on your Azure Database for PostgreSQL flexible server by using the Azure portal or the Azure CLI. The information applies whether you're using flexible servers in the same zone or using a zone-redundant deployment model.

## Enable high availability for existing servers

### Portal

1. In the [Azure portal](https://portal.azure.com/), select your Azure Database for PostgreSQL flexible server.

2. On the left menu, in the **Settings** section, select **High availability**.

3. If high availability isn't enabled, the **Enable high availability** checkbox is cleared. Also, the **High availability status** value is **Not enabled**.

4. Select the **Enable high availability** checkbox to enable the option. Once selected, the **Zone redundant** option is automatically enabled by default for regions that have support for [availability zones](https://learn.microsoft.com/azure/postgresql/flexible-server/overview#azure-regions), as it is the recommended configuration.

5. For **High availability mode**, the **Same zone** and **Zone redundant** options appear:

    * To create the standby server in the same availability zone as the primary server, select **Same zone**.

    * To choose zone redundancy, select **Zone redundant**. Then, for **Standby availability zone**, choose the other availability zones in which you want to deploy your standby server.

      > [!NOTE]
      > If the region in which your server is created doesn't support high availability with zone redundancy, the **Zone redundant** option is unavailable.

6. When everything is configured according to your needs, select **Save** to apply the changes.

7. A dialog shows the cost increase associated with the deployment of the standby server. If you decide to proceed, select **Enable high availability**.

8. A deployment starts. When it finishes, a notification shows that you successfully enabled high availability.

### CLI

You can enable high availability in an existing server via the [az postgres flexible-server update](https://learn.microsoft.com/cli/azure/postgres/flexible-server#az-postgres-flexible-server-update) command.

To enable high availability so that the standby server is deployed in the same zone as the primary server, use this command:

```azurecli-interactive
az postgres flexible-server update \
  --resource-group <resource_group> \
  --name <server> \
  --high-availability SameZone
```

To enable high availability with the standby server deployed in a different zone from the primary server's zone, and if you want the zone to be automatically selected, use this command:

```azurecli-interactive
az postgres flexible-server update \
  --resource-group <resource_group> \
  --name <server> \
  --high-availability ZoneRedundant
```

Optionally, you can select the availability zone in which to deploy the standby server. Use this command:

```azurecli-interactive
az postgres flexible-server update \
  --resource-group <resource_group> \
  --name <server> \
  --high-availability ZoneRedundant \
  --standby-zone <standby_zone>
```

If you're enabling high availability with zone redundancy, and the zone specified for standby matches the zone of the primary, you get this error:

```output
Your server is in availability zone <server>. The zone of the server cannot be same as the standby zone.
```

If you're enabling high availability with zone redundancy, and the zone specified for standby isn't available in that region, you get this error:

```output
Code: InvalidParameterValue
Message: Invalid value given for parameter StandbyAvailabilityZone,availabilityZone. Specify a valid parameter value.
```

If you're enabling high availability with zone redundancy, and the region doesn't have multiple availability zones, you get this error:

```output
This region is single availability zone. Zone redundant high availability is not supported in a single availability zone region.
```

If high availability is enabled in one mode, and you try to enable it again by specifying a different mode, you get this error:

```output
Code: InvalidParameterValue
Message: Invalid value given for parameter Cannot switch Properties.HighAvailability.Mode directly from SameZone to ZoneRedundant. Please disable HA and then enable HA.. Specify a valid parameter value.
```
