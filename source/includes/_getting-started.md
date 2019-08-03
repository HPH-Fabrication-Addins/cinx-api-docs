# Getting Started

## PING Server
### API Endpoint - PING CINX API Server

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
  "response": {},
  "rows": [
    {
      "status": 200,
      "message": "CINX: API Ping Response: Ok"
    }
  ]
}
```
`GET`

This endpoint can be used to test the availability of the CINX API.

URL Pattern: **{api path}/{api_version}/ping**

URL Samples: `https://api.cinx.com/2.0/ping`


## User Auth
### API Endpoint - User Subscription/Authorization

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
    "response": {},
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
                        "cinx_app_guid": "3780a6b903937022c5649f5cd391744e",
                        "cinx_app_id": "d217f7b7-ef49-5ae1-adf3-3765160725a4",
                        "name": "Integrated Price Updates",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "Southland"
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
`GET`

This endpoint will be used to get the applications/subscriptions that the user is authorized to access.  The response will also contain account status and CINX Ids required to make additional API calls.

**Notes**

  - A User can be associated with multiple companies (orgs).  In this case, their will be multiple **Rows** in the response.
  - If a User account is expired the **status_code** will be **401**.
  - For addtional information about working with this response see this page [Auth Response](#auth-response)

URL Pattern: **{api path}/{api version}/subs**

URL Sample: `https://api.cinx.com/2.0/subs`
