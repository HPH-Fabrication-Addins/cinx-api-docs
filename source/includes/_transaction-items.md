# Transaction Items
## Get Items
### API – GET BOM ITEMs

This request will be used to get a list of the BOM-ITEMs for a given BOM.

URL Pattern:

{api path}/sub/{B2B Id GUID}/bom/{BOM GUID}/items?view=details

NOTE:  If you remove the ?view=details the API will return a list of only the IDs for the BOM-ITEMs.

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/bom/22cd75f0-c431-71a3-59b7-9d0620764587/items?view=details`

## Create Item - HPH Code
### API – Create a BOM ITEM – HPH Code

This request will be used to create a new BOM-ITEM for a given BOM using the item’s HPH Code.

URL Pattern:

{api path}/sub/{B2B Id GUID}/bom/{BOM GUID}/add/item? hphcode={HPH Item Code}

NOTE: The item (HPH Code) must be present in the data source tied to the B2B subscription.

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/bom/22cd75f0-c431-71a3-59b7-9d0620764587/add/item?hphcode=464PL0011`

## Get Item Details
### API – GET BOM ITEM Details

This request will be used to get the details of a specific BOM-ITEM.

URL Pattern:

{api path}/sub/{B2B Id GUID}/bom/item/{BOM-ITEM GUID}/

## Modify Item
### API – Modify a BOM ITEM

This request will be used to modify a BOM-ITEM.

URL Pattern:

{api path}/sub/{B2B Id GUID}/bom/item/{BOM-ITEM GUID}/modify? values={JSON Structure}

The values section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the CINX BOM-Item JSON Structures section of this document for a listing of the available JSON structures.

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/bom/item/579df238-832d-c868-a8b8-91181321840e/modify? values={"cost_code":"7464"}`

## JSON Structures
### CINX BOM-Item JSON Structures

The JSON structures shown below can be used in API calls to Modify a BOM-Item.

If the structure is an array, all elements of the array must be submitted.  

Description
“description”:”value”

Size
“size”:”value”

Manufacturer Item Catalog Number
“mfr_catalog”:”value”

Manufacturer Name
“mfr_name”:”value”

Quantity
“qty_entered”:”value”

Order By Date
“order_by”:”date value”

Deliver By Date
“deliver_by”:”date value”

Allow Substitutions
“allow_substitutions”:”boolean value”

Packaging Instructions
“packaging”:”value”

Labeling Instructions
“labeling”:”value”

Delivery Instructions
“delivery”:”value”

Weight
“weight”:”value”

Vendor Name (wholesale distributor)
“vendor_name”:”value”

Vendor Availability
“vendor_availability_type”:”value”
Available options are: STOCKED, NON-STOCKED, MADE-TO-ORDER, NEW – TO BE RELEASED, SELL UNTIL DEPLETED, OBSOLETE, {user defined}

Vendor Availability Location
“vendor_availability_location”:”value”


Vendor Item Id
“vendor_id”:”value”

Vendor Item System Id
“vendor_system_id”:”value”

Construction Status
“construction_status”:”value”
Available options are: NOT INSTALLED, INSTALLED, TESTED, COMMISSIONED, OPERATIONAL, {user defined}

Project Phase
“wbs_phase”:”value”

Accounting Category
“wbs_category”:”value”

Cost Code
“cost_code”:”value”

Architectural Symbol
“arch_symbol”:”value”

Drawing
“wbs_drawing”:”value”

Level/Floor
“wbs_floor”:”value”

Space/Zone/Section
“wbs_space”:”value”

Sub-Space/Sub-Zone/Room
“wbs_sub_zone”:”value”

System/Service
“wbs_system”:”value”

Spool
“wbs_spool”:”value”

Work Order
“wbs_workorder”:”value”

Material
“wbs_material”:”value”

Item Type
“wbs_item_type”:”value”

Buy Price – Base Price
“buy_base_price”:”value”

Buy Price – Multiplier Value
“buy_price_multiplier”:”value”

Buy Price – Unit Cost
“buy_unit_cost”:”value”

Buy Price – Unit-of-Measure
“buy_uom”:”value”

Buy Price – Currency
“buy_currency”:”value”
Default value: USD

Sell Price – Base Price
“sell_base_price”:”value”

Sell Price – Multiplier Value
“sell_price_multiplier”:”value”

Sell Price – Unit Cost
“sell_unit_cost”:”value”

Sell Price – Unit-of-Measure
“sell_uom”:”value”

Sell Price – Currency
“sell_currency”:”value”
Default value: USD

Labor Unit
“labor_unit”:”value”

Labor Unit Multiplier
“labor_unit_multiplier”:”value”

Labor Cost
“labor_cost”:”value”

Labor Cost Currency
“labor_currency”:”value”
Default value: USD

Attributes (array)
“attributes”:[{”name”:”name”,”value”: “value”}]

## Delete Item
### API – Delete a BOM ITEM

This request will be used to remove a BOM-Item.

URL Pattern:

{api path}/sub/{B2B Id GUID}/bom/item/{BOM-ITEM GUID}/delete

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/bom/item/12a0ddcd-462e-2615-fe7c-d238238a96cf/delete`








