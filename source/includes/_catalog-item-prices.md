# Catalog Item Prices

## Catalog Item Prices
### CINX Catalog Item Prices Discussion


<aside class="notice">
Catalog item prices are also output in the Get Catalog Item response views. Please see the Catalog Item section of this web site.
</aside>

This section of the site describes endpoints relating to different price types that can be associated with a catalog item.  There are four different types of prices that can be linked to a catalog item. Each price type is defined below.

**List Price**

Base price for a product that is normally set by the product's manufacturer. The List price is similar in concept to a car's MSRP price. For items in the HPH Plumbing/Mechanical catalog, HPH continuously updates the manufacturer list price as revisions are issued by the manufacturer. Each List price also has the Name and Number of the Manufacturer Price Sheet from which the price was obtained as well as the price's effective date. The Effective Date is the published date upon which the manufacturer implemented the new price.

**Buy Price** 

Price paid to a vendor for the purchase of a product or service. The Buy Price is often a discounted price from a previously established base price - which is commonly referred to as a List Price or a MSRP. Each catalog item in an organization's private catalog can have a Buy Price.

CINX also tracks buy prices that are used on transactions with vendors. Prices from Purchase Orders, Quotes, and Invoices are archived to allow for use by the organization when creating new transactions or performing analytics.

**Sell Price**

Price charged to a customer for a product or service. A Sell Price is normally related to a Buy Price or an established base price. Each catalog item in an organization's private catalog can have a Sell Price.

**Estimate Price**

Price for a product or service used in the estimating/bidding phase of a project. An Estimate Price is normally related to a Buy Price or an established base price. Each catalog item in an organization's private catalog can have a Estimate price.

**Supported API Services**

  - [Get an Item's List Prices using the HPH Code](#get-list-prices-hph-code)
  - [Get an Item's List Prices using a CINX Id](#get-list-prices-cinx-id)
  - [Get an Item's Price History using the HPH Code](#get-price-history-hph-code)
  - [Get an Item's Price History using an Organization Id](#get-price-history-org-id)
  - [Get an Item's Price History using a CINX Id](#get-price-history-cinx-id)

## Get List Prices - HPH Code
### API Endpoint – Get an Item's List Prices using an HPH Code

> The above code returns JSON structured like this:

```json
{
  "response": {},
  "rows": [{
      "cinx_guid": "04b7673a-eb84-11e0-8ba1-00137268a1bf",
      "current_price": false,
      "mfr_list_price": 22,
      "price_uom": "E",
      "effective_date": "2011-07-22",
      "price_sheet_type": "Wrot Solder Joint Fittings",
      "price_sheet_number": "W-162",
      "price_sheet_name": "Wrot Solder Joint Fittings",
      "cinx_price_sheet_guid": "773549d8-b995-11e0-b635-00137268a1bf"
    }]
}
```

`GET`

This endpoint will be used to get a catalog item’s manufacturer list prices using the HPH Item Code of the item.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/hph-code/{hph_code}/list-prices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/hph-code/012EK0018/list-prices`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
which | Defines how many list prices are returned. The all option is the default.| current, all
format | Defines the response format type. If not specified, json will be used. | json, xml

**Which Parameter Option Definitions** 

- **current**: returns only the current or most recent manufacturer list price for the item.
- **all**: returns all the list prices for the item. This will include the current list price and all historical prices. The result is sorted most recent to earliest.

## Get List Prices - CINX Id
### API Endpoint – Get an Item's List Prices using the CINX Id

> The above code returns JSON structured like this:

```json
{
  "response": {},
  "rows": [{
      "cinx_guid": "04b7673a-eb84-11e0-8ba1-00137268a1bf",
      "current_price": false,
      "mfr_list_price": 22,
      "price_uom": "E",
      "effective_date": "2011-07-22",
      "price_sheet_type": "Wrot Solder Joint Fittings",
      "price_sheet_number": "W-162",
      "price_sheet_name": "Wrot Solder Joint Fittings",
      "cinx_price_sheet_guid": "773549d8-b995-11e0-b635-00137268a1bf"
    }]
}
```

`GET`

This endpoint will be used to get a catalog item’s manufacturer list prices using the CINX Id of the item.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/guid/{cinx_guid}/list-prices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/item/guid/b023b15c-b996-11e0-b635-00137268a1bf/list-prices`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
which | Defines how many list prices are returned. The all option is the default.| current, all
format | Defines the response format type. If not specified, json will be used. | json, xml

**Which Parameter Option Definitions** 

- **current**: returns only the current or most recent manufacturer list price for the item.
- **all**: returns all the list prices for the item. This will include the current list price and all historical prices. The result is sorted most recent to earliest.

## Get Price History - HPH Code
### API Endpoint – Get an Item's Transaction Buy Price History using an HPH Code

`GET`

This endpoint will be used to get a catalog item’s buy price history using the HPH Item Code of the item. The response will contain a listing of the prices used on transactions.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/analytics/item/hph-code/{hph_code}/price-history**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/analytics/item/hph-code/012EK0018/price-history`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
source | Limits the prices to a specific transaction type.| po, poco, quote, invoice
project | Limits the prices to a specific project.| {cinx_project_guid}
vendor | Limits the prices to a specific vendor.| {cinx_commerce_guid}
include | Indicator if the same product from a different manufacturer should be included.| xrefs
view | Defines the content contained in the response. Summary is the default.| summary, list
format | Defines the response format type. If not specified, json will be used. | json, xml

**View Parameter Option Definitions** 

- **summary**: returns a summary of the price history.  Contents include the following price types: average, last, low,  and high.
- **list**: returns a listing of average price information into addition to all the prices that match the criteria defined by the URL parameters.

## Get Price History - Org Id
### API Endpoint – Get an Item's Transaction Buy Price History using an Org Item Id

`GET`

This endpoint will be used to get a catalog item’s buy price history using the CINX Id of the item. The response will contain a listing of the prices used on transactions.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/analytics/item/org-id/{org_item_id}/price-history**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/analytics/item/org-id/C90114/price-history`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
source | Limits the prices to a specific transaction type.| po, poco, quote, invoice
project | Limits the prices to a specific project.| {cinx_project_guid}
vendor | Limits the prices to a specific vendor.| {cinx_commerce_guid}
include | Indicator if the same product from a different manufacturer should be included.| xrefs
view | Defines the content contained in the response. Summary is the default.| summary, list
format | Defines the response format type. If not specified, json will be used. | json, xml

**View Parameter Option Definitions** 

- **summary**: returns a summary of the price history.  Contents include the following price types: average, last, low,  and high.
- **list**: returns a listing of average price information into addition to all the prices that match the criteria defined by the URL parameters.

## Get Price History - CINX Id
### API Endpoint – Get an Item's Transaction Buy Price History using a CINX Id

`GET`

This endpoint will be used to get a catalog item’s buy price history using the CINX Id of the item. The response will contain a listing of the prices used on transactions.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/analytics/item/guid/{cinx_guid}/price-history**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/analytics/item/guid/b023b15c-b996-11e0-b635-00137268a1bf/price-history`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
source | Limits the prices to a specific transaction type.| po, poco, quote, invoice
project | Limits the prices to a specific project.| {cinx_project_guid}
vendor | Limits the prices to a specific vendor.| {cinx_commerce_guid}
include | Indicator if the same product from a different manufacturer should be included.| xrefs
view | Defines the content contained in the response. Summary is the default.| summary, list
format | Defines the response format type. If not specified, json will be used. | json, xml

**View Parameter Option Definitions** 

- **summary**: returns a summary of the price history.  Contents include the following price types: average, last, low,  and high.
- **list**: returns a listing of average price information into addition to all the prices that match the criteria defined by the URL parameters.

## Item Price History View - Summary
### API Item Price History Response View Definition - Summary

```json
{
  "response": {},
  "rows": [{
    "include_xrefs": false,
    "counts": {
      "total": 2,
      "primary": 2,
      "xrefs": 0
    },
    "dates": {
      "first": "2019-08-29",
      "last": "2019-09-04"
    },
    "average": {
      "price": 13.18,
      "currency": "USD"
    },
    "low": {
      "item": {
        "is_xref": false,
        "cinx_guid": "b023b15c-b996-11e0-b635-00137268a1bf",
        "hph_code": "012EK0018",
        "org_item_id": null,
        "org_system_id": null,
        "description": "1\" WROT CXC 90 ELBOW",
        "manufacturer": {
          "cinx_org_id": "org-0000-1179",
          "name": "Elkhart Products Corporation"
        }
      },
      "price": 8.25,
      "price_uom": "E",
      "currency": "USD",
      "quantity": 100,
      "date": "2019-08-29",
      "bom": {
        "cinx_guid": "df8a088c-1fd6-5b8f-99f3-ba6d38d8cd82",
        "type": "BOM-PO",
        "number": "",
        "name": "PO-000006",
        "cinx_bom_item_guid": "9cf3ec4f-c162-5262-bb7e-f3bcbec8550d"
      },
      "project": {
        "cinx_guid": "0929772a-fbaf-59ae-bf9b-0a5275f4a847",
        "number": "PRJ-2019-10",
        "name": "PRJ-2019-10"
      },
      "vendor": {
        "cinx_commerce_guid": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f",
        "number": "99999",
        "name": "Keegan Supply"
      }
    },
    "high": {
      "item": {
        "is_xref": false,
        "cinx_guid": "b023b15c-b996-11e0-b635-00137268a1bf",
        "hph_code": "012EK0018",
        "org_item_id": null,
        "org_system_id": null,
        "description": "1\" WROT CXC 90 ELBOW",
        "manufacturer": {
          "cinx_org_id": "org-0000-1179",
          "name": "Elkhart Products Corporation"
        }
      },
      "price": 18.11,
      "price_uom": "E",
      "currency": "USD",
      "quantity": 15,
      "date": "2019-09-04",
      "bom": {
        "cinx_guid": "d15c0678-f8dc-5a03-a9b9-c7a303cd9837",
        "type": "BOM-PO",
        "number": "PO-000007",
        "name": "PO-000007",
        "cinx_bom_item_guid": "a0532c2c-adf3-5190-8aaf-4be57bf3928a"
      },
      "project": {
        "cinx_guid": null,
        "number": null,
        "name": null
      },
      "vendor": {
        "cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
        "number": "V101",
        "name": "Hilti-6"
      }
    },
    "last": {
      "item": {
        "is_xref": false,
        "cinx_guid": "b023b15c-b996-11e0-b635-00137268a1bf",
        "hph_code": "012EK0018",
        "org_item_id": null,
        "org_system_id": null,
        "description": "1\" WROT CXC 90 ELBOW",
        "manufacturer": {
          "cinx_org_id": "org-0000-1179",
          "name": "Elkhart Products Corporation"
        }
      },
      "price": 18.11,
      "price_uom": "E",
      "currency": "USD",
      "quantity": 15,
      "date": "2019-09-04",
      "bom": {
        "cinx_guid": "d15c0678-f8dc-5a03-a9b9-c7a303cd9837",
        "type": "BOM-PO",
        "number": "PO-000007",
        "name": "PO-000007",
        "cinx_bom_item_guid": "a0532c2c-adf3-5190-8aaf-4be57bf3928a"
      },
      "project": {
        "cinx_guid": null,
        "number": null,
        "name": null
      },
      "vendor": {
        "cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
        "number": "V101",
        "name": "Hilti-6"
      }
    }
  }]
}
```

When requesting an item's price history from the CINX API there are two view options. 

The table below defines the fields output using the **summary** view option.

## Item Price History View - List
### API Item Price History Response View Definition - List

```json
{
  "response": { },
  "rows": [{
    "include_xrefs": false,
    "counts": {
      "total": 2,
      "primary": 2,
      "xrefs": 0
    },
    "dates": {
      "first": "2019-08-29",
      "last": "2019-09-04"
    },
    "average": {
      "price": 13.18,
      "currency": "USD"
    },
    "prices": [{
        "cinx_item_guid": "b023b15c-b996-11e0-b635-00137268a1bf",
        "hph_code": "012EK0018",
        "org_item_id": null,
        "org_system_id": null,
        "description": "1\" WROT CXC 90 ELBOW",
        "mfr_name": "Elkhart Products Corporation",
        "price": 8.25,
        "uom": "E",
        "currency": "USD",
        "quantity": 100,
        "date": "2019-08-29",
        "bom_cinx_guid": "BOM-PO",
        "bom_type": "BOM-PO",
        "bom_number": "",
        "bom_name": "PO-000006",
        "vendor_number": "99999",
        "vendor_name": "Keegan Supply",
        "project_number": "PRJ-2019-10",
        "project_name": "PRJ-2019-10",
        "is_xref": false,
        "is_low_price": true,
        "is_high_price": true,
        "is_first_date": true,
        "is_last_date": true
      },
      {
        "cinx_item_guid": "b023b15c-b996-11e0-b635-00137268a1bf",
        "hph_code": "012EK0018",
        "org_item_id": null,
        "org_system_id": null,
        "description": "1\" WROT CXC 90 ELBOW",
        "mfr_name": "Elkhart Products Corporation",
        "price": 18.11,
        "uom": "E",
        "currency": "USD",
        "quantity": 15,
        "date": "2019-09-04",
        "bom_cinx_guid": "BOM-PO",
        "bom_type": "BOM-PO",
        "bom_number": "PO-000007",
        "bom_name": "PO-000007",
        "vendor_number": "V101",
        "vendor_name": "Hilti-6",
        "project_number": null,
        "project_name": null,
        "is_xref": false,
        "is_low_price": false,
        "is_high_price": true,
        "is_first_date": false,
        "is_last_date": true
      }
    ]
  }]
}
```
When requesting an item's price history from the CINX API there are two view options. 

The table below defines the fields output using the **list** view option.