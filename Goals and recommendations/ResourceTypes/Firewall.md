# Azure Firewall Zone Resiliency

It's recommended to configure availability zones during initial deployment. However, you can reconfigure them after deployment if:

- The firewall is deployed in a virtual network (not supported in secured virtual hubs).
- The region supports availability zones.
- All attached public IP addresses are configured with the same zones.

To reconfigure availability zones:

1. Deallocate the firewall:

    ```azurepowershell
    $azfw = Get-AzFirewall -Name "FW Name" -ResourceGroupName "RG Name"
    $azfw.Deallocate()
    Set-AzFirewall -AzureFirewall $azfw
    ```

2. Update the zone configuration and allocate the firewall:

    ```azurepowershell
    $azfw = Get-AzFirewall -Name "FW Name" -ResourceGroupName "RG Name"
    $vnet = Get-AzVirtualNetwork -ResourceGroupName "RG Name" -Name "VNet Name"
    $pip = Get-AzPublicIpAddress -ResourceGroupName "RG Name" -Name "azfwpublicip"
    $mgmtPip = Get-AzPublicIpAddress -ResourceGroupName "RG Name" -Name "mgmtpip"
    $azfw.Allocate($vnet, $pip, $mgmtPip)
    $azfw.Zones = 1, 2, 3
    Set-AzFirewall -AzureFirewall $azfw
    ```

> [!IMPORTANT]
>
> Impact: When an Azure Firewall is deallocated and then reallocated, the firewall can be assigned a different private IP address. Any User Defined Routes (UDRs) that reference the old private IP will stop routing correctly.
>
> Workaround: After reallocation, verify the firewall's private IP and update any UDRs to reference the new address.
>
> Status: Microsoft is investigating a fix to preserve private IP addresses during the deallocate/allocate cycle. See the known issues for details: [Firewall known issues](https://learn.microsoft.com/azure/firewall/firewall-known-issues).