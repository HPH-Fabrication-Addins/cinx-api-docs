# PO Acknowledgments

## PO Acknowledgment Definition
### CINX Object Definition - PO Acknowledgment

A CINX PO Acknowledgment is a document a vendor prepares in response to a customer’s Purchase Order.  PO Acknowledgments will contain order confirmation information from the vendor. The exact content's of a PO Acknowledgment will be dependent on which ERP system the vendor uses. Common information on a PO Acknowledgment include an order status, item prices, and shipping/delivery information.

**Supported API Services**

  - [Get a List of PO Acknowledgments](#get-po-acknowledgment-list)
  - [Get a PO Acknowledgment](#get-po-acknowledgment)


## Get PO Acknowledgment List
### API Endpoint - Get a List of PO Acknowledgments

> The above code returns JSON structured like this:

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "e462c9e9-8e93-59e2-9308-97851ad44511",
		"number": "0926656",
		"name": "0926656",
		"description": null,
		"date_received": "2021-01-15",
		"assigned_to": null,
		"workflow_status": "ACCEPTED",
		"po_number": "PO-000047",
		"po_name": "PO-000047",
		"vendor_number": "99999",
		"vendor_name": "Keegan Supply",
		"ship_via": "SUPPLIER TRUCK",
		"delivery_location_type": "JOB SITE",
		"delivery_location_name": "011521-2-test",
		"project_number": "WTS-2019-06",
		"project_name": "Martha's Restaurant Upgrade",
		"phase": null,
		"material_cost_code": null,
		"category": null,
		"tax_group": null,
		"external_references": [],
		"item_counts": {
			"accepted": 5,
			"accepted_with_changes": 1,
			"rejected": 0,
			"unacknowledged": -7
		}
	}]
}
```
`GET`

This endpoint will be used to get a list of PO Acknowledgments. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po-ack**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po-acks`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ERP PENDING, ERP ACCEPTED, ERP FAILED
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

## Get PO Acknowledgment
### API Endpoint - Get a PO Acknowledgment

`GET`

This endpoint will be used to get the details of a specific PO Acknowledgment.  Note: This response will include the PO Acknowledgment’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po-ack/{cinx_guid}**

The cinx_guid will be the PO Acknowledgment’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po-ack/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "e462c9e9-8e93-59e2-9308-97851ad44511",
		"locked": "1",
		"number": "0926656",
		"name": "0926656",
		"description": null,
		"assigned_to": null,
		"workflow_status": "ACCEPTED",
		"date_received": "2021-01-15",
		"submitter": {
			"cinx_guid": "4a23ff84-9d61-5ab3-95c9-3870cb2727bd",
			"name": "Karl Stone",
			"email": "karlstone@cinx.com"
		},
		"vendor": {
			"cinx_commerce_guid": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f",
			"number": "99999",
			"name": "Keegan Supply"
		},
		"customer": {
			"cinx_commerce_guid": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f",
			"number": "88300",
			"name": "WTS Mechanical"
		},
		"po": {
			"cinx_guid": "567347c9-fa72-5895-94bd-7c42ec3cba82",
			"number": "PO-000047",
			"name": "PO-000047"
		},
		"project": {
			"cinx_guid": "ebe9d0ef-3234-545d-aeb3-2065875fd37d",
			"project_number": "WTS-2019-06",
			"project_name": "Martha's Restaurant Upgrade"
		},
		"delivery": {
			"address1": "995 Industrial Park Rd",
			"address2": "",
			"address3": "",
			"city": "LITTLETON",
			"state": "NH",
			"postal_code": "03561",
			"country": "USA",
			"ship_via": "SUPPLIER TRUCK",
			"fob_type": null,
			"ship_from": null,
			"attention": null,
			"location_type": "JOB SITE",
			"location_name": "011521-2-test",
			"instructions": null
		},
		"external_references": [],
		"item_counts": {
			"accepted": 5,
			"accepted_with_changes": 1,
			"rejected": 0,
			"unacknowledged": -7
		},
		"items": [{
			"cinx_guid": "db6a5e09-f6fb-5f96-80e3-c060ede5ead6",
			"sequence": 1,
			"acknowledgement_status": "ACCEPTED",
			"unit_price": 4.5,
			"price_uom": "E",
			"currency": "USD",
			"hph_code": "012EK0700",
			"org_item_id": "242672720334661141",
			"org_system_id": "242672720334661141",
			"mfr_part_number": "10031578",
			"upc": "683264315785",
			"size": "5/8\"",
			"description": "107_MT_2 Street EL Medium FtgxC",
			"mfr_name": "Elkhart Products Corporation",
			"item_type": "MATERIAL",
			"vendor": {
				"cinx_commerce_guid": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f",
				"number": "99999",
				"name": "Keegan Supply",
				"item_id": "CIS9E",
				"item_system_id": "1291237"
			},
			"project": {
				"cinx_guid": "ebe9d0ef-3234-545d-aeb3-2065875fd37d",
				"project_number": "WTS-2019-06",
			"project_name": "Martha's Restaurant Upgrade"
			},
			"delivery": {
				"shipping_status": "NOT SCHEDULED",
				"date_scheduled_ship": null,
				"ship_via": null,
				"deliver_to": null
			},
			"work_breakdown": {
				"work_order_id": null,
				"work_order_name": null,
				"sppol_id": null,
				"spool_name": null,
				"building_name": null,
				"level": null,
				"space": null,
				"sub_space": null,
				"system": null,
				"arch_symbol": null,
				"tag": null
			},
			"job_cost": {
				"cinx_phase_guid": null,
				"phase_name": null,
				"cinx_material_cost_code_guid": null,
				"material_cost_code": null,
				"cinx_category_guid": null,
				"category_name": null
			},
			"design": {
				"model_item_guid": null,
				"model_name": null,
				"model_file": null,
				"drawing_number": null,
				"drawing_name": null
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