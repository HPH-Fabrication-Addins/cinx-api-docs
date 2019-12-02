# Catalog Item

## Item Definition
### CINX Object Definition - Catalog Item

A CINX Catalog Item is a building material product or construction related service that is stored within a CINX catalog.

A CINX catalog is a collection of items grouped together in a CINX database structure. Catalogs may contain construction materials, sub-contract services, rental equipment, and other content necessary for the execution of a construction project or maintenance of a building.

A CINX organization will have a private catalog where items can be stored. An organization's private CINX catalog can be built from the items from CINX public catalogs including the HPH Plumbing/Mechanical database. Private items not associated with a CINX public catalog can also be inserted into an organization's private catalog. Thus, the responsibility for maintaining that item will be the organization.

**Labor Units**

HPH has worked with industry labor unit providers (MCAA and PHCC) to store their labor units as CINX Catalogs. HPH has also linked labor units to our HPH Plumbing/Mechanical catalog items. The CINX Get Item API can return labor units when the **details view** is used. Adding a labor parameter to the URL will enable the output of labor units. **Labor units will be returned ONLY if the organization is authorized by the labor unit author to access them**.

For more information about labor units, please review the [Labor Units](#labor-units) pages on this site.

**Dependencies and Business Rules**

  - A catalog item must be associated with a CINX catalog
  - A catalog item must have a description
  - A catalog item must have a manufacturer

**Supported API Services**

  - [Get an Item using the HPH Code](#get-item-hph-code)
  - [Get an Item using an Organization Id](#get-item-org-id)
  - [Get an Item using a CINX Id](#get-item-cinx-id)
  - [Create a Catalog Item from an HPH Code](#create-item-hph-code)
  - [Get a Catalog Item Template](#get-item-template)
  - [Create a Catalog Item](#create-item)
  - [Modify a Catalog Item](#modify-item)


## Get Item - HPH Code
### API Endpoint – Get an Item using an HPH Code

> The above code returns JSON structured like this:

```json

```

`GET`

This endpoint will be used to get a catalog item’s information using the HPH Code of an item.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/hph-code/{hph_code}?view={view_option}&labor={labor_type}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/hph-code/012EK0018?view=details`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
view | Defines the level of content in the response. | compact, details, list-price
labor | Defines the type of labor units returned. | mcaa, phcc, all
format | Defines the response format type. If not specified, json will be used. | json, xml

**View** 

- **compact**: returns a small set of item information fields. This is the default view if one is not specified. Please see [Compact View](#item-view-compact) for a definition of the output.
- **details**: returns a comprehensive set of item information. Please see [Details View](#item-view-details) for a definition of the output.
- **list-price**: returns details about the current mfr list price for the item. Please see [List Price View](#item-view-list-price) for a definition of the output.

**Labor** 

- **all**: returns all industry labor units the organization is authorized to use
- **mcaa**: returns the MCAA labor units if the organization is authorized to access them
- **phcc**: returns the PHCC labor units if the organization is authorized to access them

## Get Item - Org Id
### API Endpoint – Get an Item using an Org Item Id

> The above code returns JSON structured like this:

```json

```
`GET`

This endpoint will be used to get a catalog item’s information using the organization's item id.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/org-id/{org_item_id}?view={view_option}&labor={labor_type}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/org-id/C90114?view=details`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
view | Defines the level of content in the response. | compact, details, list-price
labor | Defines the type of labor units returned. | mcaa, phcc, all
format | Defines the response format type. If not specified, json will be used. | json, xml

**View** 

- **compact**: returns a small set of item information fields. This is the default view if one is not specified. Please see [Compact View](#item-view-compact) for a definition of the output.
- **details**: returns a comprehensive set of item information. Please see [Details View](#item-view-details) for a definition of the output.
- **list-price**: returns details about the current mfr list price for the item. Please see [List Price View](#item-view-list-price) for a definition of the output.

**Labor** 

- **all**: returns all industry labor units the organization is authorized to use
- **mcaa**: returns the MCAA labor units if the organization is authorized to access them
- **phcc**: returns the PHCC labor units if the organization is authorized to access them

## Get Item - CINX Id
### API Endpoint – Get an Item using the CINX Id

> The above code returns JSON structured like this:

```json

```
`GET`

This endpoint will be used to get a catalog item’s information using the item's CINX Id.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/guid/{cinx_guid}?view={view_option}&labor={labor_type}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/guid/b023b15c-b996-11e0-b635-00137268a1bf?view=details`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
view | Defines the level of content in the response. | compact, details, list-price
labor | Defines the type of labor units returned. | mcaa, phcc, all
format | Defines the response format type. If not specified, json will be used. | json, xml

**View** 

- **compact**: returns a small set of item information fields. This is the default view if one is not specified. Please see [Compact View](#item-view-compact) for a definition of the output.
- **details**: returns a comprehensive set of item information. Please see [Details View](#item-view-details) for a definition of the output.
- **list-price**: returns details about the current mfr list price for the item. Please see [List Price View](#item-view-list-price) for a definition of the output.

**Labor** 

- **all**: returns all industry labor units the organization is authorized to use
- **mcaa**: returns the MCAA labor units if the organization is authorized to access them
- **phcc**: returns the PHCC labor units if the organization is authorized to access them

## Item View - Compact
### API Item Response View Definition - Compact

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "b0f01d82-b996-11e0-b635-00137268a1bf",
    "availability_status": "A",
    "size": "1\"",
    "category": "Copper Fittings & Flanges",
    "sub_category": "Pressure Wrot-Solder",
    "hph_code": "012NI0018",
    "org_item_id": null,
    "org_system_id": null,
    "mfr_part_number": "607",
    "description": "1\" WROT CXC 90 ELBOW",
    "mfr_name": "NIBCO, Inc.",
    "mfr_list_price": 18.11,
    "price_uom": "E"
  }]
}
```
When requesting a catalog from the CINX API there are three view options. 

The table below defines the fields output using the **compact** view option.

## Item View - Details
### API Item Response View Definition - Details

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "b0f01d82-b996-11e0-b635-00137268a1bf",
    "availability_status": "A",
    "size": "1\"",
    "category": "Copper Fittings & Flanges",
    "sub_category": "Pressure Wrot-Solder",
    "item_ids": {
      "hph_code": "012NI0018",
      "org_item_id": null,
      "org_system_id": null,
      "mfr_part_number": "607",
      "mfr_order_number": "9055750",
      "upc": "039923312969",
      "gtin": "00039923312969"
    },
    "descriptions": {
      "org": null,
      "cinx_long": "1\" WROT CXC 90 ELBOW",
      "cinx_short": "1 WROT CXC 90 ELL",
      "mfr": null
    },
    "mfr": {
      "cinx_org_id": "org-0000-1411",
      "name": "NIBCO, Inc.",
      "name_short": "NIBCO",
      "status": "A"
    },
    "weight": {
      "weight": 0.177,
      "uom": "lb"
    },
    "image": {
      "url": "http://cdn.dev.cinx.biz/assets/org-0000-1411/5bd9c604de78090ebd153512.jpg",
      "mime_type": "image/jpg"
    },
    "spec_sheet": {
      "url": null,
      "mime_type": null
    },
    "mfr_list_price": {
      "cinx_price_sheet_guid": "3d4c7bfc-49b0-11e9-9891-00137268a1bf",
      "price": 18.11,
      "uom": "E",
      "effective_date": "2019-04-01",
      "price_sheet_number": "WROT-0419",
      "price_sheet_name": "Wrot Copper Fittings"
    },
    "org_prices": [],
    "labor_units": [{
        "cinx_guid": "1b99b258-f362-5127-a354-8a56e1593a21",
        "hph_labor_code": "L02PP11500005201",
        "source": "PHCC",
        "method": "per fitting",
        "description": "Piping/Process | Copper | 1000 Degree Alloy Braze | Elbow | 1\"",
        "joint_quantity": null,
        "base_unit": 0.57,
        "total_unit": 0.57,
        "uom": "HOUR"
      },
      {
        "cinx_guid": "f77b4ca3-1b04-55b3-89cf-a5ada9891f6a",
        "hph_labor_code": "L01FTCU032000022",
        "source": "MCAA",
        "method": "component",
        "description": "Piping Systems (Component Method) | Fittings | Copper | Pressure | Silver Solder Joint (Brazing with Flux) | 90 Elbow Long Radius | 1.0000 Dia. (in)",
        "joint_quantity": null,
        "base_unit": 0.75,
        "total_unit": 0.75,
        "uom": "HOUR"
      }
    ],
    "packaging": [{
        "type": "Master Pack",
        "upc": "039923312969",
        "gtin": "039923312969",
        "quantity": 100,
        "depth": null,
        "height": null,
        "width": null,
        "cube": null,
        "dimension_uom": null,
        "weight": null,
        "weight_uom": null
      }
    ]
  }]
}
```

When requesting a catalog from the CINX API there are three view options. 

The table below defines the fields output using the **details** view option.

## Item View - List Price
### API Item Response View Definition - List Price

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "82393d53-6f55-52a8-8019-42f5ec9615e1",
    "mfr_list_price": 162.32,
    "price_uom": "E",
    "availability_status": "P",
    "effective_date": "2017-06-19",
    "price_sheet_type": "APOLLOXPRESS Fittings",
    "price_sheet_number": "XPR-14",
    "price_sheet_name": "APOLLOXPRESS Fittings",
    "cinx_price_sheet_guid": "14a3dc28-5131-11e7-9399-00137268a1bf"
  }]
}
```
When requesting a catalog from the CINX API there are three view options. 

The table below defines the fields output using the **list-price** view option.

**Notes**

  - The manufacturer list price will be pulled from HPH's public catalog containing the item

## Get Item Template
### API Endpoint - Get a Catalog Item Template

```json
{
  "doc_info": {},
  "template": {
    "cinx_guid": null,
    "availability_status": null,
    "size": null,
    "description": null,
    "mfr_name": null,
    "cinx_material_cost_code_guid": null,
    "product_ids": {
      "org_item_id": null,
      "org_system_id": null,
      "mfr_part_number": null,
      "mfr_order_number": null,
      "upc": null,
      "gtin": null
    },
    "cinx_catalog_parent": {
      "cinx_guid": null,
      "hph_code": null
    },
    "weight": {
      "value": null,
      "uom": null
    },
    "lines": [{
      "cinx_guid": null
    }],
    "org_prices": [{
      "type": null,
      "price": null,
      "uom": null
    }],
    "packaging": [{
      "type": null,
      "upc": null,
      "gtin": null,
      "quantity": null,
      "depth": null,
      "height": null,
      "width": null,
      "cube": null,
      "dimension_uom": null,
      "weight": null,
      "weight_uom": null
    }],
    "attributes": [{
      "name": null,
      "value": null
    }]
  },
  "field_options": {},
  "api_calls": []
}
```
`GET`

This endpoint will be used to get a CINX Template for a catalog item.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/item**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/item`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

The table below defines the input fields within the template.

**TEMPLATE FIELDS**

<aside class="warning">
If you are creating a new private catalog item that will be copied from an existing public catalog (HPH) item, then your API POST request will only need to contain the cinx_catalog_parent object with either the cinx_guid or hph_code field populated. The mandatory fields referenced in the table below are to be used when creating an item NOT linked to a public catalog item. For these fields the Required column will contain the following: Yes (Non-HPH Item).
</aside>

Name | Data Type | Required | Dflt | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; PUT = Yes |  | CINX System Id.
availability_status | String | Yes (Non-HPH Item) | A | Manufacturer availability status of the item. Template has a list of optional values.
size | String | No |  | Size or rating of the item.
description | String | Yes (Non-HPH Item) |  | Organization-defined description for the item.
mfr_name | String | Yes (Non-HPH Item) |  | Name of the item's manufacturer.
cinx_material_cost_code_guid | String (GUID Format) | No |  | Default CINX Id for the Material Cost Code assigned to the item.
product_ids.org_item_id | String | No |  | The organization's Item Id for the item . User-friendly code.
product_ids.org_system_id | String | No |  | The organization's System Item Id for the item. Unique Id code.
product_ids.mfr_part_number | String | No |  | Manufacturer-defined Part/Catalog Number for the item.
product_ids.mfr_order_number | String | No |  | Manufacturer-defined Order Number for the item.
product_ids.upc | String | No |  | Manufacturer-defined UPC Number for the item.
product_ids.gtin | String | No |  | Manufacturer-defined GTIN for the item.
cinx_catalog_parent.cinx_guid | String (GUID Format) | No |  | CINX System Id if the organization's item is linked to a public catalog (HPH) item.
cinx_catalog_parent.hph_code | String | No |  | HPH Item Code if the organization's item is linked to a public catalog (HPH) item.
weight.value | Real | No |  | Weight of the item.
weight.uom | String | No |  | Measurement type in which the weight value is expressed.
line.cinx_guid | String (GUID Format) | No |  | CINX System Id of the Line to which an item is linked.
org_prices.type | String | Yes |  | Type of item price. Template has a list of optional values.
org_prices.price | Real | Yes | 0 | Unit price of the item.
org_prices.uom | String | Yes (Non-HPH Item) | E | Price unit-of-measure. Template has a list of optional values.
packaging.type | String | No |  | Description of the type of packaging unit. Template has a list of optional values.
packaging.upc | String | No |  | Manufacturer-defined UPC Number for the item package.
packaging.gtin | String | No |  | Manufacturer-defined GTIN for the item package.
packaging.quantity | Real | No |  | Number of items in the package.
packaging.depth | Real | No |  | Depth of the item package.
packaging.height | Real | No |  | Height of the item package.
packaging.width | Real | No |  | Width of the item package.
packaging.cube | Real | No |  | Cube of the item package.
packaging.dimension_uom | String | No |  | Measurement type in which the dimension values are expressed.
packaging.weight | Real | No |  | Weight of the item's package.
packaging.weight_uom | String | No |  | Measurement type in which the weight value is expressed.
attributes.name | String | No |  | Name of the attribute.
attributes.value | String | No |  | Value of the attribute.

## Create Item
### API Endpoint - Create a New Catalog Item

 `POST`

This endpoint will be used to insert a new item into the organization's private CINX catalog.

<aside class="warning">
A private catalog item can be created from a public catalog (HPH) item. If either the CINX GUID or the HPH Item Code is known for the new item, simply insert the known value into the cinx_catalog_parent object of the Item template. This will add the item and create a linkage to the parent public catalog item. This link will allow the public catalog information to be included when requesting details about the item. This includes information such as Mfr List Prices, Labor Units, and links to Mfr documentation. If you submit new values for your private catalog item that are also available from the public item, your values will supersede the public catalog content.
</aside>

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request
  - This API call supports the submission of a single item

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-item-import?body=json**

URL Samples: 

  - Asynchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-item-import?body=json`
  - Synchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-item-import?body=json&synchronous=1`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload. | json
synchronous | Switch to have the payload processed synchronously. | 1

<aside class="notice">
By default the POST payload will be processed asynchronously.  See the optional URL parameters table for a synchronous option.
</aside>

## Modify Item
### API Endpoint - Modify a CINX Catalog Item

`PUT`

This endpoint will be used to modify an organization's private catalog item.

<aside class="warning">
If you submit new values for your private catalog item that are also available from the public item, your values will supersede the public catalog content. For example, if you submit a new weight value for an item that the HPH item already has a value, your new weight value will be used.
</aside>

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-item-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-item-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload. | json

<aside class="notice">
By default the PUT payload will be processed asynchronously.  See the optional URL parameters table for a synchronous option.
</aside>