# Catalog/App Updates
## Update Intro
### CINX Catalog/Application Update Introduction - Price Update Service

CINX allows a company to define their own catalog of material content. This Private Catalog can contain items from the Harrison Plumbing/Mechanical database, vendor catalogs that are hosted on CINX, and items created and maintained by the company. In addition, a company can have access to CINX software partner catalogs. For example, databases used by industry estimating systems are available as CINX catalogs.

As part of CINX’s integration services, a company can request catalog updates formatted for industry software or develop a customized format. The company can have unlimited subscriptions to CINX Import-Export Applications.

Each subscription will define the catalog of items and the output format. This subscription has an **app_id** that will be required to create API requests. This Id can be obtained from the CINX Subscriptions/Authorizations response.

**Update Format**

As noted above, CINX can produce update files according to the specifications of leading industry software systems. Custom formats are also supported.

In addition to specifying the catalog and format, a subscription has additional settings that are used to manage the update process. Examples include a schedule for when updates are produced, who is notified when updates are ready, and what prices types (sources) to include in the updates.

**Schedule**

CINX has the ability to define when catalog updates are processed for subscriptions based on a Private CINX catalog. Schedule options include:

  - Nightly
  - Weekly (select the day)
  - Monthly (select the 1st, 15th, of 28th of the month)
  - Quarterly

**Notifications**

When a catalog update is posted, CINX checks the subscription settings and notifies the defined users. Notification types include:

  - Email
  - CINX System Alert

**Price Types/Sources**

CINX has the ability to include four price types in a catalog update file.  

  - Manufacturer List
  - Buy/Purchase  (taken from the company’s private catalog)
  - Sell/Invoice (taken from the company’s private catalog)
  - Estimate (taken from the company’s private catalog)

**Catalog Update File Types**

Each CINX catalog update file has field that defines its **Type**. Catalog update types are:

  -  **Update** – file contains any items that have had changes since the previous update was published
  -  **Full** – file contains ALL items in the catalog
  -  **Custom** – file contains user-defined contents

**Catalog Update File Consumption Status Types**

Each CINX catalog update file has field that defines its **Status**. When an API call is made to retrieve catalog updates a Status filter can be submitted.  Catalog update status filters are:

  -  **New** – files that have not been download or applied
  -  **Applied** – files that have been applied to the integrated system (Requires submission of an API call to mark the file as consumed/applied.)
  -  **All** – returns all update files for the requested subscription

**CINX UI – Catalog Updates**

The CINX UI provides extensive capabilities to manage the catalog updates. Admin settings can be defined that will allow for the creation of update files that can be accessed via the API. Custom update files can be requested. Updates can be downloaded and a history of activity can be viewed.

<img src='images/subscription15.jpg'/>

(Note: many of the API URLs will contain an IPU parameter. IPU is an acronym for Integrated Product/Price Updates)

## Get Update List
### API Endpoint – Get a List of Catalog Updates

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

cinxApi.getCatalogUpdates(application_guid, update_type)
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "7b13257e-25ff-3a03-5d7d-9f4dbe30e091",
    "title": "QuoteExpress Mechanical Legacy FULL 08/13/2019",
    "type": "FULL",
    "published": "2019-08-13 21:12:35",
    "range_start": "2001-01-01",
    "range_end": "2019-08-13",
    "documents": [{
        "type": "DATA-FILE",
        "format": "upd",
        "size": 80954160
      },
      {
        "type": "BULLETIN",
        "format": "xls",
        "size": 184320
      },
      {
        "type": "BULLETIN",
        "format": "js",
        "size": 197514
      }
    ],
    "consumed": "Yes",
    "downloads": [{
      "downloaded": "2019-09-23",
      "applied": "2019-09-23",
      "user": "Will Stone"
    }]
  }]
}
```
`GET`

This endpoint will be used to retrieve catalog updates for a given subscription.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/price-updates**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/app/2494df92-e855-5563-826c-05907f9cca22/price-updates?status=all`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
status | Limits results based on the consumption status. | NEW, APPLIED, ALL


**Notes**

  - If no **status** parameter is included in the URL, the ALL option will be used by default 
  - If the url uses the **NEW** parameter and there are no new updates, the api response will have an empty **rows** array

## Download Update
### API Endpoint – Download a Catalog/App Update File

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

cinxApi.getCatalogUpdateFile(application_guid, update_guid)
    .then(function(response) {
        console.log(response);
    });
```
`GET`

This endpoint will be used to download a catalog update file. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/price-update/{update_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/app/2494df92-e855-5563-826c-05907f9cca22/price-update/7b13257e-25ff-3a03-5d7d-9f4dbe30e091`

**Notes**

  - The update guid used in the URL is obtained from the Get Update List reponse.  It is the cinx_guid value in the reponse.


## Download Bulletin
### API Endpoint – Download a Catalog/App Update Bulletin File ONLY
`GET`

This will stream back the update bulletin file in the requested format.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/price-update/{update_guid}/bulletin**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/app/2494df92-e855-5563-826c-05907f9cca22/price-update/7b13257e-25ff-3a03-5d7d-9f4dbe30e091/bulletin?type=xls`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
type | Defines the file type to be returned. | XLS, JS

**Notes**

  - If no **type** parameter is included in the URL, the XLS option will be used by default 

## Mark as Applied
### API Endpoint – Mark Catalog/App Update File As Applied

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"applied_date":"2019-06-21", "download_date":"2019-06-21"}`;

cinxApi.setCatalogUpdateFileApplied(application_guid, file_guid, values)
    .then(function(response) {
        console.log(response);
    });
```
`PUT`

This will mark the update as **Applied** and it will no longer show up in the **New** update list.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/price-update/{update_guid}/apply**

URL Sample: `https://update me`


The update id field is taken from the Get Update response in the following location:  row -> cinx_id -> id

Sample:

`https://api.cinx.com/sub/0d2b4b77-d706-e215-13f2-207c7e4aaee7/ipu/update/apply/1ac399a6-40e8-f9e4-d5b8-d5dc709e9e1d?values={%22applied_date%22:%222016-06-10%22,%22download_date%22:%222016-06-10%22}`
