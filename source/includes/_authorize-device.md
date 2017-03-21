# Authorize Device

For the user's assigned applications to get pushed down to the device, the device must be assigned to the user by logging in to the device.

## Assign Device to User

```javascript--airwatch
1. Get Device ID

GET https://airwatch.com/api/mdm/devices?searchby=SerialNumber&id={device_serial_number}

Response Body:
{ 
  "id" : 1123
}

2. Assign Device to User

PATCH https://airwatch.com/api/mdm/devices/{deviceId}/enrollmentuser/{userId}

```

This endpoint will assign the device to the specified user.

### HTTP Request

`POST http://mdm.com/api/devices/{device_serial_number}/user/{user_id}`

### Request Parameters

Parameter | Description
--------- | ------- | -----------
device_serial_number | The Device's Serial Number.
user_id | The MDM User ID.
