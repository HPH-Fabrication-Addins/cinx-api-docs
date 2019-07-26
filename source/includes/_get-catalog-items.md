# Get Catalog Items

## Full View - GUID
### API – GET Item Information using the “full” Response View – Item GUID

> The above code returns JSON structured like this:

```json

```

This request will be used to get an item’s information using the API’s “full” view and its’ CINX Private Catalog Item GUID.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/item/{Private Catalog Item GUID}?view=full

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/item/28468a6d-5858-1e50-af40-73d62f787a9a?view=full`

## Full View  - Org Part
### API – GET Item Information using the “full” Response View – Org Part Number

> The above code returns JSON structured like this:

```json

```

This request will be used to get a catalog item’s information using the API’s “full” view.  You will need to include the item’s Org Part Number as a parameter in the URL.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/item/org/id/{Org Part Number}?view=full

URL Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/item/org/id/F01034S009?view=full`

## Full View  - HPH Code
### API – GET Item Information using the “full” Response View – HPH Code

> The above code returns JSON structured like this:

```json

```

This request will be used to get an item’s information using the API’s “full” view and its HPH Code.

URL Pattern:

{api path}/sub/{B2B Id GUID}/items/hphcodes?values={HPH Item Code(s);comma-separated if multiple}&view=full

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/item/hphcode/006wb0212?view=full`

## MCAA View - GUID
### API – GET Item Information using the “mcaa” Response View – Item GUID

> The above code returns JSON structured like this:

```json

```

This request will be used to get a catalog item’s information using the API’s “mcaa” view.  You will need to include the item’s Private Catalog GUID as a parameter in the URL.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/item/{Private Catalog Item GUID}?view=mcaa

URL Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/item/28468a6d-5858-1e50-af40-73d62f787a9a?view=mcaa`

## MCAA View - Org Part
### API – GET Item Information using the “mcaa” Response View – Org Part Number

> The above code returns JSON structured like this:

```json

```

This request will be used to get a catalog item’s information using the API’s “mcaa” view.  You will need to include the item’s Org Part Number as a parameter in the URL.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/item/org/id/{Org Part Number}?view=mcaa

URL Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/item/org/id/F01034S009?view=mcaa`

## MCAA View - HPH Code
### API – GET Item Information using the “mcaa” Response View – HPH Code

> The above code returns JSON structured like this:

```json

```

This request will be used to get a catalog item’s information using the API’s “mcaa” view.  You will need to include the item’s HPH Code as a parameter in the URL.

Single Item 

URL Pattern:

{api path}/sub/{B2B Subscription Id}/item/hphcode/{HPH Item Code}?view=mcaa

URL Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/item/hphcode/006wb0212?view=mcaa`

**Multiple Items**

URL Pattern:


{api path}/sub/{B2B Id GUID}/items/hphcodes?values={HPH Item Code(s);comma-separated if multiple}&view=mcaa

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/items/hphcodes?values=006wb0212,006wb0214&view=mcaa`


## MCAA Contents
### “mcaa” View Response Contents

Response | Description
-------------- | --------------
status | Mfr product availability status.  A=Available with a list price, P=Available calling for pricing, D=Discontinued/Obsolete
mfr -> name_long | Manufacturer full name including reference to legal entity type
mfr -> name_short | Manufacturer abbreviated name
mfr -> name_logo | Link to the manufacturer's logo on the CINX CDN.
ids -> hph_code | HPH's unique identifier for a product
ids -> org_part | Customer defined part number
ids -> org_system_id | Customer defined auxiliary part identifier.
ids -> mfr_catalog | Manufacturer catalog/part number
ids -> mfr_order | Manufacturer order number
ids -> mfr_upc | Manufacturer UPC (12 digit - when defined by the mfr)
ids -> mfr_gtin | Manufacturer GTIN (14 digit - when defined by the mfr)
descriptions -> hph_long | HPH description excluding the item's size
descriptions -> hph_short | HPH "invoice" description that includes the item's size
descriptions -> org | Customer defined description
descriptions -> mfr | Manufacturer defined description
category | HPH top-level category value
sub_category | HPH secondary-level categorization value
cost_code | Customer defined default cost code
size | HPH-defined product size
weight -> value | Product's weight
weight -> uom | Weight unit-of-measure
price_mfr_list -> value | Manufacturer's list price
price_mfr_list -> uom | List price unit-of-measure
price_mfr_list -> effective | Manufacturer price sheet effective date
price_mfr_list -> price_sheet_number | Manufacturer price sheet number
price_mfr_list -> price_sheet_name | Manufacturer price sheet name
price_org_buy | Customer defined buy/purchase price
price_org_sell | Customer defined sell/change-order price
price_org_estimate | Customer defined estimate price
labor_units <array structure> |  
labor_units -> source | MCAA or PHCC
labor_units -> description | Labor unit description
labor_units -> value | Labor unit value
labor_units -> uom | Labor unit unit-of-measure
labor_units -> hph_labor_code | HPH defined unique identifier for the labor unit
images <array structure> |  
images -> url | Product picture url on the CINX CDN
images -> mime_type | Mime-type for the image
links <array structure> |  
links -> url | Manufacturer documentation url on the CINX CDN
links -> type | Documentation type (SDS, Spec, etc.)
links -> mime_type | Mime-type for the file
links -> date | Date the url was created
history -> created | Date the item was added to the customer's CINX catalog
history -> creator | User who added the item
history -> modified | Date of the last modification to the catalog item
history -> modifier | User who last modified the item
catalog_ref | Private catalog GUID



## Custom View - GUID
### API – GET Item Information using the “custom” Response View – Item GUID

This request will can be used to submit a Private Catalog Item GUID with the response fields defined by the requesting URL.

URL Pattern:

{api path}/sub/{B2B Id GUID}/catalog/item/{Private Catalog Item GUID}?view=custom&fields={comma separated list of the fields}

Please see the CINX Private Catalog Item Data Options – Custom View section of this document for a listing of the available response fields.

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/item/28468a6d-5858-1e50-af40-73d62f787a9a?view=custom&fields=image,desc_long,hphcode,mfr_name,price_current,upc,weight,price_buy,price_sell,price_estimate,status,desc_org,desc_short,desc_mfr,partno_mfr,partno_org,system_id,specsheet,hier,xref,price_list_effective`


## Custom View - HPH Code
### API – GET Item Information using the “custom” Response View – HPH Code

This request will can be used to submit a list of HPH Codes with the response fields defined by the requesting URL.

URL Pattern:

{api path}/sub/{B2B Id GUID}/items/hphcodes?values={HPH Item Code(s);comma-separated if multiple}&view=custom&fields={comma separated list of the fields}

Please see the CINX Private Catalog Item Data Options – Custom View section of this document for a listing of the available response fields.

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/items/hphcodes?values=006WB0212&view=custom&fields=image,desc_long,hphcode,mfr_name,price_current,upc,weight,price_buy,price_sell,price_estimate,status,desc_org,desc_short,desc_mfr,partno_mfr,partno_org,system_id,specsheet,hier,xref,price_list_effective`

## Custom Options
### CINX Private Catalog Item Data Options – Custom View

The list shown below is the available data options for constructing a Custom View URL.

<img src='images/subscription14.jpg'/>

**NOTES:**

API Request should have the field names comma-delimited without any spaces.

The response fields will be in the ordered that they were requested.

Fields without values in the contractor's catalog will be returned as null.

Requests for a field not yet supported will be returned with the requested field name and a value of **"Unsupported Field".**


## Item Count
### API – GET Catalog Item Count

This request is used to obtain the count of Catalog Items contained within an Org’s Private CINX catalog.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/items/ids?count=1

Sample:

`http://api.cinx.com/sub/14b8fb3e-f62e-cd1c-b71f-fd5b1936d1b2/catalog/items/ids?count=1`

The total_count parameter of the response object details the total items in the catalog.

## Item Ids
### API – GET Catalog Item Ids

This request is used to obtain the list of Catalog Item Ids contained within an Org’s Private CINX catalog.

Note:  If the catalog has a large number of items then the paging elements (offset and limit) should be used in conjunction with the URL.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/items/ids

Sample:

`http://api.cinx.com/sub/14b8fb3e-f62e-cd1c-b71f-fd5b1936d1b2/catalog/items/ids?offest=25&limit=100`

The response will contain three Ids for each item.  These Ids can be used in subsequent API calls to retrieve other product information.  The Ids are:

cinx_id: This value is the item’s Private Catalog GUID

hphcode: HPH Item Code

org_id: Org-defined product identifier

## List Price History
### API – GET Item List Price History – HPH Code


This request can be used to obtain the Manufacturer List Price history of an item.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/item/hphcode/{HPH Item Code}/price/history

URL Sample:

`https://api.cinx.com/sub/14b8fb3e-f62e-cd1c-b71f-fd5b1936d1b2/item/hphcode/012NI0018/price/history`
