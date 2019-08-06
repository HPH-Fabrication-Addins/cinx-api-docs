# Back-Orders

## Back-Order Definition
### CINX Object Defintion - Back-Order

A back-order is an item from a submitted PO that cannot be delivered by the requested delivery date, and for which the customer is prepared to wait for the vendor to replenish its inventory.

**Dependencies and Business Rules**

  - The item must be on a CINX PO

**Supported API Services**

  - [Get a List of Back-Orders](#get-back-order-list)
  - [Get a Back-Order](#get-back-order)
  - [Get a Back-Order Template](#get-back-order-upd-template)


## Get Back-Order List
### API Endpoint - Get a List of Back-Orders

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "076bd4bb-d6d9-5096-96f2-ec105d0562b1",
			"date_expected_delivery": null,
			"date_po_needr_by": null,
			"date_informed": null,
			"date_last_updated": null,
			"reason": null,
			"quantity_back_ordered": 1,
			"quantity_shipped": 0,
			"quantity_po": 1,
			"org_item_id": null,
			"vendor_item_id": null,
			"mfr_part_number": null,
			"mfr_order": null,
			"hph_code": "326ZU6542",
			"upc": "67024006745",
			"org_description": "Floor, Z1400 Adjustable, 4",
			"cinx_description": null,
			"mfr_description": null,
			"mfr_name": null,
			"delivery_location_type": null,
			"delivery_location_name": "",
			"vendor_number": "",
			"vendor_name": "Hilti-6",
			"work_order_id": null,
			"work_order_name": null,
			"spool_id": null,
			"spool_name": null,
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"po_number": "P19-062819",
			"po_name": "P19-062819",
			"po_submitted_by": "Will Stone"
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of back-orders. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/back-orders**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/back-orders`


**OPTIONAL URL PARAMETERS**

**delivery**: will limit results to a specific delivery type location

  - Available options are: JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR

**project**: will limit results to a single project

  - {cinx_project_guid}

**vendor**: will limit results to a single vendor

  - {cinx_commerce_guid}
  
**po_guid**: will limit results to a specified CINX purchase order

  - {CINX_PO_Id}

## Get Back-Order
### API Endpoint - Get a Back_Order

`GET`

This endpoint will be used to get the details of a specific back-order.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/back-order{po_item_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/back-order/e73c118f-1ee9-57e0-9c79-1775c1a04b81`


## Get Back-Order Upd Template
### API Endpoint - Get a Back-Order Update Template

`GET`

This endpoint will be used to get a CINX Template for a updating a back-ordered item.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/back-order**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/back-order`


The table below defines the input fields within the template.