# App Subscription Added

When a company purchases applications from AppDirect Marketplace, a VPP application must be assigned to the company in the MDM.

## Assign VPP application to the company

```javascript--airwatch

1. Sync VPP applications

PUT https://airwatch.com/api/mam/apps/purchased/VppSyncAssets/{organizationGroupId}

Response Body:
{
  "status": "Queued",
  "statusCode": 5
}

2. Get purchased VPP applications

GET https://airwatch.com/api/mam/apps/purchased/search?locationgroupid={organizationGroupId}

Response Body
{
  "Application": [
    {
      "BundleId": "com.appdirect.HarmonyAuthenticator",
      "Id": {
        "Value": 454
      }
    }
  ]
}


3. Create VPP application Smart Group

POST https://airwatch.com/api/mdm/smartgroups

Request Body:
{
  "Name": "Sample Smart Group",
  "CriteriaType": "UserDevice",
  "ManagedByOrganizationGroupId": 1000
}

Response Body:
{
  "Value": 800
}

4. Enable Device based assignment

PUT https://airwatch.com/api/mam/apps/purchased/EnableDeviceAssignmentForVppApp/{applicationId}

Response Body:
{
  "status": "Device based assignment successfully enabled for the app.",
  "statusCode": 1
}

5. Get application allocation details

GET https://airwatch.com/api/mam/apps/purchased/{applicationId}

Response Body:
{
  "ManagedBy": 1000,
  "Licenses": {
    "TotalLicenses": 50,
    "OnHold": 0,
    "Allocated": 0,
    "Unallocated": 50,
    "Redeemed": 0,
    "ExternallyRedeemed": 0
  },
  "Assignments": [],
  "Deployment": {
    "AssignmentType": "Auto",
    "RemoveOnUnenroll": true,
    "PreventApplicationBackup": false,
    "UseVPN": false
  }
}

6. Create VPP application allocation

POST https://airwatch.com/api/mam/apps/purchased/{applicationId}/assignment

Request Body:
{
  "AppConfigList": [
    {
      "Key": "deviceId",
      "Type": 1,
      "Value": "{DeviceSerialNumber}"
    }, {
      "Key": "consumerKey",
      "Type": 1,
      "Value": "HP11rzsslR"
    }, {
      "Key": "consumerSecret",
      "Type": 1,
      "Value": "15vicj1dMSsZ2xcO6O2X"
    }
  ],
  "Assignments": [{
    "Allocated": 50,
    "SmartGroupId": 800
  }],
  "Deployment": {
    "AssignmentType": "Auto"
  },
  "SendApplicationConfiguration": true
}

```

This endpoint assigns the specified VPP application to the company.

### HTTP Request

`POST http://mdm.com/api/app-subscription`

### Request Parameters

Parameter | Description
--------- | -----------
comapany_id | The MDM Company ID.
bundle_id | Bundle ID of the iTunes Application. 

### Response Parameters

Parameter | Description
--------- | -----------
id | The MDM Subscription ID.

