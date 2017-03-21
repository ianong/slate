# App Subscription Removed

When a company removes applications from AppDirect Marketplace, a VPP application must be unassigned to the company in the MDM.

## Remove VPP application from the company

```javascript--airwatch

1. Update Smart Group Assignments

PUT https://airwatch.com/api/mdm/smartgroups/{smartGroupId}

Request Body:
{
  "Name": "Sample Smart Group",
  "CriteriaType": "UserDevice",
  "ManagedByOrganizationGroupId": 1000,
  "UserAssignments": []
}

2. Sync Devices

POST https://airwatch.com/api/mdm/devices/{deviceId}/SyncDevice

```

This endpoint remove the specified VPP application from the company.

### HTTP Request

`DELETE http://mdm.com/api/app-subscription/{subscription_id}`

### Request Parameters

Parameter | Description
--------- | -----------
subscription_id | The MDM Subscription ID.

