# Role Based Access Control (RBAC) Requirements for Resiliency preview scenarios

The following table lists the RBAC roles that can be leveraged by users to achieve specific resiliency management requirements.

| Scenario | Roles |
|----------|--------------------------|
| Create service group and add/remove member resources in the service group | 1. Microsoft.Relationship/ServiceGroupMember/write access on the resources that are being added to the service group <br> 2. Service Group contributor |
| Assign goals to service group | 1.  Service Group contributor <br>2.  Microsoft.Relationship/ServiceGroupMember/read access to the resources under the service group |
| View counts of resilient, non-resilient, not evaluated resources under the service group (after goal assignment) | 1.  Service Group reader |
| View list of resources under the service group and their zone resiliency configuration status (after goal assignment) | 1.  Service Group reader <br>2.  Reader access to the resources within the service group |
| Include/Exclude/Attest resources in the service group (after goal assignment) | 1.  Service Group contributor |
| Rediscover resources in the service group | 1.  Service Group contributor <br>2.  Microsoft.Relationship/ServiceGroupMember/read access to the required resources under the service group |
| View SG level recommendations | 1.  Service Group reader |
| View resource level recommendations for resources under the SG (after goal assignment) | 1.  Service Group reader <br>2.  Reader access to the resources for which recommendations need to be viewed |
| Postpone/Dismiss recommendations | 1.  Contributor access to the resources for which recommendations need to be dismissed/postponed |