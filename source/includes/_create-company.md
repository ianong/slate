# Create Company

When a company is created in AppDirect Marketplace, and the company is flagged to support "On-Device Sales Automation", a representation of that company needs to exist in the MDM.

## Create MDM Company

```javascript--airwatch
POST https://airwatch.com/api/system/groups/{parentOrganizationGroupId}

Request Body:
{
  "Name": "Sample Company Name",
  "LocationGroupType": "Customer"
}

Response Body:
{
  "Value": 1000
}

```

This endpoint creates a representation of a Marketplace company in the MDM.

### HTTP Request

`POST http://mdm.com/api/companies`

### Request Parameters

Parameter | Description
--------- | -----------
name | Name of the company.

### Response Parameters

Parameter | Description
--------- | -----------
id | The MDM Company ID.
api_credentials | [Optional] Credentials used to make API calls in behalf of the company. This parameter may be broken down into username and password for APIs that support Basic Auth. Furthermore, this parameter may not be provided as part of the company create API.

## Add Apple App Restriction Profile

```javascript--airwatch
POST https://airwatch.com/api/v2/mdm/profiles/platforms/apple/create

Request Body:
{
  "General": {
    "Name": "SystemAppRestriction",
    "Description": "System App Restriction",
    "AssignedSmartGroups": [ 1234 ], 
    "AssignmentType": "Auto",
    "IsActive": true,
    "IsManaged": true,
    "ManagedLocationGroupID": 1000
  },
  "Restrictions": {
    "AllowAutomaticSyncWhileRoaming": true,
    "AllowBackup": true,
    "AllowBluetoothSettingsModification": true,
    "AllowChangesToCellularDataUsageForApps": true,
    "AllowChangesToFindMyFriends": true,
    "AllowDiagnosticDataToBeSentToApple": true,
    "AllowDocumentSync": true,
    "AllowEraseAllContentsandSettings": true,
    "AllowExplicitMusicAndPodcasts": true,
    "AllowFaceTime": true,
    "AllowFingerPrintForUnlock": true,
    "AllowGameCenter": true,
    "AllowHandoff": true,
    "AllowManualProfileInstallation": true,
    "AllowMultiplayerGaming": true,
    "AllowNews": true,
    "AllowOpeningManagedAppDocumentsInUnmanagedApps": true,
    "AllowOpeningUnManagedAppDocumentsInManagedApps": true
    "ShowNotificationsViewOnLockScreen": true,
    "ShowTodayViewOnLockScreen": true,
    "ShowUserGeneratedContentInSiri": true,
    "HideApps": [
      "com.apple.AppStore",
      "com.apple.compass",
      "com.apple.facetime",
      "com.apple.gamecenter"
    ]
  }
}

Response Body:
{
  "Value": 52
}
```

This endpoint creates an Apple App Restriction Profile for the company. This will allow restriction of apps and settings on all devices managed by the company. 

### HTTP Request

`POST http://mdm.com/api/profiles/apple`

### Request Parameters

Parameter | Description
--------- | -----------
comapany_id | ID of the company to add the profile.
restriction_settings | The Apple restriction settings. t should represent the <a href="https://developer.apple.com/library/content/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010206-CH1-SW13">Restrictions Payload</a> as defined by Apple.

### Response Parameters

Parameter | Description
--------- | -----------
id | The MDM Profile ID.