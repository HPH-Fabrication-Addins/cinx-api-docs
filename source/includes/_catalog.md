# Catalog

## Catalog Definition
### CINX Object Definition - Private Catalog

A CINX catalog is a collection of items grouped together in a CINX database structure. Catalogs may contain
construction materials, sub-contract services, rental equipment, and other content necessary for the
execution of a construction project or maintenance of a building.

Every CINX organization can have their own private catalog that can be accessed by the organization's users in the CINX user interface or via the API. A private catalog can be populated by copying items from a CINX public catalog (HPH) or by creating new private items. Private items will not be linked to an HPH item and therefore will have to be managed and updated by the organization.

With a CINX private catalog, an organization can:
  - create a hierarchy classification system to group items
  - create their own product identifiers and descriptions for items
  - manage different pricing levels
  - create exports and update files for different software systems

**Supported API Services**

  - [Get Catalog Line Roots](#get-catalog-line-roots)
  - [Get a Catalog Line Children](#get-catalog-line-children)
  - [Get a Catalog Items Ids](#get-catalog-items-ids)
  - [Get a Catalog Stats](#get-catalog-stats)
  - [Catalog Items](#catalog-item)
  - Catalog/App Updates


## Get Catalog Line Roots
### API Endpoint – Get a Private Catalog's Line Root Levels

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

`GET`

This endpoint will be used to get a listing of a private catalog line's children (child lines).

URL Pattern: **{api path}/{api_version}/sub/{api_token}/line/{line_cinx_guid}/children**

The line_cinx_guid is the CINX Id of the parent line.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/line/3cfc2cdf-c96a-5b00-a572-33d8f343f0c6/children`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Catalog Items Ids
### API Endpoint – Get a Private Catalog Items' Ids

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

`GET`

This endpoint will be used to get a private catalog's statistics for items, lines and manufacturers.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/catalog/stats**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/catalog/stats`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml