# Getting Started

## REST API
### ReST API

The CINX platform offers programmatic access to read and write data using ReST web services and standard HTTP verbs.


**Authentication & Headers**

HTTP Basic Authentication over HTTPS is used to control access to CINX platform resources.

With each API call, you’ll need to set request headers, including a CINX User’s User Name and Password.


**Account Authorization**

CINX accounts are subscription based and have expiration dates.  Accounts with expired subscriptions will not have access to CINX data.


**Production Endpoint**

The production endpoint for the CINX API is:

**https://api.cinx.com/**


**API Response Formatting – Standard/JSON**

All CINX API responses use a standardized format.  By default a JSON formatted response is provided.  Please see below if you prefer XML.

The **“response” object** will contain meta data about the server’s response to the request.

The **“rows” array** will contain the query results.


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
  "rows": [
    {
  ]
}



**API Response Formatting – XML**

To receive an XML response, please add the following parameter to the url:

**format=xml**


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

cinxApi.pingCinx()
    .then(function(response) {
        console.log(response);
    });
```

> The above command returns JSON structured like this:

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

**{api path}/ping**

URL Samples:

**http://api.cinx.com/ping**

**http://api.cinx.com/ping?format=xml**



## User Auth
### API – GET User Subscriptions/Authorizations (Orgs and Applications)

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');

cinxApi.getSubscriptions()
    .then(function(response) {
        console.log(response);
    });
```

> The above command returns JSON structured like this:

```json
 {
        "response": {
          "status_code": 200,
          "message": "OK",
          "method": "User->getUserSubscriptions",
          "uri": "sub/user/subscriptions",
          "format": "json",
          "start_time": 1562338517.204,
          "total_time": 0.31632900238037,
          "record_count": 2,
          "total_count": 0
        }
        "rows": [
          "org": {
            "names": {
              "primary": "Ratkoceri Engineering-LIVE",
              "alternate": null,
              "short": null,
              "previous": null
            },
            "cinx_id": {
              "type": "ORG",
              "domain": "orgs",
              "id": "org-0000-8247"
            }
          },
          "access_status": {
            "code": 200,
            "message": "OK",
            "reason": null
          },
          "start_date": "2015-06-18 13:04:53Z",
          "end_date": "2022-07-18 13:04:53Z",
          "apps": [
            {
              "name": "HPH Plumbing/Mechanical",
              "id": "e82d126d-53c7-b455-8e26-cc0a4a2b6762",
              "type": "DATA-SOURCE",
              "sub_type": "CATALOG",
              "access": "PUBLIC",
              "app_cdoc": "couchdb://apps/dab29b19c69e2703849cd5010a183fdd",
              "attributes": [
                
              ],
              "cost": 0,
              "is_paid": "1",
              "users": [
                
              ],
              "notify": [
                
              ],
              "labor_app": false,
              "logo": "https://cdn.cinx.com/assets/apps/org-0000-0001_logo_1.png",
              "description": "HPH Plumbing and Mechanical Material Catalog",
              "data_source": "couchdb://apps/dab29b19c69e2703849cd5010a183fdd",
              "data_source_name": "HPH Plumbing/Mechanical",
              "catalog_source": "couchdb://apps/dab29b19c69e2703849cd5010a183fdd"
            }
          ],
          "cinx_id": {
            "type": "SUBSCRIPTION",
            "domain": "subscriptions",
            "id": "47895223-a950-a206-ef6c-fb489667eeb3"
          },
          "user": {
            "names": {
              "first": "Burim",
              "middle": "",
              "last": "Ratkoceri",
              "suffix": ""
            },
            "cinx_id": {
              "type": "USER",
              "domain": "users",
              "id": "911d0a71-c650-51dc-5a28-d35d1229397b"
            },
            "joomla_id": "10396",
            "orgs": [
              {
                "org_cdoc": "couchdb://orgs/org-0000-8247",
                "role": "Administrator",
                "permissions": [
                  
                ],
                "permission_extensions": [
                  
                ]
              },
              {
                "org_cdoc": "couchdb://orgs/org-0000-7068",
                "role": "User",
                "permissions": [
                  
                ],
                "permission_extensions": [
                  
                ]
              }
            ]
          }
        ]
      }
```

This request will be used to get the applications/subscriptions that the user is authorized to access.  The response will contain information required to make additional API calls.

URL Pattern: 

**{api path}/sub/user/subscriptions**

URL Sample: 

**https://api.cinx.com/sub/user/subscriptions**



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

**Org:** contains two objects labeled **Names** and **CINX Id.**  The **CINX Id** will contain the Unique Id to identify the Org on the CINX Platform.

**Access Status:** defines the org’s subscription status which controls access to the API.

**Start Date:** lists the date the CINX subscription was established.

**End Date:** provides the scheduled expiration date for the subscription.

**Apps:** an array of applications that the org currently subscribes to and can access using the API.  The structure of an app object is governed by its **Type.**  Current CINX App types include **Data-Source** (catalogs of content), **Integration** (interactions with other software systems), and **Website** (CINX web site features).

**CINX Id:** contains the Unique Id for the org’s subscription.

**User:** provides basic information about the user and his/her CINX Unique Id.

The following sections contain important information about using the API and the CINX Unique Ids that will be required for making some API calls. 

**Is the subscription active?**

You will first need to verify that the subscription is active.  This is done by checking the **access_status** object of the response. If the subscription is active the response will have the following information:


"access_status": {
    "code": 200,
    "message": "OK",
    "reason": null
}

If the subscription has expired the response will have the following information:


"access_status": {
    "code": 401,
    "message": Unauthorized",
    "reason": "Subscription expired on [2014-08-03]"
}

**Does the subscription response contain a B2B (data integration) application?**

A B2B CINX application allows programmatic access to content on the CINX Platform.   To determine if an Org has a B2B app in their subscription, you will need to query the apps array for an  app_cdoc that has this value:  "couchdb://apps/2d4dde95cc7d1a3d8e830036ff126f60" (which is a CINX Platform constant).  Once this is located please hold the value of the id: field.  The string shown in this field is required to make additional API calls to retrieve item and project information.

<img src='images/subscription7.jpg'/>

In the above screenshot, the necessary **id** value is:  **050ba80b-832b-89cc-8197-b2a1261a408c**

**Does the subscription response contain multiple B2B (data integration) applications?**

It is possible for an org to have multiple B2B applications.  This is allowed to let CINX link to different data sources.  A data source is a catalog of content.  One org may have access to multiple content catalogs.

It is recommended that B2B application with an org’s Private Catalog data source be used when working with the public API for a specific org.

Similar to the B2B app cdoc, the My Private Catalog data source will have a static/constant that can be used when querying the API’s Subscription response.  Inside a B2B app there will be a **data_source** field.  The value in this field for the My Private Catalog will be **couchdb://apps/a6502d78d800a4cd3cc052562500033a.**  This value is a CINX Platform constant.

<img src='images/subscription8.jpg' />

It is not recommended to use the **data_source_name** field as the name text may change in the future.

**Does the subscription response contain Integration (Import-Export) application?**

A CINX Import-Export application provides API access to formats required for integration with external applications.  This will be used in the API calls to pull price updates for a Your company catalog.

<img src='images/subscription9.jpg' />

The necessary **id** value in this screenshot is:  **0d2b4b77-d706-e215-13f2-207c7e4aaee7**

**What is the user’s CINX Unique Id?**

The CINX User Unique Id (GUID) will be required by some API requests.  These requests will generally be ones in which new information is created or existing content is updated.  The user will then be identified as the “last modified by”.




