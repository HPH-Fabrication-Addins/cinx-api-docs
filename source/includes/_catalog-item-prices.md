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
  - [Get an Item's List Prices a CINX Id](#get-list-prices-cinx-id)

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

URL Pattern: **{api path}/{api_version}/sub/{api_token}/item/guid/{cinx_guid/list-prices**

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
### API Endpoint – Get an Item's Buy Price History using an HPH Code

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
view | Defines the content contained in the response.| summary, list
format | Defines the response format type. If not specified, json will be used. | json, xml

**View Parameter Option Definitions** 

- **summary**: returns a summary of the price history.  Contents include the following price types: last, low, high, and ..........
- **list**: returns a listing of all the prices that match the criteria defined by the URL parameters.
