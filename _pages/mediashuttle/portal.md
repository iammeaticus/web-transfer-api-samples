---
layout: page
title: Media Shuttle Portal
permalink: mediashuttle/v1.1/portal
---

## portal/{portalprefix}

```HTTP
GET /1.1/portal/{portalurlprefix}?authToken={authTokenValue}
```
portalurlprefix - The URL prefix portion of the portal’s full URL. For example, for portal testportal.mediashuttle.com, the value of this parameter is testportal.

Sample Response:

```JSON
{
    "name": "Media Shuttle Portal",
    "url": "media-shuttle-portal",
    "maxFile": "2147483",
    "maxFileUnits": "MB",
    "maxStorage": "21474836480",
    "maxStorageUnits": "GB",
    "agent": {
        "name": "portal-server.acme.com"
    },
    "manager": [
      {
        "name": "opsadmin@gmail.com",
        "contact": "555-123-4567"
      }, 
      {
        "name": "opsadmin2@hotmail.com",
        "contact": "E-mail me only if it is urgent"
      }
    ],
    "itSuspended": "false",
    "opSuspended": "false",
    "concurrentTransfers": "3",
    "capability": "FULL",
    "metrics": [
      {
          "name": "totalMembers",
          "value": "4"
      }, 
      {
          "name": "totalTransfers",
          "value": "103"
      }, 
      {
          "name": "avgFileSize",
          "value": "15565457"
      }, 
      {
          "name": "avgTransferRate",
          "value": "70828383"
      }, 
      {
          "name": "senderMembers",
          "value": "0"
      }, 
      {
          "name": "receiverMembers",
          "value": "0"
      }, 
      {
          "name": "transfersPerWeek",
  "value": "2012-10-01T00:00:00.000=14,2012-10- 15T00:00:00.000=74,2012-11-05T00:00:00.000=2,2012-11-12T00:00:00.000=13"
      }, 
      {
          "name": "storageUtilized",
          "value": "18135786040"
      }, 
      {
          "name": "peakStorage",
          "value": "18135786040"
      }, 
      {
          "name": "peakStorageTime", 
          "value": "2012-11-13T20:23:18.726"
      }, 
      {
          "name": "capacityStatus",
          "value": "GREEN"
      }, 
      {
          "name": "daysToExpire",
          "value": "128"
      }
    ],
    "callbackHost": "portal- server.acme.com/signiant_mediashuttle_cloud_connector/spring/rest/cc",
    "createdOn": "2012-09-27T21:40:59.456", "contentDelivery": "USER",
    "roles": [
      {
        "portalId": "aa123f04d-1234-1234-1234-1212121212121", "role": "DELIVER_TO_USERS",
        "roleType": "DELIVER_TO_USERS",
      }
    ], 
}
```

## portal/{portalprefix}/portalInfo

```HTTP
GET /1.1/portal/{portalurlprefix}/portalInfo?authToken={authTokenValue}
```
portalurlprefix - The URL prefix portion of the portal’s full URL. For example, for portal testportal.mediashuttle.com, the value of this parameter is testportal.

Sample Response:

```JSON
{
    "name": "Media Shuttle Portal",
    "url": "media-shuttle-portal",
    "maxFile": "2147483",
    "maxFileUnits": "MB",
    "maxStorage": "119185342464",
    "maxStorageUnits": "GB",
    "itSuspended": "false",
    "opSuspended": "false",
    "concurrentTransfers": "0",
    "capability": "FULL",
    "callbackHost": "portal-
server.acme.com/signiant_mediashuttle_cloud_connector/spring/rest/cc", 
    "createdOn": "2012-08-07T18:48:33.239",
    "contentDelivery": "USER"
}
```

## portal/{portalprefix}/cloudConnectorStatus

```HTTP
GET /1.1/portal/{portalurlprefix}/cloudConnectorStatus?authToken={authTokenValue}
```

Success Response:

```JSON
{
    "result": "SUCCESS",
    "resultCode": "1.0"
}
```

If the IT infrastructure cannot be reached then the following is returned:

```JSON
{
    "result": "FAILURE"
}
```