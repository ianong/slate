# Application Assignment

When an application that was purchased is assigned to a user, the equivalent user in the MDM should also have subscription of that application in the MDM.

## Assign VPP application to the company

```javascript--airwatch



```

This endpoint assigns the specified VPP application to the company.

### HTTP Request

`POST http://mdm.com/api/application/{id}`

### Request Body

Parameter | Description
--------- | -----------
comapany_id | ID of the company to add the VPP application.
bundle_id | iTunes bundle ID of the application.

### Response Body

Parameter | Description
--------- | -----------
id | The MDM Subscription ID.

