# Catalog Updates
## Update Intro
### CINX Catalog Update Introduction - Price Update Service

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

**Catalog Update File Status Filter Types**

Each CINX catalog update file has field that defines its **Status**. When an API call is made to retrieve catalog updates a Status filter can be submitted.  Catalog update status filters are:

  -  **New** – files that have not been download or applied
  -  **Applied** – files that have been applied to the integrated system (Requires submission of an API call to mark the file as Applied.)
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

cinxApi.getCatalogUpdates(application_id, update_type)
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
            "title": "QuoteExpress Mechanical Legacy FULL 08/13/2014",
            "type": "FULL",
            "date_published": "2014-08-13 21:12:35",
            "date_range_start": "2001-01-01",
            "date_range_end": "2014-08-13",
            "documents": [
                {
                    "type": "DATA-FILE",
                    "format": "upd",
                    "size": 80954160,
                    "formatter": "upd"
                },
                {
                    "type": "BULLETIN",
                    "format": "xls",
                    "size": 184320,
                    "formatter": "xls"
                },
                {
                    "type": "BULLETIN",
                    "format": "js",
                    "size": 197514,
                    "formatter": "js"
                }
            ],
            "transactions": null,
            "count_of_transactions": 0,
            "consumed": {
                "download_date": "2019-07-23",
                "applied_date": "2019-07-23",
                "user": {
                    "name": "Will Stone",
                    "cinx_id": {
                        "type": "USER",
                        "domain": "users",
                        "id": "185aabe1-3487-5f59-9ad5-c577a76bd392"
                    }
                },
                "cinx_id": {
                    "type": "SUB-CONSUMPTION",
                    "domain": "org-0001-4030",
                    "id": "4ceb4a6e-0513-5745-bf8b-bf9266a28561"
                }
            },
            "export_id": "bulletin_20140813_161048",
            "created_by": "User Not Found",
            "cinx_id": {
                "type": "SUB-UPDATE",
                "domain": "subscriptions",
                "id": "7b13257e-25ff-3a03-5d7d-9f4dbe30e091"
            }
        }
    ]
}
```
`GET`

This endpoint will be used to retrieve catalog updates for a given subscription. 

**Notes**

  - If the url uses the **new** update status parameter and there are no new updates, the api response will have an empty **rows** array


URL Pattern: **{api path}/{api_version}/sub/{api_token}/xxx**

URL Sample: `https://update me`

## Download Update
### API Endpoint – Download a Catalog Update File
`GET`

This endpoint will be used to download a catalog update file. 


URL Pattern: **{api path}/sub/{app-id-guid}/ipu/update/download/{update id}/data-file**

URL Sample: `https://update me`


<img src='images/subscription16.jpg'/>

## Download Bulletin
### API Endpoint – Get a Catalog Update Bulletin File ONLY - Download
`GET`

This will stream back the bulletin file in the requested format.

URL Pattern: **{api path}/sub/{app-id-guid}/ipu/update/download/{update id}/bulletin?type={json or xls}**

URL Sample: `https://update me`

`https://api.cinx.com/sub/0d2b4b77-d706-e215-13f2-207c7e4aaee7/ipu/update/download/1ac399a6-40e8-f9e4-d5b8-d5dc709e9e1d/bulletin?type=json`

`https://api.cinx.com/sub/0d2b4b77-d706-e215-13f2-207c7e4aaee7/ipu/update/download/1ac399a6-40e8-f9e4-d5b8-d5dc709e9e1d/bulletin?type=xls`

<img src='images/subscription17.jpg'/>

## Mark as Applied
### API Endpoint – Mark Catalog Update File As Applied

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"applied_date":"2019-06-21", "download_date":"2019-06-21"}`;

cinxApi.setCatalogUpdateFileApplied(application_id, file_id, values)
    .then(function(response) {
        console.log(response);
    });
```
`PUT`

This will mark the update as **Applied** and it will no longer show up in the **New** update list.

URL Pattern: **{api path}/sub/{app-id-guid}/ipu/update/apply/{update id}?values={applied_date:yyyy-mm-dd,download_date:yyyy-mm-dd}**

URL Sample: `https://update me`


The update id field is taken from the Get Update response in the following location:  row -> cinx_id -> id

Sample:

`https://api.cinx.com/sub/0d2b4b77-d706-e215-13f2-207c7e4aaee7/ipu/update/apply/1ac399a6-40e8-f9e4-d5b8-d5dc709e9e1d?values={%22applied_date%22:%222016-06-10%22,%22download_date%22:%222016-06-10%22}`