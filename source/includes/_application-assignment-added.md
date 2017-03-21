# App Assignment Added

When an application is entitled to a user, the application must also be assigned to the user in the MDM.

## Entitle User to the Application

```javascript--airwatch

1. Update Smart Group Assignments

PUT https://airwatch.com/api/mdm/smartgroups/{smartGroupId}

Request Body:
{
  "Name": "Sample Smart Group",
  "CriteriaType": "UserDevice",
  "ManagedByOrganizationGroupId": 1000,
  "UserAssignments": [
    17
  ]
}

2. Sync Devices

POST https://airwatch.com/api/mdm/devices/{deviceId}/SyncDevice

```

This endpoint entitles the user to an application.

### HTTP Request

`POST http://mdm.com/api/app-subscription/{subscription_id}/app-assignment/{user_id}`

### Request Parameters

Parameter | Description
--------- | -----------
subscription_id | The MDM Subscription ID.
user_id | The MDM User ID.
