# Project Items

## Project Items Definition
### CINX Object Definition - Project Items

CINX Project Items are building material products or construction related services that are used on a project.

A CINX project item is linked to its source item in a CINX Catalog. Note: If a project is imported into CINX and its items are not yet linked to a catalog item a new catalog item will be created.

In addition to the catalog-level information, a project item has a large number of fields that can used to manage the item through the different project and procurement workflows. Some important examples include: project job-costing, taxes, order conditions, construction status, work-breakdowns, and ERP integration.  

Project items are also tracked on every transaction to which they have been attached.

**Dependencies and Business Rules**

  - A project item must be associated with a CINX project
  - A project item must be associated with a CINX catalog item
  - A project item must have a quantity

**Supported API Services**

  - [Get Project Items](#get-project-items)

## Get Project Items
### API Endpoint – Get a Project Items

> The above code returns JSON structured like this:

```json

```

`GET`

This endpoint will be used to get a listing of a specific project's item.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/items?view={view_option}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/bb613aff-4256-5359-b7cd-391505d19e01/items?view=ids`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
view | Defines the level of content in the response. | ids, compact, details
guid | Limits the response to a single CINX Project Item GUID. | {cinx_guid}
hph-code | Limits the response to a single HPH Item Code. | {hph_item_code}
model-guid | Limits the response to a single Model Item GUID. | {model_guid}
org-id | Limits the response to a single organization's item id | {org_id}
org-sys | Limits the response to a single organization's item system id. | {org_system_id}
mfr-part | Limits the response to a single Manufacturer Part Number. | {mfr_part_number}
upc | Limits the response to a single Manufacturer UPC Number. | {upc__number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 10 will be used. | Integer

**View** 

- **ids**: returns a small set of item ids. Please see [Compact View](#project-items-view-ids) for a definition of the output.
- **compact**: returns a small set of project item information fields. This is the default view if one is not specified. Please see [Compact View](#project-items-view-compact) for a definition of the output.
- **details**: returns a comprehensive set of project item information. Please see [Details View](#project-items-view-details) for a definition of the output. This is the default view if one is not specified.

## Project Items View - Ids
### API Project Items Response View Definition - Ids

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "dc7517d8-6e8c-5bfd-927f-1b784d401143",
    "hph_code": "012NI0018",
    "upc": "039923312969",
    "org_item_id": null,
    "org_system_id": null,
    "model_item_guid": "234234q32fqw5324f3232"
  }]
}
```
When requesting listing of a project's items from the CINX API there are three view options. 

The table below defines the fields output using the **ids** view option.

NOTE: Limit and Offset information is included in the **Response** object.

## Project Items View - Compact
### API Project Items Response View Definition - Compact

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "dc7517d8-6e8c-5bfd-927f-1b784d401143",
    "hph_code": "012NI0018",
    "upc": "039923312969",
    "org_item_id": null,
    "org_system_id": null,
    "mfr_part_number": "607",
    "model_item_guid": "234234q32fqw5324f3232",
    "size": null,
    "description": "1\" WROT CXC 90 ELBOW",
    "mfr_name": "NIBCO, Inc.",
    "quantity": 3,
    "unit_price": 18.11,
    "price_uom": "E",
    "weight": 0.177,
    "weight_uom": "lb",
    "phase_name": null,
    "material_cost_code": "UG-123",
    "labor_cost_code": null,
    "taxable": "Yes",
    "availability_status": "A",
    "procurement_status": "NOT ORDERED",
    "construction_status": "NOT INSTALLED"
  }]
}
```
When requesting listing of a project's items from the CINX API there are three view options. 

The table below defines the fields output using the **compact** view option.

NOTE: Limit and Offset information is included in the **Response** object.

## Project Items View - Details
### API Project Items Response View Definition - Details

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "dc7517d8-6e8c-5bfd-927f-1b784d401143",
    "hph_code": "012NI0018",
    "upc": "039923312969",
    "org_item_id": null,
    "org_system_id": null,
    "mfr_part_number": "607",
    "model_item_guid": "234234q32fqw5324f3232",
    "size": null,
    "description": "1\" WROT CXC 90 ELBOW",
    "mfr_name": "NIBCO, Inc.",
    "unit_price": 18.11,
    "price_uom": "E",
    "image_url": "",
    "spec_sheet_url": null,
    "item_type": "MATERIAL",
    "weight": 0.177,
    "weight_uom": "lb",
    "labor_unit": 0,
    "labor_cost": 0,
    "availability_status": "A",
    "procurement_status": "NOT ORDERED",
    "construction_status": "NOT INSTALLED",
    "quantities": {
      "entered": 3,
      "ordered": 3,
      "received": 0,
      "invoiced": 0,
      "back_ordered": 0
    },
    "order_conditions": {
      "allow_substitutes": "Yes",
      "order_lead_time": 10,
      "order_by_date": null
    },
    "delivery": {
      "deliver_to": "Site Forman",
      "location_type": "HPH",
      "instructions": "Handle with double extra care",
      "labeling_instructions": "HPH-789879",
      "packaging_instructions": "Wrapped pallets"
    },
    "work_breakdown": {
      "work_order_name": "WO-8774512",
      "spool_name": null,
      "building_name": "HPH1",
      "level": "1",
      "space": "Lobby",
      "sub_space": "Female Restroom",
      "system": "Domestic Cold Water",
      "arch_symbol": "ELB-045"
    },
    "job_cost": {
      "phase_name": "First Floor",
      "material_cost_code": "UG-123",
      "labor_cost_code": null,
      "category_name": null
    },
    "taxes": {
      "taxable": "Yes",
      "tax_group_name": "TAX-12"
    }
  }]
}
```
When requesting listing of a project's items from the CINX API there are three view options. 

The table below defines the fields output using the **details** view option.

NOTE: Limit and Offset information is included in the **Response** object.


## Create or Modify a Project Item
### API Endpoint - Create or Modify a New Project Item

<aside class="warning">
Please use teh Modify Project API call to create or modify a project item. Documentation for this API Endpoint can be found under the **Projects** menu option.
</aside>

