# App Assignment Removed

When an application is unentitled from a user, the application must also be unassigned from the user in the MDM.

## Unentitle User from the Application

```javascript--airwatch

1. Unassign VPP application from Smart Group

DELETE https://airwatch.com/api/mam/apps/purchased/{appId}/smartgroups/{smartGroupId}

2. Delete Smart Group

DELETE https://airwatch.com/api/mdm/smartgroups/{smartGroupId}

```

This endpoint unentitles the user from an application.

### HTTP Request

`DELETE http://mdm.com/api/app-subscription/{subscription_id}/app-assignment/{user_id}`

### Request Body

Parameter | Description
--------- | -----------
subscription_id | The MDM Subscription ID.
user_id | The MDM User ID.

