# Project Transmittals

## Project Transmittal Definition
### CINX Object Definition - Project Transmittal

A CINX project transmittal consists of two components.  The transmittal cover page provides identification and submission information.  Also included on the cover page is a listing of documents included in the package. 

The second section contains the actual documents that are being submitted.

Today, transmittals are often referred to as submittal packages.

The CINX web application has functionality to help a contractor create and manage transmittals. User's can select documents from the project's submittals and add them to a transmittal. Each transmittal can have a recipients list which will be used when the transmittal is electronically submitted.

Currently, the API supports working with documents defined as transmittals within CINX.

**Supported API Services**

 - [Get a List of Project Transmittals](#get-project-transmittals)
 - [Get a Transmittal](#get-transmittal)

## Get Project Transmittals
### API Endpoint – Get a Project's Transmittals

<aside class="warning">
BETA: This call is in a beta state and therefore subject to potential change. It has been published to allow partners to provide input.  
</aside>

```json
{
 "response": {},
 "rows": [{
  "cinx_guid": "0229f4de-65bf-531a-be48-d1aebc372f07",
  "number": "TRAN-030220",
  "revision": "1",
  "name": "TRAN-030220",
  "description": "Valve Spec Sheets",
  "workflow_status": "SUBMITTED",
  "project_number": "PRJ-2019-13",
  "project_name": "PRJ-2019-13",
  "date_due": "2020-03-12",
  "date_submitted": "2020-03-02",
  "date_created": "2020-03-02",
  "date_modified": "2020-03-02",
  "document": {
    "mime_type": "application/pdf",
    "url": "http://5f062a51145e77536a19-9611898491c752c3179a567caf577a77.r87.cf1.rackcdn.com/TRAN_030220__20200302160457.pdf",
    "submittal_count": 7
 }}]
}
```

`GET`

This endpoint will be used to get a listing of a project's transmittals.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/transmittals**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/transmittals`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
workflow | Limits results to a specific workflow status. | CREATED, APPROVED FOR SUBMISSION, SUBMITTED
number | Limits results to a specified transmittal number. | {transmittal_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 10 will be used. | Integer

## Get Transmittal
### API Endpoint – Get a Project Transmittal 

<aside class="warning">
BETA: This call is in a beta state and therefore subject to potential change. It has been published to allow partners to provide input.  
</aside>

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "2dc90e17-bbdc-59fa-8845-ee80bdfdec74",
    "locked": "0",
    "number": "TRAN-200301A",
    "revision": "1",
    "name": "TRAN-200301A",
    "description": "Valve Spec Sheets",
    "workflow_status": "SUBMITTED",
    "delivery_type": "CINX",
    "remarks": "Please review ASAP.  We need to order these soon.",
    "dates": {
      "created": "2020-03-02",
      "last_modified": "2020-03-02",
      "due": "2020-03-20",
      "submitted": "2020-03-02"
    },
    "project": {
      "guid": "eac76f6c-a988-5b53-a987-58e4bc01bd66",
      "name": "PRJ-2019-13",
      "number": "PRJ-2019-13"
    },
    "document": {
      "cinx_guid": "c3ea0b9b-5e6d-5caa-bcb3-4a42344bc9d1",
      "url": "http://5f062a51145e77536a19-9611898491c752c3179a567caf577a77.r87.cf1.rackcdn.com/TRAN_200301A__20200302210151.pdf",
      "mime_type": "application/pdf",
      "submittal_count": 2
    },
    "submittals": [{
        "cinx_guid": "d894dd54-c489-57ba-a62b-98590ca0d2ea",
        "revision": "1",
        "description": "Autogeneration File",
        "url": "http://cdn.dev.cinx.biz/submittals/org-0001-4030/5bd72c4ede78090bbd5e9c8f.pdf",
        "mime_type": "application/pdf",
        "date_created": "2020-03-02",
        "creator": {
          "guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
          "name": "Will Stone",
          "email": "willstone@cinx.com"
        }
      },
      {
        "cinx_guid": "4e3ba9ff-d189-51a7-9ad2-511c4c058413",
        "revision": "1",
        "description": "Autogeneration File",
        "url": "http://cdn.dev.cinx.biz/submittals/org-0001-4030/5bd9b461de78090dac7d35b9.pdf",
        "mime_type": "application/pdf",
        "date_created": "2020-03-02",
        "creator": {
          "guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
          "name": "Will Stone",
          "email": "willstone@cinx.com"
        }
      }
    ],
    "participants": [{
      "cinx_guid": "d89f99cd-99da-50d8-94e7-91314d95ec86",
      "name": "David McPhaul",
      "email": "dmcphaul@hphguide.com",
      "phone": "6034440820",
      "org_name": "HPH",
      "org_type": "ENGINEER"
    }],
    "attributes": []
  }]
}
```

`GET`

This endpoint will be used to get the details of a specific project transmittal.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/transmittal/{transmittal_guid}/**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/transmittal/cd204035-368e-5677-838b-17d7506c4523`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml