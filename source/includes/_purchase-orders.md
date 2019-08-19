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
			"vendor_name": "Hilti",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_order_by": "2019-06-07",
			"date_submitted": "2019-06-06",
			"submitter": "Will Stone",
			"date_need_by": "2019-06-11",
			"date_received": "",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
			"phase": "First Floor",
			"material_cost_code": "101-1025",
			"category": null,
			"tax_group": "TAX-03",
			"terms": "0/0",
			"quote_number": null,
			"quote_name": null,
			"erp_status": "NOT SUBMITTED",
			"external_references": [],
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

## Get PO
### API Endpoint - Get a Purchase Order

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "8185cbd2-18c6-5cdc-b3ed-25795aabbfcc",
			"locked": "1",
			"number": "PO-111111",
			"name": "PO-111111",
			"description": "Sample PO description text",
			"terms": "1.5/10",
			"user_comment": "Sample PO user Comment",
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
				"submitted": "2019-07-29",
				"received": ""
			},
			"customer": {
				"cinx_commerce_guid": "de0cf849-6f7b-5df6-9ae9-f924659f2d25",
				"number": "CX101",
				"name": "WTS Mechanical"
			},
			"vendor": {
				"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
				"number": "V101",
				"name": "Hilti"
			},
			"project": {
				"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
				"number": "WTS-2017-03",
				"name": "WTS-Building 3"
			},
			"delivery": {
				"address1": "377 Route 117",
				"address2": null,
				"address3": null,
				"city": "Sugar Hill",
				"state": "NH",
				"postal_code": "03586",
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
				"credits": 0,
				"charges": 0,
				"items": 1
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
					"name": "Hilti",
					"item_id": null,
					"system_id": null,
					"cinx_quote_guid": null,
					"quote_number": null
				},
				"requisition": {
					"cinx_guid": "2e5763f6-f7be-5179-9109-5e81014fb5b5",
					"number": "REQ-19-001",
					"name": "REQ-19-001"
				},
				"project": {
					"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
					"number": "WTS-2017-03",
					"name": "WTS-Building 3"
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
				"unit_price": null,
				"price_uom": null,
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

**TEMPLATE FIELDS**

Name | Data Type | Required | Default | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; Put = Yes |  | CINX System Id.
number | String | Yes |  | Public number for the object.
name | String | Yes |  | Public name for the object.
description | String | No |  | Public description for the object.
terms | String | No |  | Transaction terms.
user_comment | String | No |  | General comment defined by a CINX user.
procurement_status | String | Yes | NOT ORDERED | Status used to track the procurement activities of the purchase order. Template has a list of optional values.
workflow_status | String | Yes | IN-PROCESS | Status used to track the workflow of the purchase order. Template has a list of optional values.
erp_status | String | Yes | NOT SUBMITTED | Status used to track the purchase order's integration with an ERP system. Template has a list of optional values.
allow_substitutes | Boolean | Yes | TRUE | Transaction level default used to indicate if the items on the purchase order can be sourced from an alternate manufacturer.
dates.order_by | Date (YYYY-MM-DD) | No |  | Date the purchase order should be submitted to the vendor.
dates.need_by | Date (YYYY-MM-DD) | No |  | Date the products on the purchase order need to be delivered to the specified delivery location.
vendor.cinx_commerce_guid | String (GUID Format) | No |  | CINX Commerce Id for the vendor that will receive the purchase order.
vendor.number | String | No |  | The public number of the vendor that will receive the purchase order.
project.cinx_guid | String (GUID Format) | No |  | CINX Project Id.
project.number | String | No |  | The public number of the project for which the items are being purchased.
delivery.address1 | String | No |  | Address 1 value for the location to which the products on the purchase order are to be delivered.
delivery.address2 | String | No |  | Address 2 value for the location to which the products on the purchase order are to be delivered.
delivery.address3 | String | No |  | Address 3 value for the location to which the products on the purchase order are to be delivered.
delivery.city | String | No |  | City to which the products on the purchase order are to be delivered.
delivery.state | String | No |  | State to which the products on the purchase order are to be delivered. Two-character alpha abbreviation.
delivery.postal_code | String | No |  | Postal/Zip Code to which the products on the purchase order are to be delivered.
delivery.country | String | No |  | Country to which the products on the purchase order are to be delivered. Three-character alpha abbreviation.
delivery.ship_via | String | No |  | How the products are to be delivered or otherwise acquired. Template has a list of optional values.
delivery.fob_type | String | No |  | F.O.B. Type. Template has a list of optional values.
delivery.ship_from | String | No |  | Location from which the requester would like the materials on the purchase order to be shipped.
delivery.attention | String | No |  | User-defined delivery attention.
delivery.location_type | String | No | JOB SITE | Type of location where the requester would like the materials delivered. Template has a list of optional values.
delivery.location_name | String | No |  | Name of the location where the requester would like the materials delivered.
delivery.Instructions | String | No |  | General delivery instructions for the order.
job_cost_defaults.cinx_phase_guid | String (GUID Format) | No |  | Transaction level default. CINX Id for the Phase/Sub-Job assigned to the items on the purchase order.
job_cost_defaults.phase_name | String | No |  | Transaction level default. Name for the Phase/Sub-Job assigned to the items on the purchase order.
job_cost_defaults.cinx_material_cost_code_guid | String (GUID Format) | No |  | Transaction level default. CINX Id for the Material Cost Code assigned to the items on the purchase order.
job_cost_defaults.material_cost_code_name | String | No |  | Transaction level default. Name for the Material Cost Code assigned to the items on the purchase order.
job_cost_defaults.cinx_category_guid | String (GUID Format) | No |  | Transaction level default. CINX Id for the Category assigned to the items on the purchase order.
job_cost_defaults.category_name | String | No |  | Transaction level default. Name for the Category assigned to the items on the purchase order.
taxes.taxable | Boolean | Yes | TRUE | Transaction level default. Indicator defining if the products on the purchase order are taxable.
taxes.cinx_guid | String (GUID Format) | No |  | Transaction level default. CINX Id for the Tax Group assigned to the items on the purchase order.
taxes.tax_group_name | String | No |  | Transaction level default. Name for the Tax Group assigned to the items on the purchase order.
external_references.type | String | No |  | Non-CINX system reference type.
external_references.description | String | No |  | Non-CINX system reference description.
external_references.value | String | No |  | Non-CINX system reference value.
charges.type | String | No |  | Name of the type of charge. Template has a list of optional values.
charges.description | String | No |  | Description of the charge.
charges.unit_price | Real | No |  | Cost of the charge.
charges.job_cost.cinx_phase_guid | String (GUID Format) | No |  | CINX Id for the Phase/Sub-Job assigned to the charge.
charges.job_cost.phase_name | String | No |  | Name for the Phase/Sub-Job assigned to the charge.
charges.job_cost.cinx_material_cost_code_guid | String (GUID Format) | No |  | CINX Id for the Material Cost Code assigned to the charge.
charges.job_cost.material_cost_code_name | String | No |  | Name for the Material Cost Code assigned to the charge.
charges.job_cost.cinx_category_guid | String (GUID Format) | No |  | CINX Id for the Category assigned to the charge.
charges.job_cost.category_name | String | No |  | Name for the Category assigned to the charge.
charges.job_cost.gl_account | String | No |  | General Ledger account assigned to the charge.
charges.taxes.taxable | Boolean | Yes | TRUE | Indicator defining if the charge is taxable.
charges.taxes.cinx_guid | String (GUID Format) | No |  | CINX Id for the Tax Group assigned to the charge.
charges.taxes.tax_group_name | String | No |  | Name for the Tax Group assigned to the charge.
charges.taxes.tax_type | String | No |  | Name of the type of tax. Template has a list of optional values.
charges.taxes.tax_rate | Real | No |  | The tax rate.
charges.taxes.tax_amount | Real | No |  | The total amount of the tax for the charge.
charges.project.cinx_guid | String (GUID Format) | No |  | CINX Project Id.
charges.project.number | String | No |  | The public number of the project.
credits.type | String | No |  | Name of the type of credit. Template has a list of optional values.
credits.description | String | No |  | Description of the credit.
credits.unit_price | Real | No |  | Amount of the credit.
credits.job_cost.cinx_phase_guid | String (GUID Format) | No |  | CINX Id for the Phase/Sub-Job assigned to the credit.
credits.job_cost.phase_name | String | No |  | Name for the Phase/Sub-Job assigned to the credit.
credits.job_cost.cinx_material_cost_code_guid | String (GUID Format) | No |  | CINX Id for the Material Cost Code assigned to the credit.
credits.job_cost.material_cost_code_name | String | No |  | Name for the Material Cost Code assigned to the credit.
credits.job_cost.cinx_category_guid | String (GUID Format) | No |  | CINX Id for the Category assigned to the credit.
credits.job_cost.category_name | String | No |  | Name for the Category assigned to the credit.
credits.job_cost.gl_account | String | No |  | General Ledger account assigned to the credit.
credits.taxes.taxable | Boolean | Yes | TRUE | Indicator defining if the credit is taxable.
credits.taxes.cinx_guid | String (GUID Format) | No |  | CINX Id for the Tax Group assigned to the credit.
credits.taxes.tax_group_name | String | No |  | Name for the Tax Group assigned to the credit.
credits.taxes.tax_type | String | No |  | Name of the type of tax. Template has a list of optional values.
credits.taxes.tax_rate | Real | No |  | The tax rate.
credits.taxes.tax_amount | Real | No |  | The total amount of the tax for the credit.
credits.project.cinx_guid | String (GUID Format) | No |  | CINX Project Id.
credits.project.number | String | No |  | The public number of the project.
items.cinx_guid | String (GUID Format) | POST = No; Put = Yes |  | CINX System Id.
items.quantity | Real | No | 1 | Quantity of the item that is being ordered.
items.unit_price | Real | No |  | Unit price of the item on the purchase order.
items.price_uom | String | No | E | Price unit-of-measure. Template has a list of optional values.
items.currency | String | No | USD | Currency in which the price is being defined.  Three-character alpha abbreviation.
items.price_source_type | String | No |  | Source from which the price was obtained. Template has a list of optional values.
items.date_need_by | Date (YYYY-MM-DD) | No |  | Date the product needs to be delivered to the specified delivery location.
items.allow_substitutes | Boolean | Yes | TRUE | Indicator if the product can be sourced from an alternate manufacturer.
items.hph_code | String | No |  | HPH Item Code for the item that is being ordered.
items.org_item_id | String | No |  | The requesting company's Org Item Id for the product that is being ordered. User-friendly code.
items.org_system_id | String | No |  | The requesting company's Org System Item Id for the product that is being ordered. Unique Id code.
items.mfr_part_number | String | No |  | Manufacturer-defined Part/Catalog Number for the product that is being ordered.
items.upc | String | No |  | Manufacturer-defined UPC Number for the product that is being ordered.
items.size | String | No |  | Size of the item that is being ordered.
items.description | String | No |  | Description of the item that is being ordered.
items.mfr_name | String | No |  | Name of the manufacturer or fabricator that produces the item that is being ordered.
items.item_type | String | No |  | Classification name of the item that is being ordered.
items.procurement_status | String | Yes | NOT-ORDERED | Status used to track the procurement activities of the item. Template has a list of optional values.
items.vendor.cinx_commerce_guid | String (GUID Format) | No |  | CINX Commerce Id for the vendor.
items.vendor.number | String | No |  | The public number of the vendor from whom the product is being sourced.
items.project.cinx_guid | String | No |  | CINX Project Id.
items.project.number | String | No |  | The public number of the project from which the item are being ordered.
items.delivery.ship_via | String | No |  | How the product is to be delivered or otherwise acquired. Template has a list of optional values.
items.delivery.deliver_to | String | No |  | Deliver To text.
items.delivery.location_type | String | No |  | Where the requester would like the product to be delivered. Template has a list of optional values.
items.delivery_location_name | String | No |  | Name of the location where the item is to be delivered.
items.delivery.instructions | String | No |  | Delivery instructions to be submitted to the vendor responsible for delivering the item.
items.delivery.labeling_instructions | String | No |  | Labeling instructions to be submitted to the vendor responsible for delivering the item.
items.delivery.packaging_instructions | String | No |  | Packaging instructions to be submitted to the vendor responsible for delivering the item.
items.work_breakdown.work_order_id | String | No |  | Contractor defined Work Order Id that was assigned to the product.
items.work_breakdown.work_order_name | String | No |  | Contractor defined Work Order Name that was assigned to the product.
items.work_breakdown.spool_id | String | No |  | Contractor defined Spool Id that was assigned to the product.
items.work_breakdown.spool_name | String | No |  | Contractor defined Spool Name that was assigned to the product.
items.work_breakdown.building_name | String | No |  | Name of the building in which the product will be installed.
items.work_breakdown.level | String | No |  | Level of the building in which the product will be installed.
items.work_breakdown.space | String | No |  | Space of the building in which the product will be installed.
items.work_breakdown.sub_space | String | No |  | Sub-space of the building in which the product will be installed.
items.work_breakdown.system | String | No |  | Name of the system in which the product will be installed.
items.work_breakdown.arch_symbol | String | No |  | Architectural symbol of the product.
items.work_breakdown.tag | String | No |  | Text of what should appear on a tag for the item.
items.job_cost.cinx_phase_guid | String (GUID Format) | No |  | CINX Id for the Phase/Sub-Job assigned to the item.
items.job_cost.phase_name | String | No |  | Name for the Phase/Sub-Job assigned to the item.
items.job_cost.cinx_material_cost_code_guid | String (GUID Format) | No |  | CINX Id for the Material Cost Code assigned to the item.
items.job_cost.material_cost_code_name | String | No |  | Name for the Material Cost Code assigned to the item.
items.job_cost.cinx_category_guid | String (GUID Format) | No |  | CINX Id for the Category assigned to the item.
items.job_cost.category_name | String | No |  | Name for the Category assigned to the item.
items.taxes.taxable | Boolean | Yes | TRUE | Indicator defining if the product is taxable.
items.taxes.cinx_guid | String (GUID Format) | No |  | CINX Id for the Tax Group assigned to the item.
items.taxes.tax_group_name | String | No |  | Name of the Tax Group assigned to the item.
items.taxes.tax_type | String | No |  | Name of the type of tax. Template has a list of optional values.
items.taxes.rate | Real | No |  | The tax rate.
items.taxes.amount | Real | No |  | The total amount of the tax for the item.
items.design.model_item_guid | String (GUID Format) | No |  | Id assigned by the authoring system that placed the item in the model.
items.design.model_name | String | No |  | Name of the model in which the item is located.
items.design.model_file | String | No |  | File name of the model in which the item is located.
items.design.drawing_number | String | No |  | Number of the drawing on which the item is located.
items.design.drawing_name | String | No |  | Name of the drawing on which the item is located.

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
			"project_name": "HPH HQ Renovation",
			"vendor_number": "H125",
			"vendor_name": "Hilti",
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
			"vendor_name": "Hilti",
			"ship_via": "SUPPLIER TRUCK",
			"location_type": "FABRICATION SHOP",
			"location_name": null,
			"date_received": "2019-06-07",
			"received_by": "Will Stone",
			"total_weight": "456",
			"packing_slip": "54654645",
			"links": [],
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
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

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}


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
			"vendor_name": "Hilti",
			"po_number": "",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
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

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
status | Limits results to a specific status. | PENDING E-INVOICE, ENTERED, REVIEWED, ACCEPTED, IN-DISPUTE, ON-HOLD, REJECTED, SUBMITTED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}


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
			"vendor_name": "Hilti",
			"po_number": "PO-123",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
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

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}


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
			"vendor_name": "Hilti",
			"work_order_id": null,
			"work_order_name": null,
			"spool_id": null,
			"spool_name": null,
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
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

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}

## ERP Status Update
### API Endpoint - Update a Purchase Order's ERP Status

`PUT`

This API call will be used to modify the erp status for a purchase order in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid/erp/applied**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/erp/applied`
