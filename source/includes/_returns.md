# Returns

## Return Definition
### CINX Object Definition - Return

A CINX Return is a contractor initiated process of returning previously purchased products to the vendor from which it was sourced. Part of the return process is receiving an RMA from a vendor which will be attached the the return. In CINX an organization may establish the return reasons and actions that are available to users when returning products.

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must have a unique number
  - Must have at least one item before it can be submitted

**Supported API Services**

  - [Get a List of Returns](#get-return-list)
  - [Get a Return](#get-return)
  - [Get a Return Template](#get-return-template)
  - [Get a Return Number](#get-return-number)
  - [Create a Return](#create-return)
  - [Modify a Return](#modify-return)

## Get Return List
### API Endpoint - Get a List of Returns

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "03dfb081-fc43-5196-8b58-d8277278bc59",
			"number": "R000001",
			"name": "R000001",
			"workflow_status": "RMA REQUESTED",
			"rma_number": null,
			"date_rma_expires": null,
			"reason_name": "Wrong Product",
			"action_name": "Replace Item",
			"assigned_to": "Will Stone",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"vendor_number": "H125",
			"vendor_name": "Hilti",
			"po_number": "PO-123",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
			"external_references": [],
			"item_count": 1
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of returns. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/returns**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/returns`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
vendor | Limits results to a single vendor. | {organization's vendor number}
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

## Get Return
### API Endpoint - Get a Return

`GET`

This endpoint will be used to get the details of a specific return. Note: This response will include the return’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/return/{cinx_guid}**

The cinx_guid will be the return's CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/return/03dfb081-fc43-5196-8b58-d8277278bc59`

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "3fe371f8-5295-59c3-9987-c1da2ac20144",
		"locked": "0",
		"number": "R1245454",
		"name": "R1245",
		"workflow_status": "RMA RECEIVED",
		"counts": {
			"credits": 0,
			"charges": 0,
			"items": 1
		},
		"dates": {
			"created": "2019-06-13",
			"last_modified": "2019-06-13",
			"rma_requested": "2019-06-13",
			"rma_issued": "2019-06-14",
			"rma_expires": "2019-06-28",
			"call_tag_pickup": "2019-06-19",
			"processed": "",
			"shipped": "",
			"closed": ""
		},
		"assigned_to": {
			"cinx_guid": "4a23ff84-9d61-5ab3-95c9-3870cb2727bd",
			"name": "Karl Stone",
			"email": "karlstone@cinx.com"
		},
		"customer": {
			"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
			"number": "C101",
			"name": "WTS Mechanical -DEV"
		},
		"vendor": {
			"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
			"number": "V101",
			"name": "Hilti"
		},
		"rma_request": {
			"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
			"name": "Will Stone",
			"email": "willstone@cinx.com"
		},
		"vendor_rma": {
			"number": "RMA-541254",
			"issued_by": {
				"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
				"name": "Will Stone",
				"email": "willstone@cinx.com"
			},
			"call_tag": "0",
			"instructions": "",
			"file_url": null
		},
		"return_processed": {
			"cinx_guid": null,
			"name": null,
			"email": null
		},
		"return_shipped": {
			"cinx_guid": null,
			"name": null,
			"email": null
		},
		"return_closeed": {
			"cinx_guid": null,
			"name": null,
			"email": null
		},
		"delivery": {
			"address1": "995 Industrial Park Rd",
			"address2": "",
			"address3": "",
			"city": "Littleton",
			"state": "NH",
			"postal_code": "03561",
			"country": "USA",
			"ship_via": "SUPPLIER TRUCK",
			"fob_type": "PREPAID AND CHARGED TO CUSTOMER",
			"ship_from": "",
			"attention": "Frank",
			"location_type": "BRANCH",
			"location_name": null,
			"instructions": "Vendor's shipping instructions for the return.",
			"terms": "",
			"packing_slip_number": "134546588",
			"total_weight": 1452,
			"was_insured": "1",
			"declared_value": 4567
		},
		"purchase_order": {
			"cinx_guid": "80e6d9c8-d2e4-5aaa-9bd3-3957430741dd",
			"number": "PO-123",
			"name": "PO123"
		},
		"vendor_delivery": {
			"cinx_guid": null,
			"number": null,
			"name": null
		},
		"project": {
			"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
			"number": "WTS-2017-03",
			"name": "WTS-2017-03"
		},
		"external_references": [],
		"credits": [],
		"charges": [],
		"items": [{
			"cinx_guid": "92d1bbb2-2c21-57e1-8fbc-540c4b7ea8bd",
			"sequence": 1,
			"quantity": 2,
			"unit_price": 7.596,
			"price_uom": "E",
			"currency": "USD",
			"credit_percentage": 0,
			"credit_unit_price": 0,
			"workflow_status": "RMA RECEIVED",
			"allow_substitutes": true,
			"hph_code": "118CH1430",
			"org_item_id": null,
			"org_system_id": null,
			"mfr_part_number": null,
			"upc": "61194203404",
			"size": "4",
			"description": null,
			"mfr_name": null,
			"item_type": "MATERIAL",
			"file_url": null,
			"vendor": {
				"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
				"number": "V101",
				"name": "Hilti",
				"item_id": "org-0001-4221",
				"system_id": null,
				"rma_number": "RMA-541254",
				"restock_fee": 0,
				"return_code": null
			},
			"return_reason": {
				"cinx_guid": "57d44251-1b29-5882-bedb-ac59fdc6b90a",
				"code": "22-item",
				"name": "Wrong Product"
			},
			"return_action": {
				"cinx_guid": "f51cc612-1f47-5f74-b47a-088e2f47d207",
				"code": "41-replace",
				"name": "Replace Item"
			},
			"purchase_order": {
				"cinx_guid": "80e6d9c8-d2e4-5aaa-9bd3-3957430741dd",
				"number": "PO-123",
				"name": "PO123"
			},
			"project": {
				"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
				"number": "WTS-2017-03",
				"name": "HPH HQ Renovation"
			},
			"job_cost": {
				"cinx_phase_guid": null,
				"phase_name": "124",
				"cinx_material_cost_code_guid": null,
				"material_cost_code_name": null,
				"cinx_category_guid": null,
				"category_name": null
			},
			"taxes": {
				"taxable": true,
				"cinx_guid": null,
				"tax_group_name": null,
				"tax_type": null,
				"tax_rate": 0,
				"tax_amount": 0
			},
			"attributes": []
		}]
	}]
}
```

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Return Number
### API Endpoint - Get a New Return Number

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getReturnNumber(cinx_api_token)
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"return": "RET-000001"
		}
    ]
}
```
`GET`

This endpoint will be used to get a value to be used in the number field of a new return.

**Notes**

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/return**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/return`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml