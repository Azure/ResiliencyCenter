# Create a service group

Azure Service Groups offer a flexible way to organize and manage resources across subscriptions and resource groups, parallel to any existing Azure resource hierarchy. They're ideal for scenarios requiring cross-boundary grouping, minimal permissions, and aggregations of data across resources. These features empower teams to create tailored resource collections that align with operational, organizational, or persona-based needs.

Some of the key capabilities of service groups are:

- **Multiple Hierarchies**: Service Groups enable scenarios where the resources can be grouped in different views for multiple purposes. The same resources can be connected to many different service groups allowing different customer personas and scenarios to be created and used. Customers can create many different views that support how they organize their resources.
- **Flexible Membership**: Service Groups allow resources from different subscriptions to be grouped together, providing a unified view and management capabilities. 
- **Low Privilege Management**: Service Groups are designed to operate with minimal permissions, ensuring that users can manage resources without needing excessive access rights.

[Learn more about Service Groups](https://learn.microsoft.com/azure/governance/service-groups/overview)

## Steps to create a service group to model your application

1. Log in to the Azure portal.
2. Search for Service Groups in the portal search bar.
3. Select + Add Service Group to start creating a new group.
4. Fill in the required information:
5. Service Group ID: Enter a unique identifier for your service group. This ID is used for all commands and references to the group within Azure and cannot be changed after creation. Note: The root service group is automatically created using the Microsoft Entra ID as its identifier. For other service groups, provide a unique ID specific to your needs.
6. Display Name: Optionally, enter a display name for the service group. This name appears in the Azure portal and can be updated at any time.
7. Select the Parent Service Group:
8. If you are unsure which parent to select, choose the Root Service Group. This group's ID matches your tenant's ID, in the format Microsoft.Management/serviceGroups[tenantId].
9. Click Next to proceed.
10. Review your settings in the Review tab, then select Create to finalise the service group.

## Adding members to the service group

After creating a service group, you can add resources as members. To add members, you must have the Microsoft.Relationship/ServiceGroupMember/write permission on the source resource and the Microsoft.ServiceGroup Contributor role on the target service group.

1. Navigate to the service group you have created and click the Members tab.
2. Select Add members, then choose the Resources option. This opens the resource selection pane.
3. Use filters (such as subscription, resource group, tags, or resource types) to find and select the relevant resources.
4. After selecting the required resources, submit your selection. You can monitor the addition process through notifications, and the newly added members will appear in the Members page.

## Next steps

[Assign goals to service group](./Goals%20and%20recommendations/AssignGoals.md)
