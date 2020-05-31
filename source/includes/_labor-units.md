# Labor Units

## Labor Units Intro
### CINX Introduction to Industry Labor Units

In construction, a labor unit is the estimated time it takes to install an item under good working conditions.

In the Plumbing/Mechanical industry there are two primary sources of labor unit standards.  They are both industry trade organizations:

  - MCAA - Mechanical Contractors Association of America
  - PHCC - Plumbing - Heating - Cooling Contractors Association

Each organization has two two choices or methods for laboring common Pipe, Valves, and Fittings. 

  - MCAA - **Component** and **Work Activity**
  - PHCC - **Per Fitting** and **Per Joint**

HPH has license agreements with both of these trade organizations which allow us to store their labor units as CINX catalogs and provide API services to access their content. Every labor unit has been assigned a unique HPH **Labor** Code.  The code can stored in local database and used in API calls to access the actual labor unit values.

<aside class="warning">
A single HPH Item Code can be linked to multiple labor units from the labor unit source. A couple of common examples of this include solder joint fittings that can be joined with different solders or brazing materials.  Service weight cast iron fittings can be joined with compression gaskets or lead and oakum. Therefore, there is NOT a one-to-one relationship between an HPH Item Code and a HPH Labor Code. 
</aside>

The API also offers full database and update files of the labor units so that a software system can have a labor unit update feature.

<aside class="warning">
The full and update files for industry labor units will be based on the HPH **LABOR** Code. 
</aside>

HPH has also linked the industry labor units to our HPH Plumbing/Mechanical catalog items. Both PHCC methods and the MCAA Component method have been assigned to our items.

<aside class="warning">
CINX can produce full, update, and custom files for an org's private catalog that includes an array of all labor units linked to the catalog item. The units contained in the file will be dependent on the authorizations attached to the company's CINX account. For more information on API capability please see the Catalog/App Updates - Labor Units section of this documentation site.
</aside>

**NOTES**

  - **Labor units will be returned ONLY if the organization is authorized by the labor unit source (trade organization) to access them**.
  - Please review the assumptions from each trade organization in regards to how the units were calculated and their intended use.
  - The Labor Unit API responses will contain a field named **joint_quantity**. This will be populated only when the labor source is PHCC and the method is Per Joint.

**Supported API Services**

  - [Get a Labor Unit using the HPH Labor Code](#get-labor-hph-code)
  - [Get a Labor Unit using the Source Id](#get-labor-source-id)
  - [Get an Item's Labor Units using the HPH Item Code](#get-item-labor-hph-item-code)
  - [Get a List of Labor Unit Update Files](#get-labor-update-list)
  - [Download a Labor Unit Update File](#download-labor-update)
  - [Mark Labor Update Applied](#mark-labor-update-applied)

## Get Labor - HPH Code
### API Endpoint – Get a Labor Unit using an HPH Labor Code

> The above code returns JSON structured like this:

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "e3944e24-5fa5-5880-b140-2e0cbf3d5a6c",
    "hph_labor_code": "L01FTCU030000025",
    "source_unit_id": "533501",
    "source": "MCAA",
    "source_logo": "http://cdn.dev.cinx.biz/assets/apps/app-v2-mcaa.png",
    "method": "component",
    "description": "Piping Systems (Component Method) | Fittings | Copper | Pressure | 95/5 Solder | 90 Elbow Long Radius | 1.0000 Dia. (in)",
    "joint_quantity": null,
    "base_unit": 0.63,
    "total_unit": 0.63,
    "uom": "HOUR",
    "date_effective": "2008-03-01"
  }]
}
```

`GET`

This endpoint will be used to get a labor unit’s information using the HPH Labor Code.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/labor/hph/{hph_labor_code}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/labor/hph/L01FTCU030000025`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Labor - Source Id
### API Endpoint – Get a Labor Unit using the Source's (Trade Organization) Unit Id

> The above code returns JSON structured like this:

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "e3944e24-5fa5-5880-b140-2e0cbf3d5a6c",
    "hph_labor_code": "L01FTCU030000025",
    "source_unit_id": "533501",
    "source": "MCAA",
    "source_logo": "http://cdn.dev.cinx.biz/assets/apps/app-v2-mcaa.png",
    "method": "component",
    "description": "Piping Systems (Component Method) | Fittings | Copper | Pressure | 95/5 Solder | 90 Elbow Long Radius | 1.0000 Dia. (in)",
    "joint_quantity": null,
    "base_unit": 0.63,
    "total_unit": 0.63,
    "uom": "HOUR",
    "date_effective": "2008-03-01"
  }]
}
```
`GET`

This endpoint will be used to get a labor unit’s information using the source's (trade organization) Id for the unit.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/labor/{labor_source}/{labor_source_unit_id}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/labor/mcaa/533501`

**LABOR SOURCE URL COMPONENT OPTIONS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
labor_source | Defines the labor unit organization. | mcaa, phcc
format | Defines the response format type. If not specified, json will be used. | json, xml

<aside class="warning">
The Ids used in the endpoint are defined by the labor unit source. CINX/HPH cannot guarantee their uniqueness. Please note that the MCAA uses a single Id to represent their Component method and the installation activity of their Work Activity method. So, most ids in the MCAA labor unit catalog will be linked to two different labor units. 
</aside>

## Get Item Labor - HPH Item Code
### API Endpoint – Get an Item's Labor Units using an HPH Item Code

> The above code returns JSON structured like this:

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "edc36af3-0c18-5f43-88d8-912525226084",
    "availability_status": "A",
    "size": "1\"",
    "category": "Copper Fittings",
    "sub_category": "Pressure Wrot-Solder",
    "item_ids": {},
    "descriptions": {},
    "mfr": {},
    "weight": {},
    "material_cost_code": {},
    "image": {},
    "spec_sheet": {},
    "mfr_list_price": {},
    "org_prices": [],
    "labor_units": [{
        "cinx_guid": "1b99b258-f362-5127-a354-8a56e1593a21",
        "hph_labor_code": "L02PP11500005201",
        "source_unit_id": "3.9.50.220.3.2054",
        "source": "PHCC",
        "method": "per fitting",
        "description": "Piping/Process | Copper | 1000 Degree Alloy Braze | Elbow | 1\"",
        "joint_quantity": null,
        "base_unit": 0.57,
        "total_unit": 0.57,
        "uom": "HOUR",
        "date_effective": "2012-02-13"
      },
      {
        "cinx_guid": "9d79c10d-4cc9-5a7c-9d59-85268928184d",
        "hph_labor_code": "L02PP21400009539",
        "source_unit_id": "3.9.50.221.3.2054",
        "source": "PHCC",
        "method": "per joint",
        "description": "Piping/Process (Per Joint Method) | Copper | 1000 Degree Alloy Braze | Joint | 1\"",
        "joint_quantity": 3,
        "base_unit": 0.28,
        "total_unit": 0.8400000000000001,
        "uom": "HOUR",
        "date_effective": "2012-02-13"
      }
    ]
  }]
}
```

`GET`

This endpoint will be used to get a catalog item’s labor units and descriptive information using the HPH Item Code of an item. The API response contains a labor units array to allow for the inclusion of all available labor units assigned to the item given the org's authorizations in CINX. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/hph-code/{hph_code}?view=details&labor={labor_type}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/hph-code/012EK0018?view=details&labor=all`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
view | Defines which API response format will be returned. | details
labor | Defines which organization's units are to be returned. | mcaa, phcc, all
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Labor Update List
### API Endpoint – Get a List of Labor Updates

> The above code returns JSON structured like this:

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "13e33a1f-6363-541d-b7f7-8bd23ce7a301",
    "title": "MCAA Labor",
    "type": "FULL",
    "published": "2020-05-20 15:37:16",
    "range_start": "2000-01-01",
    "range_end": "2020-05-21",
    "documents": [{
      "type": "DATA-FILE",
      "format": "zip",
      "size": 5850414
    }],
    "consumed": "Yes",
    "downloads": [{
        "downloaded": "2020-05-21",
        "applied": "2020-05-21",
        "user": "Will Stone"
      },
      {
        "downloaded": "2020-05-21",
        "applied": "2020-05-21",
        "user": "Will Stone"
      }
    ]
  }]
}
```
`GET`

This endpoint will be used to retrieve labor updates for a given labor unit catalog.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/labor-updates**

The app_id is the cinx_app_id value for the desired labor unit source found in the API's subscription response.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/app/3df33ce2-a5f5-5c39-8da1-0a969c23f444/labor-updates`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
status | Limits results based on the consumption status. | NEW, APPLIED, ALL
type | Limits results based on type of update file. | UPDATE, FULL
after | Limits results to files published after the submitted date. | YYYY-MM-DD
format | Defines the response format type. If not specified, json will be used. | json, xml


**Notes**

  - If no **status** parameter is included in the URL, the ALL option will be used by default 
  - If the URL uses the **NEW** parameter and there are no new updates, the API response will have an empty **rows** array
  - Labor Update files of **type=Update** should always be processed in chronological order starting with the earliest date.

## Download Labor Update
### API Endpoint – Download a Labor Update File

`GET`

This endpoint will be used to download a labor unit update file. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/labor-update/{update_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/app/3df33ce2-a5f5-5c39-8da1-0a969c23f444/labor-update/13e33a1f-6363-541d-b7f7-8bd23ce7a301`

**Notes**

  - The update guid used in the URL is obtained from the Get Update List response.  It is the cinx_guid value in the response.
  - Labor Update files of **type=Update** should always be processed in chronological order starting with the earliest date.

## Mark Labor Update Applied
### API Endpoint – Mark Labor Unit Update File As Applied

`PUT`

This will mark the update as **Applied** and it will no longer show up in the **New** update list.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/app/{app_id}/labor-update/{update_guid}/apply**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/app/3df33ce2-a5f5-5c39-8da1-0a969c23f444/labor-update/13e33a1f-6363-541d-b7f7-8bd23ce7a301/apply`