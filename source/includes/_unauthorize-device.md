# Unauthorize Device

To unassociate the device from the user and remove all applications of the user from the device, the device must be unassigned to the user by logging out from the device.

## Unssign Device to User

```javascript--airwatch
1. Get Device ID

GET https://airwatch.com/api/mdm/devices?searchby=SerialNumber&id={device_serial_number}

Response Body:
{ 
  "id" : 1123
}

2. Assign Device to User

PATCH https://airwatch.com/api/mdm/devices/{deviceId}/enrollmentuser/{userId}

{userId} will be the Default Staging User's ID.
```

This endpoint will unassign the device from the specified user.

### HTTP Request

`DELETE http://mdm.com/api/devices/{device_serial_number}/user/{user_id}`

### Request Parameters

Parameter | Description
--------- | ------- | -----------
device_serial_number | The Device's Serial Number.
user_id | The MDM User ID.
