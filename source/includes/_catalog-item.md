# Catalog Item

## Create - HPH Code
### API – Add a New Catalog Item – HPH Code

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Item_Link->addItemFromCatalog",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/catalog/add/item",
        "format": "json",
        "start_time": 1564132149.572,
        "total_time": 0.75662302970886,
        "record_count": 1,
        "total_count": 0
    },
    "rows": [
        {
            "cinx_id": {
                "type": "ITEM-LINK",
                "domain": "org-0001-4030",
                "id": "01f9c181-c624-5475-ad84-1b7eeb511155" //Private Catalog Item GUID
            }
        }
    ]
}
```

This request will be used to submit a HPH Item Code for an item and have it added to an Org’s private catalog. 

URL Pattern:

{api path}/sub/{B2B Subscription Id}/catalog/add/item?hphcode={HPH Item Code}

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/add/item?hphcode=005GR0006`

The GUID shown in the **id** field is the item’s CINX Private Catalog GUID


## Create - Non-HPH Code
### API – Create a non-HPH Private Catalog Item

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Item_Link->addItemFromCatalog",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/catalog/add/item",
        "format": "json",
        "start_time": 1564132149.572,
        "total_time": 0.75662302970886,
        "record_count": 1,
        "total_count": 0
    },
    "rows": [
        {
            "cinx_id": {
                "type": "ITEM-LINK",
                "domain": "org-0001-4030",
                "id": "01f9c181-c624-5475-ad84-1b7eeb511155" //Private Catalog Item GUID
            }
        }
    ]
}
```

This request will be used to create a Private Catalog Item that is not linked to an HPH Item.  Please note that this URL will require a valid CINX user GUID.  This will be used to indicate who created the item.

URL Pattern:

{api path}/sub/{B2B Id GUID}/catalog/add/non-catalog/item?values={JSON Structure}

The values section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Private Catalog Item JSON Structures** section of this document for a listing of the available JSON structures.

Basic Sample: 

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/add/non-catalog/item?values={"mfr_name":"Rubbermaid","descriptions":[{"type":"LONG","value":"30GAL Black Trash Can"},{"type":"SHORT","value":"Trash Can"}],"pkg_ids":[{"type":"MFR CATALOG","value":"101"}]}`

Expanded Sample: 

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/add/non-catalog/item?user=dc3aecca-f2ec-ee6e-eee9-6d96d45390fa&values={%22mfr_name%22:%22Rubbermaid%22,%22descriptions%22:[{%22type%22:%22LONG%22,%22value%22:%2230GAL%20Black%20Trash%20Can%22},{%22type%22:%22SHORT%22,%22value%22:%22Trash%20Can%22}],%22pkg_ids%22:[{%22type%22:%22MFR%20CATALOG%22,%22value%22:%22101%22},{%22type%22:%22UPC%22,%22value%22:%22464645656410%22}],%22size%22:%20{%22type%22:%22PHYSICAL%22,%22value%22:%2230%22,%22uom%22:%22GALLON%22},%22prices%22:[{%22type%22:%22BUY%22,%22cdoc%22:%22%22,%22value%22:%2210.256%22,%22price_uom%22:%22E%22,%22date_updated%22:%22%22,%22user_cdoc%22:%22dc3aecca-f2ec-ee6e-eee9-6d96d45390fa%22,%22source_method%22:%22USER%22},{%22type%22:%22ESTIMATED%22,%22cdoc%22:%22%22,%22value%22:%2211.256%22,%22price_uom%22:%22E%22,%22date_updated%22:%22%22,%22user_cdoc%22:%22dc3aecca-f2ec-ee6e-eee9-6d96d45390fa%22,%22source_method%22:%22USER%22}],%22weight%22:%222.300%22,%22weight_uom%22:%22LBS%22,%22depth%22:%2223.00%22,%22height%22:%2238.00%22,%22width%22:%2223.00%22,%22cube%22:%22123%22,%22dimension_uom%22:%22INCHES%22,%22attributes%22:[{%22name%22:%22Color%22,%22value%22:%22Black%22},{%22name%22:%22Body%20Style%22,%22value%22:%22Tapered%22}],%22cost_code%22:%22123456%22,%22pkg_status%22:%22A%22}`

The GUID shown in the **id** field is the item’s CINX Private Catalog GUID.

## Modify - GUID
### API – Modify a CINX Private Catalog Item – using a CINX GUID

> The above code returns JSON structured like this:

```json
```

This request will be used to modify a Private Catalog Item using its CINX Item GUID.

URL Pattern:

{api path}/sub/{B2B Id GUID}/catalog/item/{CINX ITEM GUID}/modify? values={JSON Structure}

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Private Catalog Item JSON Structures** section of this document for a listing of the available JSON structures.

Sample: 

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/item/3635ded0-2c4a-758f-0ba1-0f11455561ea/modify?values={"size":{"type":"PHYSICAL","value":"40","uom":"GALLON"}}`

## JSON Structures
### CINX Private Catalog Item JSON Structures

The JSON structures shown below can be used in API calls to **Create** or **Modify** CINX Private Catalog Items.

If the structure is an array, all elements of the array must be submitted. 

**Manufacturer Name (required)**

“mfr_name”:”name”

**Item Identifiers (array)**

“pkg_ids”:[{”type”:”type name”,”value”: “value”}]

Available “type names” are: **MFR CATALOG, MFR ORDER, UPC, GTIN, ORG ID, ORG SYSTEM ID**

**Descriptions (array)**

“descriptions”:[{”type”:”type name”,”value”: “value”}]

Available “type names” are: **LONG, SHORT, ORG**

**Size**

“size”:{”type”:”type name”,”value”: “value”,”uom”:”value”}

**Prices (array)**

“prices”:[{”type”:”type name”,”cdoc”:null,”value”: “value” ,”price_uom”: “price_uom value”,”date_updated”:””,”user_cdoc”:”{user guid}”,”source_method”:”USER”}]

Available “type names” are: **BUY, SELL, ESTIMATED**

“cdoc”: please submit a **null**

Available “price uoms” are: **E, T, C, M**

“date_updated”: **datetime format (yyyy-mm-dd hh:mm:ssZ)**

“source_method”: **please submit “USER”**

**Price Multiplier**

“multiplier”:{“cdoc”:null,”code”:”code value”,”name”: “name”}]

**Attributes (array)**

“attributes”:[{”name”:”name”,”value”: “value”}]

**Physical Properties**

“weight”:”value”

“weight_uom”: “value”

“depth”:”value”

“height”:”value”

“width”:”value”

“cube”:”value”

“dimension_uom”:”value”

**Default Cost Code**

“cost_code_value”:”value”

**Product Availability Status**

“pkg_status”:”value”

Available “values” are: **A,D,P**

## Delete
### API – DELETE a Catalog Item (based on an CINX Item GUID)

> The above code returns JSON structured like this:

```json
```

This request will be used to delete an item from an Org’s Private CINX catalog.  Please note that this API call requires the item’s CINX Private Catalog Item GUID.

URL Pattern:

{api path}/sub/{B2B Id GUID}/catalog/item/{CINX ITEM GUID}/delete

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/catalog/item/3635ded0-2c4a-758f-0ba1-0f11455561ea/delete`

