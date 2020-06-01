# Catalog

## Catalog Definition
### CINX Object Definition - Private Catalog

A CINX catalog is a collection of items grouped together in a CINX database structure. Catalogs may contain construction materials, sub-contract services, rental equipment, and other content necessary for the execution of a construction project or maintenance of a building.

Every CINX organization can have their own private catalog that can be accessed by the organization's users in the CINX user interface or via the API. A private catalog can be populated by copying items from a CINX public catalog (HPH) or by creating new private items. Private items will not be linked to an HPH item and therefore will have to be managed and updated by the organization.

With a CINX private catalog, an organization can:

  - create a hierarchy classification system to group items
  - create their own product identifiers and descriptions for items
  - manage different pricing levels
  - create exports and update files for different software systems

**Catalog Lines**

Each organization can create its own hierarchy system used to classify and group items together. This hierarchy system is called Lines. The CINX Line system allows a company to create as many levels as needed to group their items. The highest level of lines are named the root level lines in this API documentation. Children lines are those that are linked to a higher level line. The line API responses contain line children counts, this will allow you to determine if you are at the bottom level of the hierarchy. The response will also contain a count of items that belong to that level of the hierarchy. 

**Catalog Manufacturers**

Each private catalog line can be linked to a manufacturer. A manufacturer is the company that produces the item. If the private catalog is copied from a CINX public catalog item, then the API can report information regarding that manufacturer. Using the Manufacturer name is often a convenient way to navigate the items in a catalog. This API provides several API calls to work with manufacturer information related to the items in the organization's private catalog.

**Manufacturer Price Sheet Types**

In construction sub-contracting trades it is common for product manufacturers to publish price sheets. A price sheet will contain a grouping of products and their corresponding prices. Some manufacturers publish multiple price sheets. It is relatively common for a manufacturer to have separate price sheets for products that are produced for a similar base material (Wrot copper fittings) or have different price sheets for the type of end product (Ball Valves). The CINX API refers to each type or version of the manufacturer price sheets as a Price Sheet Type.

**Manufacturer Price Sheets**

Manufacturers will frequently issue price sheet revisions with updated prices and product offerings. These revisions will be linked to a price sheet type and will normally have a price sheet number, name, and effective date that the prices will be implemented. In this API these individual instances of a price sheet type will be refereed to as Price Sheets. 

<aside class="notice">
If an item is discontinued by a manufacturer, then the last price and price sheet for that item will be included in the API response. So, it is possible that we requesting a list of price sheets for a private catalog there will be older price sheets returned.
</aside>

**Supported API Services**

  - [Get Catalog Line Roots](#get-catalog-line-roots)
  - [Get a Catalog Line Children](#get-catalog-line-children)
  - [Get a Catalog Line Items](#get-catalog-line-items)
  - [Get Catalog Manufacturers](#get-catalog-manufacturers)
  - [Get Manufacturer Price Sheet Types](#get-price-sheet-types)
  - [Get Price Sheet Instances](#get-price-sheets)
  - [Get Catalog Items Ids](#get-catalog-items-ids)
  - [Get a Catalog Stats](#get-catalog-stats)

## Get Catalog Line Roots
### API Endpoint – Get a Private Catalog's Line Root Levels

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "268625fa-38cf-5085-9e08-89be31e395e7",
    "name": "(Unassigned)",
    "description": "All items not currently assigned to a specific LINE.",
    "image_url": "http://cdn.dev.cinx.biz/assets/org-0000-7413/image-hier-no-image.jpg",
    "has_children": false,
    "children_count": 0,
    "item_count": 8,
    "parent": {
      "cinx_guid": null,
      "name": null,
      "description": null
    }
  }]
}
```

`GET`

This endpoint will be used to get a listing of a company's private catalog root level line hierarchies.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/lines/roots**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/lines/roots`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Catalog Line Children
### API Endpoint – Get a Private Catalog Line's Children Levels

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "012773c1-d75c-50d8-b53d-7af936fb9311",
    "name": "Fittings - Compression",
    "description": "Fittings - Compression",
    "image_url": "https://cdn.cinx.com/assets/org-0000-0001/image-hier-no-image.jpg",
    "has_children": true,
    "children_count": 2,
    "item_count": 317,
    "parent": {
      "cinx_guid": "3cfc2cdf-c96a-5b00-a572-33d8f343f0c6",
      "name": "Copper",
      "description": ""
    }
  }]
}
```

`GET`

This endpoint will be used to get a listing of a private catalog line's children (child lines).

URL Pattern: **{api path}/{api_version}/sub/{api_token}/line/{line_cinx_guid}/children**

The line_cinx_guid is the CINX Id of the parent line.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/line/3cfc2cdf-c96a-5b00-a572-33d8f343f0c6/children`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Catalog Line Items
### API Endpoint – Get a Private Catalog's Items for a given Line

`GET`

This endpoint will be used to get a listing of a private catalog's items for a given line.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/line/{line_cinx_guid}/items**

The line_cinx_guid is the CINX Id of the parent line.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/line/3cfc2cdf-c96a-5b00-a572-33d8f343f0c6/items`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
view | Defines the level of content in the response. | compact, details, list-price
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 20 will be used. | Integer

**View** 

- **compact**: returns a small set of item information fields. This is the default view if one is not specified. Please see [Compact View](#line-item-view-compact) for a definition of the output.
- **details**: returns a comprehensive set of item information. Please see [Details View](#line-item-view-details) for a definition of the output.
- **list-price**: returns the current list price and price sheet information for each item. Please see [Details View](#line-item-view-list-price) for a definition of the output.

## Line Item View - Compact
### API Line Item Response View Definition - Compact

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
When requesting the items for a catalog line from the CINX API there are three view options.

The table below defines the fields output using the **compact** view option.

## Line Item View - Details
### API Line Item Response View Definition - Details

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
When requesting the items for a catalog line from the CINX API there are three view options. 

The table below defines the fields output using the **details** view option.

## Line Item View - List-Price
### API Line Item Response View Definition - List Price

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "b0f01d82-b996-11e0-b635-00137268a1bf",
    "mfr_list_price": 18.11,
    "price_uom": "E",
    "effective_date": "2019-04-01",
    "price_sheet_type": "WROT COPPER",
    "price_sheet_number": "WROT-0419",
    "price_sheet_name": "Wrot Copper Fittings",
    "cinx_price_sheet_guid": "3d4c7bfc-49b0-11e9-9891-00137268a1bf"
  }]
}
```
When requesting the items for a catalog line from the CINX API there are three view options. 

The table below defines the fields output using the **list-price** view option.

## Get Catalog Manufacturers
### API Endpoint – Get a Private Catalog's Manufacturers

```json
{
  "response": {},
  "rows": [{
    "cinx_org_id": "org-0000-1698",
    "name": "Aegis Technologies, Inc.",
    "short_name": "Aegis",
    "logo": "http://cdn.dev.cinx.biz/assets/org-0000-1698/logo/030_0000-0000.JPG",
    "item_count": 235
  }]
}
```

`GET`

This endpoint will be used to get a listing of a company's private catalog manufacturers.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/mfrs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/mfrs`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

<aside class="warning">
The manufacturers included in this response will be based on the items linked to a master HPH item. CINX does not have the required information for private manufacturers created by the company.
</aside>

## Get Price Sheet Types
### API Endpoint – Get a Manufacturer's Price Sheet Types

```json
{
  "response": {},
  "rows": [{
      "price_sheet_type_guid": "90f7b284-4b7b-11e1-9e73-00137268a1bf",
      "name": "Brass Fittings",
      "description": "Brass Fittings",
      "status": "A",
      "manufacturer": {
        "name": "Brass-Craft",
        "cinx_org_id": "org-0000-1074"
      }
    }
  ]
}
```

`GET`

This endpoint will be used to get a listing of a specific manufacturer's price sheet types.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/mfr/{mfr_cinx_org_id}/price-sheet-types**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/mfr/org-0000-1074/price-sheet-types`

The mfr_cinx_org_id is the CINX Org Id for the manufacturer and can be obtained from the Get Mfrs API response.

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Price Sheets
### API Endpoint – Get a Manufacturer Price Sheet Type's Price Sheets

```json
{
  "response": {},
  "rows": [{
    "price_sheet_guid": "154dae84-2150-11e8-9eb7-00137268a1bf",
    "name": "Brass Fittings",
    "number": "0302A",
    "date_effective": "2018-03-01",
    "date_release": "",
    "date_expiration": "",
    "sequence_number": "1",
    "version": "1",
    "status": "A"
  }]
}
```

`GET`

This endpoint will be used to get a listing of price sheet instances for a given price sheet type that are used on items in the company's private catalog.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/mfr/price-sheet-types/{price-sheet-type-cinx-guid}/price-sheets**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/mfr/price-sheet-type/90f7b284-4b7b-11e1-9e73-00137268a1bf/price-sheets`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

<aside class="notice">
If an item is discontinued by a manufacturer, then the last price and price sheet for that item will be included in the API response. So, it is possible that we requesting a list of price sheets for a private catalog there will be older price sheets returned.
</aside>

## Get Catalog Items Ids
### API Endpoint – Get a Private Catalog Items' Ids

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "a9c63fa4-ec0d-50eb-ac78-f7c279a996ba",
    "hph_code": "152BC4703",
    "org_item_id": null,
    "org_system_id": null
  }]
}
```

`GET`

This endpoint will be used to get a listing of a private catalog items' product identifiers.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/items/ids**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/items/ids?offset=50&limit=5`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

## Get Catalog Stats
### API Endpoint – Get a Private Catalog Statistics
```json
{
  "response": {},
  "rows": [{
    "items": {
      "private": 6,
      "total": 7457
    },
    "lines": {
      "root": 5,
      "total": 996
    },
    "manufacturers": {
      "total": 19
    }
  }]
}
```

`GET`

This endpoint will be used to get a private catalog's statistics for items, lines and manufacturers.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/catalog/stats**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/catalog/stats`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml