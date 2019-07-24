# Introduction

## App/Sub Model
### CINX Application/Subscription Model Introduction

A CINX customer (organization) has the opportunity to subscribe to different applications available on the platform. An application can be a grouping of pages and functionality on the CINX web site or external applications that consume content from CINX.  Each application on the CINX platform has a unique identifier and a range of fields that define its attributes.  When an organization subscribes to an application a new unique identifier is created to link the application to the subscribing organization.  This application id will be used in API calls to identify and grant access to requested data operations.

<img src='images/subscription1.jpg'/>

## Data Sources
### CINX Data Source Introduction

CINX supports different “catalogs” of content.  Companies subscribing to CINX can have access to multiple catalogs or databases of content.  Here are some common catalogs in CINX:

  - HPH Plumbing/Mechanical catalog
  - MCAA WebLEM
  - PHCC Labor Units 
  
Another catalog that each CINX company can use is a “Private” catalog.  This catalog of content is specific to the subscribing company and can contain material items.  These items can be copied from another catalog on CINX or manually entered/uploaded by the company.

Estimating systems, CAD/BIM software systems, and other software partners that utilize CINX content will also have a separate CINX Catalogs.  This allows each system to have a specific set of items that CINX maintains.

A good way to visualize this concept is to open the Catalog drop-down in the CINX Search app.  Here is a screen shot that shows a company that has access to many catalogs.  Note:  each company’s private catalog will be listed using the company’s name as registered in CINX.
  
<img src='images/subscription2.jpg'/>
  
When working with the CINX API in conjunction with a company’s subscription a catalog is often named Data Source.

## App - Data Sources
### CINX Application and Data Source Introduction

For software partner (external) applications that consume data from CINX there is an important attribute in the CINX subscription that defines which CINX catalog is used to acquire information for data outputs.  This attribute is called a **data source**.
  
Each application subscription in CINX has this attribute.
  
Importantly, a company can subscribe to an application multiple times provided that the data source is different.  For example, a company using an industry estimating system may have CINX produce updates for different locations using different CINX Catalogs (data sources).  One location may want standard list prices from the standard estimating database and another location may want update files to contain net buy prices based on their private catalog of content.

<img src='images/subscription3.jpg'/>
  
**Please note that when working with the CINX Subscription API response each combination of an application and a data source will be listed in separate blocks.**
  
Below is a sample showing an App with its data source

App Name: Viewpoint Estimation

Data Source Name: Viewpoint Estimation

<img src='images/subscription4.jpg'/>

App Name: Viewpoint Estimation

Data Source Name: My Private Catalog

<img src='images/subscription5.jpg'/>

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
