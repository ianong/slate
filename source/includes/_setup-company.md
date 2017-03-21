# Setup the Company

In order for the devices to work, the company has to setup all the tokens for the Apple Deployment Program. This includes setting up the following:

* APNs (Apple Push Notification service)
* DEP (Device Enrolment Program)
* VPP (Volume Purchase Program)

## Get APNs PLIST

```javascript--airwatch
1. Initiate APNs PLIST creation

GET https://airwatch.com/api/system/groups/{id}/apns?force={force}

Response Body:
{ 
  "AppleId" : "Text value", 
  "CertificateSigningRequestBlobId" : 2, 
  "UploadedCertificateBlobId" : 3, 
  "IssuedCertificateId" : 4, 
  "id" : 1
}

2. Download APNs PLIST

GET https://airwatch.com/api/mam/blobs/downloadblob/{blobId}

Response Body:
File Data
```

In order to manage Apple devices, the company will need an Apple Push Notification service (APNs) certificate. This API will get the PLIST certificate request from the MDM provider.

### HTTP Request

`GET http://mdm.com/api/apns`

### Request Parameters

Parameter | Description
--------- | ------- | -----------
company_id | The MDM Company ID.

### Response Parameters

File data

## Upload APNs PEM certificate 

```javascript--airwatch
1. Upload PEM certificate

POST https://airwatch.com/api/mam/blobs/uploadblob?filename={filename}&organizationgroupid={organizationgroupid}&moduleType={moduleType}

Request Body:
File Data

Response Body:
{ 
  "Value" : 1
}

2. Setup APNs needs

POST https://airwatch.com/api/system/groups/{id}/apns

Request Body:
{ 
  "AppleId" : "Text value", 
  "CertificateSigningRequestBlobId" : 2,
  "UploadedCertificateBlobId" : 3, 
  "IssuedCertificateId" : 4, 
  "Renew" : true, 
  "CertificatePassword" : "Text value", 
  "id" : 1 
}
```

To complete the APNs certificate, the push certificate downloaded from Apple should be uploaded to the MDM provider. This API will upload the Apple-issued PEM to the MDM provider.

### HTTP Request

`POST http://mdm.com/api/apns`

### Request Parameters

Parameter | Description
--------- | -----------
company_id | The MDM Company ID.
file | The PEM file from Apple.

## Get DEP PEM certificate

A public key from the MDM provider is required to obtain the encrypted Authentication Token file from Apple. This API will get the public key from the MDM provider.

### HTTP Request

`GET http://mdm.com/api/dep`

### Request Parameters

Parameter | Description
--------- | -----------
company_id | The MDM Company ID.

### Response Parameters

File data


## Upload DEP token

To complete the DEP setup, the encrypted Authentication Token provided by Apple needs to be uploaded to the MDM provider. This API will upload the DEP PEM token to the MDM provider

### HTTP Request

`POST http://mdm.com/api/apns`

### Request Parameters

Parameter | Description
--------- | -----------
company_id | The MDM Company ID.
file | The PEM file from Apple.

## Upload VPP sToken

To add a VPP License Account, the Authentication Token from the Apple VPP account must be uploaded to the MDM provider. This API will upload the token to be able to manage VPP licenses.

### HTTP Request

`POST http://mdm.com/api/vpp`

### Request Parameters

Parameter | Description
--------- | -----------
company_id | The MDM Company ID.
file | The VPP token file from Apple.