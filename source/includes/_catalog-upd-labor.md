# Catalog/App Updates - Labor
## Update Intro
### CINX Catalog/Application Update Introduction - Labor Unit Update Service

CINX allows a company to define their own catalog of material content. This Private Catalog can contain items from the Harrison Plumbing/Mechanical database, vendor catalogs that are hosted on CINX, and items created and maintained by the company. The items in a private catalog can also be linked to labor units.

In construction, a labor unit is the estimated time it takes to install an item under good working conditions.

In the Plumbing/Mechanical industry there are two primary sources of labor unit standards.  They are both contractor industry trade organizations:

  - MCAA - Mechanical Contractors Association of America
  - PHCC - Plumbing - Heating - Cooling Contractors Association

Each organization has two two choices or methods for laboring common Pipe, Valves, and Fittings. 

  - MCAA - **Component** and **Work Activity**
  - PHCC - **Per Fitting** and **Per Joint**

HPH has license agreements with both of these trade organizations which allow us to store their labor units as CINX catalogs and provide API services to access their content. 

The CINX API has two different labor unit update options:

  - Catalog/App Updates service is based on the items in an org's private catalog and uses the HPH **ITEM** CODE and is documented in this web site section.
  - Industry Labor Catalog update service is based on each trade organization labor catalog and uses the HPH **LABOR** CODE and is documented in the **LABOR UNITS** section of this site.

<aside class="warning">
A single HPH Item Code can be linked to multiple labor units from the labor unit source. A couple of common examples of this include solder joint fittings that can be joined with different solders or brazing materials.  Service weight cast iron fittings can be joined with compression gaskets or lead and oakum. Therefore, there is NOT a one-to-one relationship between an HPH Item Code and a HPH Labor Code. 
</aside>

**File Format**

By default CINX offers to standard file format options: JSON and CSV. Custom formats can also be developed.

**The contents of the files are based on the HPH Item Code. Therefore, if an item in the private catalog has multiple labor units their will be multiple rows/entries of the HPH Item Code in the file.**

**Labor Update File Types**

Each CINX catalog labor update file has field that defines its **Type**. Catalog labor update types are:

  -  **Full** – file contains ALL items in the catalog
  -  **Custom** – file contains user-defined contents (The CINX UI can be used to trigger the generation of a custom labor unit file)
  -  **Update** – file contains any labor units that have had changes since the previous update was published (Trade organizations rarely release updates to existing labor units)

**Notifications**

When a labor update is posted, CINX checks the subscription settings and notifies the defined users. Notification types include:

  - Email
  - CINX System Alert


**Catalog Update File Consumption Status Types**

Each CINX catalog labor update file has field that defines its **Status**. When an API call is made to retrieve catalog labor updates a Status filter can be submitted.  Catalog update status filters are:

  -  **New** – files that have not been download or applied
  -  **Applied** – files that have been applied to the integrated system (Requires submission of an API call to mark the file as consumed/applied.)
  -  **All** – returns all update files for the requested subscription

**NOTES**

  - **Labor units will be returned ONLY if the organization is authorized by the labor unit source (trade organization) to access them**.
  - Please review the assumptions from each trade organization in regards to how the units were calculated and their intended use.
  - The API responses will contain a field named **joint_quantity**. This will be populated only when the labor source is PHCC and the method is Per Joint.


**Supported API Services**

  - [Get Labor Update List](#get-labor-update-list)
  - [Download a Labor Update File](#download-labor-update)
  - [Mark Labor Update Applied](#mark-labor-update-applied)

## Get Labor Update List
### API Endpoint – Get a List of Catalog Labor Unit Updates

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

This endpoint will be used to retrieve catalog labor updates for a given subscription.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/labor-updates**

The app_id is the cinx_app_id value for the **Integrated Labor Updates** Import-Export app found in the API's subscription response.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/app/c5919ab5-68e4-580a-ae1e-9f748abfb223/labor-updates?status=all`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
status | Limits results based on the consumption status. | NEW, APPLIED, ALL
type | Limits results based on type of update file. | UPDATE, FULL, CUSTOM
after | Limits results to files published after the submitted date. | YYYY-MM-DD
format | Defines the response format type. If not specified, json will be used. | json, xml

**Notes**

  - If no **status** parameter is included in the URL, the ALL option will be used by default 
  - If the URL uses the **NEW** parameter and there are no new updates, the API response will have an empty **rows** array

## Download Labor Update
### API Endpoint – Download a Catalog/App Labor Update File

`GET`

This endpoint will be used to download a catalog update file. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/price-update/{update_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/app/2494df92-e855-5563-826c-05907f9cca22/price-update/7b13257e-25ff-3a03-5d7d-9f4dbe30e091`

**Notes**

  - The update guid used in the URL is obtained from the Get Update List response.  It is the cinx_guid value in the response.
  - Catalog Update files of **type=Update** should always be processed in chronological order starting with the earliest date.


## Mark Labor Update Applied
### API Endpoint – Mark Catalog/App Labor Update File As Applied

`PUT`

This will mark the labor update as **Applied** and it will no longer show up in the **New** update list.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/labor-update/{update_guid}/apply**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/app/2494df92-e855-5563-826c-05907f9cca22/price-update/7b13257e-25ff-3a03-5d7d-9f4dbe30e091/apply`
