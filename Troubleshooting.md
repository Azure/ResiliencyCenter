# Troubleshoot Errors in Resiliency Center

This article contains information about common errors you might encounter while using Resiliency Center.

> [!NOTE]
> This content will be updated throughout the preview period. If you encounter errors not covered here, contact [azresiliencyprivatepreviewsupport@microsoft.com](mailto:azresiliencyprivatepreviewsupport@microsoft.com) with your service group name and steps to reproduce the error.

## Goal assignment errors

### Resource count exceeds maximum limit during goal assignment

**Error message:**

```text
Resource count in the service group exceeds the maximum supported limit of 500
```

**Cause:** This error occurs when you try to assign goals to a service group that contains 500 or more resources, which exceeds the supported scope of Resiliency Center.

**Resolution:**

Remove non-essential memberships from the service group.
    1. Navigate to the service group and select the **Members** tab.
    2. Remove the memberships you don't need.
    3. Try to assign goals again.

> [!IMPORTANT]
> The resource count includes all resources under the service group, including any child service groups, subscriptions, or resource groups. Each resource is counted only once.

## Rediscovery errors

### Resource count exceeds maximum limit during rediscovery

**Error message:**

```text
Resource count in the service group exceeds the maximum supported limit of 500. All existing goal assignment resource associations have been cleaned up.
```

**Cause:** This error occurs when resources are added to the service group (or any child service groups, subscriptions, or resource groups) after goal assignment, causing the number of discovered members to exceed 500. This exceeds the supported scope for Resiliency Center.

**Resolution:**

Remove non-essential memberships from the service group.
    1. Navigate to the service group and select the **Members** tab.
    2. Remove the memberships you don't need.
    3. Trigger [rediscovery](./Goals%20and%20recommendations/ViewResiliencePosture.md#Rediscovering-resources) again.

The error should resolve if the new resource count is less than 500.
