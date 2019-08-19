# PO Change Orders

## PO Change Order Definition
### CINX Object Defintion - PO Change Order

A CINX Purchase Order Change Order is created when changes need to be made to a previously submitted purchase order. Example of changes include: changing a price or quantity; adding or modifying job costing information; adding or removing a item row. 

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must be linked to a previously created purchase order
  - PO Change Orders will be automatically numbered by the system
  - Must have a procurement status
  - Must have at least one item before it can be submitted
  - Will be locked after it is submitted

**Supported API Services**

  - [Get a List of PO Change Orders](#get-po-co-list)
  - [Get a PO Change Order](#get-po-co)
  - [Get a PO Change Order Template](#get-po-co-template)
  - [Create a PO Change Order](#create-po-co)
  - [Modify a PO Change Order](#modify-po-co)

## Get PO CO List
### API Endpoint - Get a List of PO Change Orders

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "a9863525-d926-5441-9f9c-aa47a285a19b",
			"number": "-01",
			"name": "PO123-01",
			"description": null,
			"workflow_status": "SUBMITTED",
			"procurement_status": "ORDERED",
			"po_number": "PO-123",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
			"vendor_number": "H125",
			"vendor_name": "Hilti",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_submitted": "2019-06-06",
			"submitted_by": "Will Stone",
			"date_need_by": "2019-06-14",
			"phase": "First Floor",
			"material_cost_code": "101-1025",
			"category": null,
			"tax_group": "TAX-03",
			"terms": "0/0",
			"erp_status": "NOT SUBMITTED",
			"links": [],
			"item_count": 2
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of PO Change Orders. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/pocos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/pocos`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
procurement | Limits results to a specific procurement status. | NOT ORDERED, ORDER PENDING, ORDERED, BACK-ORDERED, DELIVERED, RETURNED, CANCELLED, CLOSED, ON-HOLD, INVOICE-APPROVED
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, ERP PENDING, ERP ACCEPTED, ERP FAILED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}

## Get PO CO
### API Endpoint - Get a PO Change Order

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "a9863525-d926-5441-9f9c-aa47a285a19b",
		"locked": "1",
		"number": "PO123-01",
		"name": "PO123-01",
		"description": null,
		"terms": "1.5/10",
		"user_comment": null,
		"procurement_status": "ORDERED",
		"workflow_status": "SUBMITTED",
		"erp_status": "NOT SUBMITTED",
		"allow_substitutes": "0",
		"submitter": {
			"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
			"name": "Will Stone",
			"email": "willstone@cinx.com"
		},
		"dates": {
			"created": "2019-06-06",
			"last_modified": "2019-06-06",
			"order_by": null,
			"need_by": "2019-06-14",
			"submitted": "2019-06-06",
			"received": null
		},
		"customer": {
			"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
			"number": "C101",
			"name": "WTS Mechanical"
		},
		"vendor": {
			"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
			"number": "V101",
			"name": "Hilti"
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
			"attention": "",
			"location_type": "FABRICATION SHOP",
			"location_name": null,
			"instructions": ""
		},
		"job_cost_defaults": {
			"cinx_phase_guid": "3b61f993-69b5-5db3-a367-2d204321c857",
			"phase_name": "First Floor",
			"cinx_material_cost_code_guid": "314f6a13-56b3-5c3f-b14e-10d159e4c5c0",
			"material_cost_code": "101-1025",
			"cinx_category_guid": null,
			"category_name": null
		},
		"taxes": {
			"taxable": true,
			"cinx_guid": "9a962b97-145c-522f-bf1a-e1ad4be4b5a8",
			"tax_group_name": "TAX-03",
			"tax_type": "Use",
			"tax_rate": 5
		},
		"external_references": [],
		"counts": {
			"credits": 0,
			"charges": 0,
			"items": 2
		},
		"credits": [],
		"charges": [],
		"items": [{
			"cinx_guid": "73d55d4b-4436-5539-aad2-7f2a11666146",
			"sequence": 1,
			"quantity": 3,
			"unit_price": 270.05,
			"price_uom": "E",
			"currency": "USD",
			"date_need_by": "2019-06-11",
			"allow_substitutes": true,
			"hph_code": "326ZU6542",
			"org_item_id": null,
			"org_system_id": null,
			"mfr_part_number": null,
			"upc": "67024006745",
			"size": "4",
			"description": "Floor, Z1400 Adjustable, 4",
			"mfr_name": null,
			"item_type": "MATERIAL",
			"vendor": {
				"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
				"number": "V101",
				"name": "Hilti",
				"item_id": null,
				"system_id": null,
				"cinx_quote_guid": null,
				"quote_number": null
			},
			"requisition": {
				"cinx_guid": null,
				"number": null,
				"name": null
			},
			"purchase_order": {
				"cinx_guid": "80e6d9c8-d2e4-5aaa-9bd3-3957430741dd",
				"number": "PO-123",
				"name": "PO123",
				"procurement_status": "ORDERED",
				"unit_price": 270.05,
				"price_source_type": "USER",
				"price_uom": "E",
				"currency": "USD",
				"quantities": {
					"ordered": 1,
					"received": 0,
					"invoiced": 0,
					"back_ordered": 0
				}
			},
			"project": {
				"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
				"number": "WTS-2017-03",
				"name": "HPH HQ Renovation"
			},
			"delivery": {
				"ship_via": null,
				"deliver_to": null,
				"location_type": "JOB SITE",
				"location_name": null,
				"instructions": null,
				"labeling_instructions": null,
				"packaging_instructions": null
			},
			"work_breakdown": {
				"work_order_id": null,
				"work_order_name": null,
				"spool_id": null,
				"spool_name": null,
				"building_name": null,
				"level": "MAIN",
				"space": null,
				"sub_space": null,
				"system": "GREASE WASTE UG",
				"arch_symbol": null,
				"tag": null
			},
			"job_cost": {
				"cinx_phase_guid": null,
				"phase_name": "124",
				"cinx_material_cost_code_guid": null,
				"material_cost_code": null,
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
			"design": {
				"model_item_guid": null,
				"model_name": null,
				"model_file": null,
				"drawing_number": "P1.0",
				"drawing_name": null
			}
		}]
	}]
}
```

`GET`

This endpoint will be used to get the details of a specific PO Change Order.  Note: This response will include the PO Change Order’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/poco/{cinx_guid}**

The cinx_guid will be the PO Change Order’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/poco/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

## Get PO CO Template
### API Endpoint - Get a PO Change Order Template

`GET`

This endpoint will be used to get a CINX Template for a PO Change Order.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/poco**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/poco`


The table below defines the input fields within the template.

## Create PO CO
### API Endpoint - Create a PO Change Order

`POST`

This endpoint will be used to create a new PO Change Order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-poco-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-poco-import?body=json`

<aside class="notice">
The POST payload will be processed asynchronously.
</aside>

## Modify PO CO
### API Endpoint - Modify a PO Change Order

`PUT`

This API endpoint will be used to modify an existing CINX PO Change Order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-poco-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-poco-import?body=json`

<aside class="notice">
The PUT payload will be processed asynchronously.
</aside>