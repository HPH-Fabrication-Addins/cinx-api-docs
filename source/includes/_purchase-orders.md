# Purchase Orders

## PO Definition
### CINX Object Defintion - Purchase Order

A CINX Purchase Order is a compilation of parts that are being ordered. The list might be for a whole project, phase, system, pre-fab work-order, spool, or a general list created by a project foreman in the field. 

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must have a unique number
  - Must have a procurement status
  - Must have at least one item before it can be submitted
  - Will be locked after it is submitted

**Supported API Services**

  - [Get a List of Purchase Orders](#get-po-list)
  - [Get a Purchase Order](#get-po)
  - [Get a Purchase Order Template](#get-po-template)
  - [Get a Purchase Order Number](#get-po-number)
  - [Create a Purchase Order](#create-po)
  - [Modify a Purchase Order](#modify-po)
  - [Get a List of Change Orders for a Purchase Order](#get-po-change-orders)
  - [Get a List of Deliveries for a Purchase Order](#get-po-deliveries)
  - [Get a List of Invoices for a Purchase Order](#get-po-invoices)
  - [Get a List of Returns for a Purchse Order](#get-po-returns)
  - [Get a List of Back-Orders for a Purchse Order](#get-po-back-orders)
  - [Update a Purchase Order's ERP Status](#erp-status-update)

## Get PO List
### API Endpoint - Get a List of Purchase Orders

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "80e6d9c8-d2e4-5aaa-9bd3-3957430741dd",
			"number": "PO-123",
			"name": "PO123",
			"description": null,
			"workflow_status": "SUBMITTED",
			"procurement_status": "ORDERED",
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_order_by": "2019-06-07",
			"date_submitted": "2019-06-06",
			"submitted_by": "Will Stone",
			"date_need_by": "2019-06-11",
			"date_received": "",
			"links": [],
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"phase": "First Floor",
			"material_cost_code": "101-1025",
			"category": null,
			"tax_group": "TAX-03",
			"terms": "0/0",
			"quote_number": null,
			"quote_name": null,
			"erp_status": "NOT SUBMITTED",
			"item_count": 15
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of purchase orders. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/pos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/pos`


**OPTIONAL URL PARAMETERS**

**delivery**: will limit results to a specific delivery type location

  - Available options are: JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR

**procurement**: will limit results to a specific procurement status

  - Available options are: NOT ORDERED, ORDER PENDING, ORDERED, BACK-ORDERED DELIVERED, RETURNED, CANCELLED, CLOSED, ON-HOLD, INVOICE-APPROVED

**workflow**: will limit results to a specific workflow status

  - Available options are: N-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, ERP PENDING, ERP ACCEPTED, ERP FAILED

**erp**: will limit results to a specific erp status

  - Available options are: NOT SUBMITTED, PENDING, SUBMITTED, APPLIED

**project**: will limit results to a single project

  - {cinx_project_guid}

**vendor**: will limit results to a single vendor

  - {cinx_commerce_guid}

**ship_via**: will limit results to a specific ship via value

  - Available options are: SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE

**deliver_date**: will limit results to a specific need-by or delivery-by date

  - Date Format: YYYY-MM-DD

**submitter**: will limit results to a specified CINX user

  - {CINX_User_Id}

**number**: will limit results to a specified transaction number

  - {transaction_number}

## Get PO
### API Endpoint - Get a Purchase Order

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "8185cbd2-18c6-5cdc-b3ed-25795aabbfcc",
			"number": "PO-111111",
			"name": "PO-111111",
			"description": "No Description Entered",
			"terms": "1.5/10",
			"user_comment": "Test User Comment",
			"procurement_status": "ORDERED",
			"workflow_status": "SUBMITTED",
			"erp_status": "NOT SUBMITTED",
			"allow_substitutes": "1",
			"submitter": {
				"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
				"name": "Will Stone",
				"email": "willstone@cinx.com"
			},
			"dates": {
				"created": "2019-07-29",
				"last_modified": "2019-07-29",
				"order_by": null,
				"need_by": "2019-08-02",
				"submitted": "2019-07-29"
			},
			"vendor": {
				"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
				"number": "V101",
				"name": "Hilti-6"
			},
			"project": {
				"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
				"number": "WTS-2017-03",
				"name": "WTS-2017-03"
			},
			"delivery": {
				"address1": null,
				"address2": null,
				"address3": null,
				"city": null,
				"state": null,
				"postal_code": null,
				"country": "USA",
				"ship_via": "SUPPLIER TRUCK",
				"fob_type": "PREPAID",
				"ship_from": "BRANCH",
				"attention": "Site Forman",
				"location_type": "JOB SITE",
				"location_name": "HPH",
				"instructions": "Handle with care"
			},
			"job_cost_defaults": {
				"cinx_phase_guid": "3b61f993-69b5-5db3-a367-2d204321c857",
				"phase_name": "First Floor",
				"cinx_material_cost_code_guid": "5d9b83d0-a3de-5475-959d-04b92fd4de75",
				"material_cost_code": "UG-123",
				"cinx_category_guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
				"category_name": "MAT"
			},
			"taxes": {
				"taxable": true,
				"cinx_guid": "7c42f24f-766e-5220-bc7e-cce8048dbb57",
				"tax_group_name": "TAX-12",
				"tax_type": "Sales",
				"tax_rate": 8
			},
			"external_references": [{
				"type": "FAB SHOP TRANSACTION REF",
				"description": "",
				"value": "465465498796189fgf349"
			}],
			"charges": [],
			"credits": [],
			"counts": {
				"items": 1,
				"charges": 0,
				"credits": 0
			},
			"items": [{
				"cinx_guid": "11208a81-c1d2-53c8-8b46-272d65b3e295",
				"sequence": 1,
				"unit_price": 18.11,
				"price_uom": "E",
				"currency": "USD",
				"price_source_type": "MFR LIST",
				"date_need_by": "2019-07-15",
				"allow_substitutes": true,
				"hph_code": "012NI0018",
				"org_item_id": null,
				"org_system_id": null,
				"mfr_part_number": "9055750",
				"upc": "039923312969",
				"size": "1\"",
				"description": "1\" WROT CXC 90 ELBOW",
				"mfr_name": "NIBCO, Inc.",
				"item_type": "MATERIAL",
				"procurement_status": "ORDERED",
				"quantities": {
					"ordered": 3,
					"received": 0,
					"invoiced": 0
				},
				"vendor": {
					"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
					"number": "V101",
					"name": "Hilti-6",
					"item_id": null,
					"system_id": null,
					"cinx_quote_guid": null,
					"quote_number": null
				},
				"requisition": {
					"cinx_guid": "2e5763f6-f7be-5179-9109-5e81014fb5b5",
					"number": "REQ-19-001",
					"name": "REQ-19-001",
				},
				"project": {
					"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
					"number": "WTS-2017-03",
					"name": "WTS-2017-03"
				},
				"delivery": {
					"ship_via": "SUPPLIER TRUCK",
					"deliver_to": "Site Forman",
					"location_type": "JOBSITE",
					"location_name": "HPH",
					"instructions": "Handle with double extra care",
					"labeling_instructions": "HPH-789879",
					"packaging_instructions": "Wrapped pallets"
				},
				"work_breakdown": {
					"work_order_id": null,
					"work_order_name": "WO-8774512",
					"spool_id": null,
					"spool_name": "SPL-4897987",
					"building_name": "HPH1",
					"level": "1",
					"space": "Lobby",
					"sub_space": "Domestic Cold Water",
					"system": null,
					"arch_symbol": "ELB-045",
					"tag": null
				},
				"job_cost": {
					"cinx_phase_guid": "3b61f993-69b5-5db3-a367-2d204321c857",
					"phase_name": "First Floor",
					"cinx_material_cost_code_guid": "5d9b83d0-a3de-5475-959d-04b92fd4de75",
					"material_cost_code": "UG-123",
					"cinx_category_guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
					"category_name": "MAT"
				},
				"taxes": {
					"taxable": true,
					"cinx_guid": "7c42f24f-766e-5220-bc7e-cce8048dbb57",
					"tax_group_name": "TAX-12",
					"tax_type": "SALES",
					"tax_rate": 8,
					"tax_amount": 0
				},
				"design": {
					"model_item_guid": "234234q32fqw5324f3232",
					"model_name": "HPH Model 1",
					"model_file": "HPHModell.rvt",
					"drawing_number": "PLB-01",
					"drawing_name": "Plumbing 01"
				}
		}]	
    }]
}
```
`GET`

This endpoint will be used to get the details of a specific purchase order.  Note: This response will include the purchase order’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid}**

The cinx_guid will be the purchase orders’s CINX Id.

## Get PO Template
### API Endpoint - Get a Purchase Order Template

```json
{
	"response": {},
	"rows": [{
		"doc_info": {},
		"template": {
			"cinx_guid": null,
			"number": null,
			"name": null,
			"description": null,
			"terms": null,
			"user_comment": null,
			"procurement_status": null,
			"workflow_status": null,
			"erp_status": null,
			"allow_substitutes": true,
			"dates": {
				"order_by": null,
				"need_by": null
			},
			"vendor": {
				"cinx_commerce_guid": null,
				"number": null
			},
			"project": {
				"cinx_guid": null,
				"number": null
			},
			"delivery": {
				"address1": null,
				"address2": null,
				"address3": null,
				"city": null,
				"state": null,
				"postal_code": null,
				"country": null,
				"ship_via": null,
				"fob_type": null,
				"ship_from": null,
				"attention": null,
				"location_type": null,
				"location_name": null,
				"instructions": null
			},
			"job_cost_defaults": {
				"cinx_phase_guid": null,
				"phase_name": null,
				"cinx_material_cost_code_guid": null,
				"material_cost_code_name": null,
				"cinx_category_guid": null,
				"category_name": null
			},
			"taxes": {
				"taxable": true,
				"cinx_guid": null,
				"tax_group_name": null
			},
			"charges": [{
				"type": null,
				"description": null,
				"unit_price": null,
				"job_cost": {
					"cinx_phase_guid": null,
					"phase_name": null,
					"cinx_material_cost_code_guid": null,
					"material_cost_code_name": null,
					"cinx_category_guid": null,
					"category_name": null,
					"gl_account": null
				},
				"taxes": {
					"taxable": true,
					"cinx_guid": null,
					"tax_group_name": null,
					"tax_type": null,
					"tax_rate": null,
					"tax_amount": null
				},
				"project": {
					"cinx_guid": null,
					"number": null
				}
			}],
			"credits": [{
				"type": null,
				"description": null,
				"unit_price": null,
				"job_cost": {
					"cinx_phase_guid": null,
					"phase_name": null,
					"cinx_material_cost_code_guid": null,
					"material_cost_code_name": null,
					"cinx_category_guid": null,
					"category_name": null,
					"gl_account": null
				},
				"taxes": {
					"taxable": true,
					"cinx_guid": null,
					"tax_group_name": null,
					"tax_type": null,
					"tax_rate": null,
					"tax_amount": null
				},
				"project": {
					"cinx_guid": null,
					"number": null
				}
			}],
			"external_references": [{
				"type": null,
				"description": null,
				"value": null
			}],
			"items": [{
				"cinx_guid": null,
				"quantity": null,
				"price_uom": null,
				"unit_price": null,
				"currency": null,
				"price_source_type": null,
				"date_need_by": null,
				"allow_substitutes": true,
				"hph_code": null,
				"org_item_id": null,
				"org_system_id": null,
				"mfr_part_number": null,
				"upc": null,
				"size": null,
				"description": null,
				"mfr_name": null,
				"item_type": null,
				"procurement_status": null,
				"vendor": {
					"cinx_commerce_guid": null,
					"number": null
				},
				"project": {
					"cinx_guid": null,
					"number": null
				},
				"delivery": {
					"ship_via": null,
					"deliver_to": null,
					"location_type": null,
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
					"material_cost_code_name": null,
					"cinx_category_guid": null,
					"category_name": null
				},
				"taxes": {
					"taxable": true,
					"cinx_guid": null,
					"tax_group_name": null,
					"tax_type": null,
					"tax_rate": null,
					"tax_amount": null
				},
				"design": {
					"model_item_guid": null,
					"model_name": null,
					"model_file": null,
					"drawing_number": null,
					"drawing_name": null
				}
			}]
		},
		"field_options": {},
		"api_calls": []
	}]
}
```
`GET`

This endpoint will be used to get a CINX Template for a purchase order.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/po**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/po`


The table below defines the input fields within the template.

## Get PO Number
### API Endpoint - Get a New Purchase Order Number

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"po": "PO-000001"
		}
    ]
}
```
`GET`

This endpoint will be used to get a value to be used in the number field of a new purchase order.

**Notes** 

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/po**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/po`

## Create PO
### API Endpoint - Create a New Purchase Order

`POST`

This endpoint will be used to create a new purchase order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-po-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-po-import?body=json`

<aside class="notice">
The POST payload will be processed asynchronously.
</aside>

## Modify PO
### API Endpoint - Modify a Purchase Order

`PUT`

This API endpoint will be used to modify an existing CINX purchase order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-po-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-po-import?body=json`

<aside class="notice">
The PUT payload will be processed asynchronously.
</aside>

## Get PO Change Orders
### API Endpoint - Get a List of PO Change Orders for a Purchase Order

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
			"status": "SUBMITTED",
			"procurement_status": "ORDERED",
			"tx_type": "CHANGE ORDER",
			"po_number": "PO-123",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_submitted": "2019-06-06",
			"submitted_by": "Will Stone",
			"date_deliver_by": "2019-06-14",
			"phase": "First Floor",
			"cost_code": "101-1025",
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

This endpoint will be used to get a list of PO Change Orders for a specified purchase order. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid}/pocos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/pocos`

## Get PO Deliveries
### API Endpoint - Get a List of Deliveries for a Purchase Order

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "f116ad07-ab08-5b87-ad42-18cab454e086",
			"number": "D000012",
			"name": "D000012",
			"description": null,
			"status": "INCOMPLETE",
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_received": "2019-06-07",
			"received_by": "Will Stone",
			"total_weight": "456",
			"packing_slip": "54654645",
			"links": [],
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"po_number": "PO-123",
			"po_name": "PO123",
			"date_deliver_by": "2019-06-11",
			"item_count": 15
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of Deliveries for a vendor. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid}/deliveries**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/deliveries`

## Get PO Invoices
### API Endpoint - Get a List of Invoices for a Purchase Order

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "8ead0386-496b-571c-b14f-09eafeeb6758",
			"number": "I456123",
			"name": "I456123",
			"status": "PENDING E-INVOICE",
			"erp_status": "NOT SUBMITTED",
			"current_owner_name": "Will Stone",
			"entry_method": "MANUAL",
			"entered_by": null,
			"date_entered": "",
			"accept_method": "MANUAL",
			"accepted_by": null,
			"date_issued": "2019-06-08",
			"payment_due": "2019-06-21 00:00:00Z",
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"po_number": "",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"links": [],
			"item_count": 15
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of Invoices for a purchase order. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid}/invoices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/invoices`

## Get PO Returns
### API Endpoint - Get a List of Returns for a Purchase Order

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "03dfb081-fc43-5196-8b58-d8277278bc59",
			"number": "R000001",
			"name": "R000001",
			"status": "RMA REQUESTED",
			"rma": null,
			"rma_expires": null,
			"reason": null,
			"action": "Replace Item",
			"current_owner_name": "Will Stone",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"po_number": "PO-123",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"links": [],
			"item_count": 1
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of Returns for a purchase order. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid/returns**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/returns`

## Get PO Back-Orders
### API Endpoint - Get a List of Back-Orders for a Purchase Order

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "076bd4bb-d6d9-5096-96f2-ec105d0562b1",
			"date_expected_delivery": null,
			"date_po_deliver_by": null,
			"date_informed": null,
			"date_last_updated": null,
			"reason": null,
			"quantity_backordered": 1,
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

This endpoint will be used to get a list of Back-Orders for a purchase order. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid/back-orders**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/back-orders`

HTTP Method: 

## ERP Status Update
### API Endpoint - Update a Purchase Order's ERP Status

`PUT`

This API call will be used to modify the erp status for a purchase order in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid/erp/applied**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/erp/applied`