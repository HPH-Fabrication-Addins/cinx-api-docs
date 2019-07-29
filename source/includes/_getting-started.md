# Getting Started

## PING Server
### API – PING Server

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.pingCinx()
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
  "response": {
    "status_code": 200,
    "message": "OK",
    "method": "Validation->ping",
    "uri": "ping",
    "format": "json",
    "start_time": 1563128596.686,
    "total_time": 0.027906894683838,
    "record_count": 1,
    "total_count": 0
  },
  "rows": [
    {
      "status": 200,
      "message": "CINX: API Ping Response: Ok"
    }
  ]
}
```

This request can be used to test the availability of the CINX API.

URL Pattern:

**{api path}/{api_version}/ping**

URL Samples:

`https://api.cinx.com/2.0/ping`

## User Auth
### API – GET User Subscriptions/Authorizations (Orgs and Applications)

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getSubscriptions()
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "User->getUserSubscriptions",
        "uri": "2.0/subs",
        "format": "json",
        "start_time": 1564084416.873,
        "total_time": 0.43612098693848,
        "record_count": 2,
        "total_count": 0
    },
    "rows": [
        {
            "cinx_api_token": "dfed7d88-adf8-5356-8029-fe061c93d0fe",
            "user": {
                "cinx_user_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
                "first_name": "Will",
                "middle_name": "",
                "last_name": "Stone",
                "suffix": ""
            },
            "org": {
                "cinx_org_id": "org-0001-4030",
                "name": "WTS Mechanical -DEV"
            },
            "subscription": {
                "status_code": 200,
                "status_message": "OK",
                "status_message_reason": null,
                "start_date": "2017-10-20",
                "end_date": "2025-11-19",
                "apps": [
                    {
                        "cinx_app_guid": "3780a6b903937022c5649f5cd35ed5a7",
                        "cinx_app_id": "2494df92-e855-5563-826c-05907f9cca22",
                        "name": "QuoteSoft Legacy",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "QuoteSoft"
                    },
                    {
                        "cinx_app_guid": "3780a6b903937022c5649f5cd391744e",
                        "cinx_app_id": "b9667d0e-685c-5f9e-add7-dc19ab843453",
                        "name": "Integrated Price Updates",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "My Private Catalog"
                    },
                    {
                        "cinx_app_guid": "3c5184a7b4b25bd44ff900cbe5000e65",
                        "cinx_app_id": "f1ab96c5-bbf9-5f8a-8974-b39dfef17f45",
                        "name": "Estimation Legacy",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "Viewpoint Estimation"
                    },
                    {
                        "cinx_app_guid": "3780a6b903937022c5649f5cd38f85a8",
                        "cinx_app_id": "5b914d1f-a4f7-5d69-a829-c8e453351a0d",
                        "name": "TSI Mechanical",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "TSI"
                    },
                    {
                        "cinx_app_guid": "3780a6b903937022c5649f5cd391744e",
                        "cinx_app_id": "d217f7b7-ef49-5ae1-adf3-3765160725a4",
                        "name": "Integrated Price Updates",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "Southland"
                    },
                    {
                        "cinx_app_guid": "viewpoint-erp-app",
                        "cinx_app_id": "808eb448-962c-564b-9e34-c560dc4fdbb9",
                        "name": "Kirlin / Viewpoint ERP",
                        "type": "INTEGRATION : ERP",
                        "data_source": "My Private Catalog"
                    }
                ]
            }
        },
        {
            "cinx_api_token": "fde79d15-0a1b-5d51-a665-7b87ed341711",
            "user": {
                "cinx_user_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
                "first_name": "Will",
                "middle_name": "",
                "last_name": "Stone",
                "suffix": ""
            },
            "org": {
                "cinx_org_id": "org-0001-4032",
                "name": "Alpine Mechanical"
            },
            "subscription": {
                "status_code": 401,
                "status_message": "Unauthorized",
                "status_message_reason": "Subscription expired on [2017-11-22]",
                "start_date": "2017-10-23",
                "end_date": "2017-11-22",
                "apps": [
                    {
                        "cinx_app_guid": "3780a6b903937022c5649f5cd38f72f1",
                        "cinx_app_id": "d50e720b-684b-52a7-ba2e-22211b0488ba",
                        "name": "QuoteSoft",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "HPH Catalog"
                    },
                    {
                        "cinx_app_guid": "timberline-erp-app",
                        "cinx_app_id": "88bd791c-d684-5196-814c-e98c63670a8b",
                        "name": "Sage / Timberline",
                        "type": "INTEGRATION : ERP",
                        "data_source": "My Private Catalog"
                    },
                    {
                        "cinx_app_guid": "308-599736-f129d818-ca871bfb90-350af7",
                        "cinx_app_id": "f5e9f665-1239-5a1e-8c01-7afda01d6e3d",
                        "name": "Autodesk Fabrication Add-In",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "My Private Catalog"
                    }
                ]
            }
        }
    ]
}
```

This request will be used to get the applications/subscriptions that the user is authorized to access.  The response will contain information required to make additional API calls.

URL Pattern: 

**{api path}/{api version}/subs**

URL Sample: 

`https://api.cinx.com/2.0/subs`
