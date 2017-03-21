# User Membership Removed

When a user is removed from a company, that user should also be removed from the specified company in the MDM provider.

## Delete User

```javascript--airwatch

DELETE https://airwatch.com/api/system/users/{userId}

```

This endpoint deletes the the user from the MDM provider.

### HTTP Request

`DELETE http://mdm.com/api/user/{userId}`

### Request Parameters

Parameter | Description
--------- | -----------
user_id | The MDM User ID.
