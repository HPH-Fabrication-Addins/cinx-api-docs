# Get Catalog Items

## Full View - GUID
### API – GET Item Information using the “full” Response View – Item GUID

This request will be used to get an item’s information using the API’s “full” view and its’ CINX Private Catalog Item GUID.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/item/{Private Catalog Item GUID}?view=full

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/item/28468a6d-5858-1e50-af40-73d62f787a9a?view=full

## Full View  - Org Part
### API – GET Item Information using the “full” Response View – Org Part Number

This request will be used to get a catalog item’s information using the API’s “full” view.  You will need to include the item’s Org Part Number as a parameter in the URL.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/item/org/id/{Org Part Number}?view=full

URL Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/item/org/id/F01034S009?view=full

## Full View  - HPH Code
### API – GET Item Information using the “full” Response View – HPH Code

This request will be used to get an item’s information using the API’s “full” view and its HPH Code.

URL Pattern:

{api path}/sub/{B2B Id GUID}/items/hphcodes?values={HPH Item Code(s);comma-separated if multiple}&view=full

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/item/hphcode/006wb0212?view=full

## MCAA View - GUID
### API – GET Item Information using the “mcaa” Response View – Item GUID

This request will be used to get a catalog item’s information using the API’s “mcaa” view.  You will need to include the item’s Private Catalog GUID as a parameter in the URL.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/item/{Private Catalog Item GUID}?view=mcaa

URL Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/item/28468a6d-5858-1e50-af40-73d62f787a9a?view=mcaa

## MCAA View - Org Part
### API – GET Item Information using the “mcaa” Response View – Org Part Number

This request will be used to get a catalog item’s information using the API’s “mcaa” view.  You will need to include the item’s Org Part Number as a parameter in the URL.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/item/org/id/{Org Part Number}?view=mcaa

URL Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/item/org/id/F01034S009?view=mcaa

## MCAA View - HPH Code
### API – GET Item Information using the “mcaa” Response View – HPH Code

This request will be used to get a catalog item’s information using the API’s “mcaa” view.  You will need to include the item’s HPH Code as a parameter in the URL.

Single Item 

URL Pattern:

{api path}/sub/{B2B Subscription Id}/item/hphcode/{HPH Item Code}?view=mcaa

URL Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/item/hphcode/006wb0212?view=mcaa

**Multiple Items**

URL Pattern:


{api path}/sub/{B2B Id GUID}/items/hphcodes?values={HPH Item Code(s);comma-separated if multiple}&view=mcaa

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/items/hphcodes?values=006wb0212,006wb0214&view=mcaa


## MCAA Contents
### “mcaa” View Response Contents

## Custom View - GUID
### API – GET Item Information using the “custom” Response View – Item GUID

This request will can be used to submit a Private Catalog Item GUID with the response fields defined by the requesting URL.

URL Pattern:

{api path}/sub/{B2B Id GUID}/catalog/item/{Private Catalog Item GUID}?view=custom&fields={comma separated list of the fields}

Please see the CINX Private Catalog Item Data Options – Custom View section of this document for a listing of the available response fields.

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/item/28468a6d-5858-1e50-af40-73d62f787a9a?view=custom&fields=image,desc_long,hphcode,mfr_name,price_current,upc,weight,price_buy,price_sell,price_estimate,status,desc_org,desc_short,desc_mfr,partno_mfr,partno_org,system_id,specsheet,hier,xref,price_list_effective


## Custom View - HPH Code
### API – GET Item Information using the “custom” Response View – HPH Code

This request will can be used to submit a list of HPH Codes with the response fields defined by the requesting URL.

URL Pattern:

{api path}/sub/{B2B Id GUID}/items/hphcodes?values={HPH Item Code(s);comma-separated if multiple}&view=custom&fields={comma separated list of the fields}

Please see the CINX Private Catalog Item Data Options – Custom View section of this document for a listing of the available response fields.

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/items/hphcodes?values=006WB0212&view=custom&fields=image,desc_long,hphcode,mfr_name,price_current,upc,weight,price_buy,price_sell,price_estimate,status,desc_org,desc_short,desc_mfr,partno_mfr,partno_org,system_id,specsheet,hier,xref,price_list_effective

## Custom Options
### CINX Private Catalog Item Data Options – Custom View

## Item Count
### API – GET Catalog Item Count

This request is used to obtain the count of Catalog Items contained within an Org’s Private CINX catalog.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/items/ids?count=1

Sample:

http://api.cinx.com/sub/14b8fb3e-f62e-cd1c-b71f-fd5b1936d1b2/catalog/items/ids?count=1

The total_count parameter of the response object details the total items in the catalog.

## Item Ids
### API – GET Catalog Item Ids

This request is used to obtain the list of Catalog Item Ids contained within an Org’s Private CINX catalog.

Note:  If the catalog has a large number of items then the paging elements (offset and limit) should be used in conjunction with the URL.

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/items/ids

Sample:

http://api.cinx.com/sub/14b8fb3e-f62e-cd1c-b71f-fd5b1936d1b2/catalog/items/ids?offest=25&limit=100

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

https://api.cinx.com/sub/14b8fb3e-f62e-cd1c-b71f-fd5b1936d1b2/item/hphcode/012NI0018/price/history

## 