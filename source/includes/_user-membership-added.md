# User Membership Added

When a user is added to a company, that user should also be created in the MDM provider under the sepcified company

## Create User

```javascript--airwatch

POST https://airwatch.com/api/system/users/adduser

Request Body:
{
  "UserName": "user123",
  "Password": "password",
  "FirstName": "First",
  "LastName": "Last",
  "Status": "True",
  "Email": "first.last@email.com",
  "SecurityType": 2,
  "LocationGroupId": 1000,
  "Role": "Basic Access",
  "MessageType": "None"
}

Response Body:
{
  "Value": 17
}

```

This endpoint creates a user in the MDM and assigns it to the specified company.

### HTTP Request

`POST http://mdm.com/api/user`

### Request Parameters

Parameter | Description
--------- | -----------
comapany_id | The MDM Company ID.
user_id | Marketplace ID of the user. To protect information, the Marketplace user ID will be used as a name the user in the MDM. The value will be set the user's username or name.

### Response Parameters

Parameter | Description
--------- | -----------
id | The MDM User ID.

