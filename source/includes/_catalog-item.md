# Catalog Item

## Item Definition
### CINX Object Defintion - Catalog

A CINX Catalog Item is a building material product or construction related service that is stored within a CINX catalog.

A CINX Catalog is a collection of items grouped together in a CINX database structure. Catalogs may contain construction materials, sub-contract services, rental equipment, and other content necessary for the execution of a construction project or maintenance of a building.

A CINX orgranization will have a private catalog where items can be stored. An organization's private CINX catalog can be built from the items from CINX public catalogs including the HPH Plumbing/Mechanical list. Private items not associated with a CINX public catalog can also be inserted into an organization's private catalog. Thus, the responsibility for maintaining that item will be the organization.

**Labor Units**

CINX has worked with industry labor unit providers (MCAA and PHCC) to store their labor units as CINX Catalogs. HPH has also linked labor units to our HPH Plumbing/Mechanical catalog items. The CINX Get Item API can return labor units when the **details** view is used. Adding a labor parameter to the URL will enable the output of labor units.  **Labor units will be returned ONLY if the organziation is authorized by the labor unit author to access them**

**Dependencies and Business Rules**

  - A catalog item must be associated with a CINX catalog
  - A catalog item must have a description
  - A catalog item must have a manufacturer

**Supported API Services**

  - Get an Item using the HPH Code
  - Get an Item using an Organization Id
  - Get an Item using a CINX Id
  - Get a Purchase Order Number
  - Create a Catalog Item from an HPH Code
  - Get a Catalog Item Template
  - Create a Catalog Item
  - Modify a Catalog Item
  - Delete a Catalog Item

## Get Item - HPH Code
### API Endpoint – Get an Item using an HPH Code

> The above code returns JSON structured like this:

```json
See this page for the contents of a **compact** response.  EMBED LINK

See this page for the contents of a **details** response.  EMBED LINK
```

This endpoint will be used to get a catalog item’s information using the HPH Code of an item.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/hph-code/{hph_code}?view={view_option}&labor={labor_type}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/hph-code/012EK0018?view=details`

HTTP Method: `GET`

**View Options** 

- **compact**: returns a small set of item information fields. This is the default view if one is not specified.
- **details**: returns a comprehensive set of item information

**Labor Options** 

- **all**: returns all industry labor units the organization is authorized to use
- **mcaa**: returns the MCAA labor units if the organization is authorized to access them
- **phcc**: returns the PHCC labor units if the organization is authorized to access them

## Get Item - Org Id
### API Endpoint – Get an Item using an Org Item Id

> The above code returns JSON structured like this:

```json
See this page for the contents of a **compact** response.  EMBED LINK

See this page for the contents of a **details** response.  EMBED LINK
```

This endpoint will be used to get a catalog item’s information using the organization's item id.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/org-id/{org_item_id}?view={view_option}&labor={labor_type}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/org-id/C90114?view=details`

HTTP Method: `GET`

**View Options** 

- **compact**: returns a small set of item information fields. This is the default view if one is not specified.
- **details**: returns a comprehensive set of item information

**Labor Options** 

- **all**: returns all industry labor units the organization is authorized to use
- **mcaa**: returns the MCAA labor units if the organization is authorized to access them
- **phcc**: returns the PHCC labor units if the organization is authorized to access them

## Get Item - CINX Id
### API Endpoint – Get an Item using the CINX Id

> The above code returns JSON structured like this:

```json
See this page for the contents of a **compact** response.  EMBED LINK

See this page for the contents of a **details** response.  EMBED LINK
```

This endpoint will be used to get a catalog item’s information using the item's CINX Id.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/hph-code/{hph_code}?view={view_option}&labor={labor_type}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/guid/012EK0018?view=details`

HTTP Method: `GET`

**View Options** 

- **compact**: returns a small set of item information fields. This is the default view if one is not specified.
- **details**: returns a comprehensive set of item information

**Labor Options** 

- **all**: returns all industry labor units the organization is authorized to use
- **mcaa**: returns the MCAA labor units if the organization is authorized to access them
- **phcc**: returns the PHCC labor units if the organization is authorized to access them

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
    "sub-category": "Pressure Wrot-Solder",
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
      "cinx_id": "org-0000-1411",
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

When requesting a catalog from the CINX API there are two view options. 

The table below defines the fields output using the **details** view option.

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
    "sub-category": "Pressure Wrot-Solder",
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
When requesting a catalog from the CINX API there are two view options. 

The table below defines the fields output using the **compact** view option.

## Create Item - HPH Code
### API Endpoint – Add a New Catalog Item using an HPH Code

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "cinx_id": {
             UPDATE CONTENTS
            }
        }
    ]
}
```

This endpoint will be used to submit an HPH Item Code for an item and have it added to an organization's private catalog. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/catalog-item/add?hph-code={hph-code}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/catalog-item/add?hph-code=001BS0200F`

HTTP Method: `POST`

## Get Item Template
### API Endpoint - Get a Catalog Item Template

This request will be used to get a CINX Template for a catalog item.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/item**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/item`

HTTP Method: `GET`

The table below defines the fields within the template.

## Create Item
### API Endpoint – Create a non-HPH Private Catalog Item

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "cinx_id": {
                
                UPDATE CONTENTS
        }
    ]
}
```

This endpoint will be used to create a private catalog item that is not linked to an HPH Item.  

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-item-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-item-import?body=json`

HTTP Method: `POST`

## Modify Item
### API Endpoint – Modify a CINX Private Catalog Item using a CINX Id


This endpoint will be used to modify a private catalog item that is not linked to an HPH Item.  

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-item-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-item-import?body=json`

HTTP Method: `PUT`


## Delete Item
### API Endpoint – Delete a Catalog Item using a CINX Id

> The above code returns JSON structured like this:

```json
```

This endpoint will be used to remove an item from an organization's private CINX catalog.  Please note that this API call requires the item’s CINX Item Id.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/{cinx_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/item/d9863525-d926-5441-9f9c-aa47a285a19b`

HTTP Method: `DELETE`
