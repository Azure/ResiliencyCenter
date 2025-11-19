# Role Based Access Control (RBAC) Requirements for Resiliency preview scenarios

The following table lists the RBAC roles that can be leveraged by users to achieve specific resiliency management requirements.

## Service Group Management

| Scenario | Roles |
|----------|--------------------------|
| Create service group and add/remove member resources in the service group | 1. Microsoft.Relationship/ServiceGroupMember/write access on the resources that are being added to the service group <br> 2. Service Group contributor |

## Goals and Recommendations

| Scenario | Roles |
|----------|--------------------------|
| Assign goals to service group | 1.  Service Group contributor <br>2.  Microsoft.Relationship/ServiceGroupMember/read access to the resources under the service group |
| View counts of resilient, non-resilient, not evaluated resources under the service group (after goal assignment) | 1.  Service Group reader |
| View list of resources under the service group and their zone resiliency configuration status (after goal assignment) | 1.  Service Group reader <br>2.  Reader access to the resources within the service group |
| Include/Exclude/Attest resources in the service group (after goal assignment) | 1.  Service Group contributor |
| Rediscover resources in the service group | 1.  Service Group contributor <br>2.  Microsoft.Relationship/ServiceGroupMember/read access to the required resources under the service group |
| View Service Group level recommendations | 1.  Service Group reader |
| View resource level recommendations for resources under the Service Group (after goal assignment) | 1.  Service Group reader <br>2.  Reader access to the resources for which recommendations need to be viewed |
| Postpone/Dismiss recommendations | 1.  Contributor access to the resources for which recommendations need to be dismissed/postponed |

## Recovery Plan

| Scenario | Roles |
|----------|--------------------------|
| Create and Execute Recovery Plan | 1. Recovery Plan Contributor on the Service Group. <br> 2. In addition, there is vault level RBAC that is needed by Recovery Plan MSI to perform Azure Site Recovery related operations. <br> 3.  User will also need contributor access to resources in case they need to enable zone redundancy for those resources before proceeding with plan creation and execution. |

## Drills

| Scenario | Roles |
|----------|--------------------------|
| Create/Update/Execute Drills |  1. **SG Drill Contributor** on the **Service Group** <br> 2. **Drill Assets Contributor** on the **subscription** associated with Automation Account and Chaos experiment <br> 3. **Drill Resource Fault Contributor** on the **resources** on which fault injection should be performed.