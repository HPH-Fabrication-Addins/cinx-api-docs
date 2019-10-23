# Labor Units

## Labor Units Intro
### CINX Introduction to Industry Labor Units

In construction, a labor unit is the estimated time it takes to install an item under good working conditions.

In the Plumbing/Mechanial industry there are two primary sources of labor unit standards.  They are both industry trade organzations:

  - MCAA - Mechanical Contractors Association of America
  - PHCC - Plumbing - Heating - Cooling Contractors Association

Each organization has two two choices or methods for laboring common Pipe, Valves, and Fittings. 

  - MCAA - **Component** and **Work Activity**
  - PHCC - **Per Fitting** and **Per Joint**

HPH has license agreements with both of these trade organinzations which allow us to store their labor units as CINX catalogs and provide API services to access their content. Every labor unit has been assigned a unique HPH Labor Code.  The code can stored in local database and used in API calls to access the actual labor unit values.

The API also offers full database and update files of the labor units so that a sofware system can have a labor unit update feature.

HPH has also linked the industry labor units to our HPH Plumbing/Mechanical catalog items. Both PHCC methods and the MCAA Component method have been assigned to our items.

**NOTES**

  - **Labor units will be returned ONLY if the organziation is authorized by the labor unit source (trade organization) to access them**.
  - Please review the assumptions from each trade organization in regards to how the units were calculated and their intended use.
  - The Labor Unit API responses will contain a field named **joint_quantity**. This will be populated only when the labor source is PHCC and the method is Per Joint.

**Dependencies and Business Rules**

  - A single HPH Item Code can be linked to multiple labor units from the labor unit source

**Supported API Services**

  - [Get a Labor Unit using the HPH Labor Code]()
  - [Get a Labor Unit using the Source Id]()
  - [Get a Labor Unit Update File]()
  - [Get an Item's Labor Units using the HPH Item Code]()
  - [Get an Item's Labor Units using an Organization's Item Id]()
  - [Get an Item's Labor Units using a CINX Item Id]()


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
labor_source | Defines the labor unit organization. | MCAA, PHCC


## Get Item Labor - HPH Code
### API Endpoint – Get an Item's Labor Units using an HPH Code

> The above code returns JSON structured like this:

```json

```

`GET`

This endpoint will be used to get a catalog item’s labor unit and descriptive information using the HPH Code of an item.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/hph-code/{hph_code}?view=details&labor={labor_type}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/hph-code/012EK0018?view=details&labor=all`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
view | Defines which API response format will be returned. | details
labor | Defines which organization's units are to be returned. | MCAA, PHCC, ALL
