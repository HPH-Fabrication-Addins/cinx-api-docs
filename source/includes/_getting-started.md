# Getting Started

## REST API
### ReST API

> JSON formatted response

```json
{
  "start_time": 1411574224.8083,
  "response": {
    "status_code": 200,
    "message": "OK",
    "record_count": 1,
    "server_response_time": 0,
    "total_elapsed_time": 0.02492094039917,
    "total_count": 0
  },
  "rows": []
}
```

> XML formatted response

```xml
<cinx_api>
  <start_time>1414436492.2267</start_time>
  <response>
    <status_code>200</status_code>
    <message>OK</message>
    <record_count>2</record_count>
    <server_response_time>0</server_response_time>
    <total_elapsed_time>0.013047933578491</total_elapsed_time>
    <total_count>0</total_count>
  </response>
  <rows>
    <row> 
    </row>
  </rows>
</cinx_api> 
```

The CINX platform offers programmatic access to read and write data using ReST web services and standard HTTP verbs.

**Authentication & Headers**

HTTP Basic Authentication over HTTPS is used to control access to CINX platform resources.

With each API call, you’ll need to set request headers, including a CINX User’s User Name and Password.

**Account Authorization**

CINX accounts are subscription based and have expiration dates.  Accounts with expired subscriptions will not have access to CINX data.  

**Production Endpoint**

The production endpoint for the CINX API is:

**https://api.cinx.com/**

**API Version**

The CINX API is versioned.  This documentation supports version 2.0 and higher.  The API version will be added to the API endpoint and become part of the base URL.

https://api.cinx.com/2.0/

**API Token**

The CINX API uses an API Token when submitting web service requests.  The CINX API Token is retrieved from the subscription web service API response.  A company (org) that has a CINX account must also be configured to permit API access before the API Token will be returned in the subscription API Response.  The API token is valid for the duration of a company’s CINX subscription.  The API Token will be added to the base URL following the API Version number.

https://api.cinx.com/2.0/{api_token_value}/

**API Response Formatting – Standard/JSON**

All CINX API responses use a standardized format.  By default a JSON formatted response is provided.  Please see below if you prefer XML.

The **“response” object** will contain meta data about the server’s response to the request.

The **“rows” array** will contain the query results.

**API Response Formatting – XML**

To receive an XML response, please add the following parameter to the url:

**format=xml**

**Result Rows - Paging**

For many HTTP GET requests you can use URL parameters to define the number of rows returned in the response.  Valid input parameters are:

**start={number}**

**limit={number}**

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


## Auth Response
### Working with the GET User Subscriptions/Authorizations API Response

The Subscriptions/Authorizations API response will provide the necessary information to make subsequent API requests.

Please keep the following CINX Platform attributes in mind as you begin to work with the Subscriptions response:

  - A User may be associated with more than one Org (multiple Orgs in the CINX subscription result)
  - An Org can subscribe to multiple catalogs of content
  - An Org might have multiple subscriptions to a single App  (the data for the App coming from different sources) (multiple instances of the same App within a single Org in the CINX subscription result)
  - A User may use a CINX Addin for multiple partner applications on the same computer
  - Objects in the CINX Platform are assigned Unique Ids that will be required API URL elements

The JSON response uses the following structure:

<img src='images/subscription6.jpg'/>

Each **Row** array of the response will correspond to an Org to which the user is a member and will contain the following components:

**CINX API Token:** Token that will be used in API calls to access and  the org’s data.

**User:** provides basic information about the user and his/her CINX Unique Id.

**Org:** basic information that can be used to identify a registered CINX org.  

**Subscription:** defines the org’s subscription status which controls access to the API.

**Subscription [Apps]:** an array of applications that the org currently subscribes to and can access using the API.  The structure of an app object is governed by its **Type.**  Current CINX App types include **Data-Source** (catalogs of content) and **Integration** (interactions with other software systems).  The contents of this array will only be used if your app needs to access content of a specific CINX Data Source in a pre-defined data format.  For example, price updates for an estimating system database.

The following sections contain important information about using the API and the CINX Unique Ids that will be required for making some API calls. 

**Does the subscription response contain a CINX API Token?**

A CINX API Token is required to grant programmatic access to content on the CINX Platform.  The API Token will appear at the top of the response object in a field named **cinx_api_token.**  If there is not a value in this field, then access to content will be denied.  A user can contact HPH, to have the necessary account modification made to allow for the generation of the token.

<img src='images/subscription10.jpg'/>

**Is the subscription active?**

API-based access to CINX will also be controlled by the org’s subscription status.  You will need to verify that the subscription is active.  This is done by checking the **subscription** object of the response.

If the subscription is active the response will have the following information:

<img src='images/subscription11.jpg'/>

**What is the user’s CINX Unique Id?**

The CINX User Unique Id (GUID) will be required by some API requests.  These requests will generally be ones in which new information is created or existing content is updated.  The user will then be identified as the “last modified by”.

<img src='images/subscription12.jpg'/>

**Will you need to access price updates or other item content stored in a CINX Catalog in a specific pre-defined format?**

The Apps array within the Subscription object in the response will provide a list of applications to which the org has subscribed.  

<img src='images/subscription13.jpg'/>

The **cinx_app_guid** is a constant value that is used to identify an application within the CINX platform.  If you are a software company that requires data access to a specific catalog of content, a CINX app will be created and you will be provided the **cinx_app_guid** so that you can query the response for instances of your app.

The **cinx_app_id** is a unique value that links a subscribing CINX org to your application.  This value will be required when you are making API calls to access content.

The **data_source** name value will define the source of the item content that will be used to create content update files (price updates).  For more information about the relationship between and app and a data source, please review the CINX Applications and Data Source page.






