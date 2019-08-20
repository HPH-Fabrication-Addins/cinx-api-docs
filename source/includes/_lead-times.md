# Lead-Times

## Lead-Time Definition
### CINX Object Defintion - Lead-Time

CINX supports the definition of a lead-time for an item that has been added to a project or purchasing transaction.  A lead time defines the amount of time, expressed in days, that it will take for the vendor to deliver the finished product after it is ordered. CINX also supports the definition of two date fields (need by and order by) that will help manage the timely ordering of materials.  

**Dependencies and Business Rules**

  - The item must be linked to a CINX project or purchasing transaction
  - CINX Lead-Times are expressed in days

**Supported API Services**

  - [Get a List of Lead-Times](#get-lead-times-list)
  - [Get a Lead Time](#get-lead-time)


## Get Lead-Times List
### API Endpoint - Get a List of Lead-Times

> The above code returns JSON structured like this:

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "fe30ea8b-78bf-5dc4-962b-1fb034061b08",
		"lead_time": 5,
		"date_need_by": "2019-09-27",
		"date_order_by": "2019-09-22",
		"quantity": 1,
		"org_item_id": null,
		"vendor_item_id": null,
		"mfr_part_number": null,
		"hph_code": "505VC2080",
		"upc": null,
		"description": "10\" EPDM GASKET",
		"mfr_name": "Victaulic Company",
		"delivery_location_type": "JOB SITE",
		"delivery_location_name": null,
		"vendor_number": null,
		"vendor_name": null,
		"work_order_id": null,
		"work_order_name": null,
		"spool_id": null,
		"spool_name": null,
		"project_number": "PRJ-2019-04",
		"project_name": "Snow-making Pump House",
		"requisition_number": null,
		"requisition_name": null,
		"po_number": null,
		"po_name": null
	}]
}
```
`GET`

This endpoint will be used to get a list of items with a lead-time. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/lead-times**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/lead-times`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}

## Get Lead-Time
### API Endpoint - Get a Lead-Time

`GET`

This endpoint will be used to get the details of an item with a lead-time.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/lead-time/{cinx_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/lead_time/84cd7385-4639-5339-a956-0cad247687f9`

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "84cd7385-4639-5339-a956-0cad247687f9",
		"lead_time": 20,
		"quantity": 1,
		"unit_price": null,
		"price_uom": null,
		"currency": "USD",
		"allow_substitutes": true,
		"hph_code": "505VC2994I",
		"org_item_id": null,
		"org_system_item_id": null,
		"mfr_part_number": null,
		"upc": null,
		"size": "18X14\"",
		"description": "18X14\" GRVXFLG AGS SUCTION DIFFUSER",
		"mfr_name": "Victaulic Company",
		"item_type": "MATERIAL",
		"procurement_status": "NOT ORDERED",
		"dates": {
			"need_by": "2019-09-26",
			"order_by": "2019-09-06"
		},
		"customer": {
			"cinx_commerce_guid": null,
			"number": null,
			"name": null
		},
		"vendor": {
			"cinx_commerce_guid": null,
			"number": null,
			"name": null,
			"item_id": null,
			"system_id": null
		},
		"project": {
			"cinx_guid": "57e7399d-d3d8-58f4-bddf-be20006e9178",
			"number": "PRJ-2019-04",
			"name": "PRJ-2019-04"
		},
		"requisition": {
			"cinx_guid": "2ca4a844-e2ea-5593-b002-0bf321e4dcf9",
			"number": "REQ-0007",
			"name": "REQ-0007"
		},
		"purchase_order": {
			"cinx_guid": null,
			"number": null,
			"name": null
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
			"cinx_phase_guid": "ea6fba0f-0b8e-5e49-a110-6bcb36182146",
			"phase_name": "Phase2",
			"cinx_material_cost_code_guid": "5d9b83d0-a3de-5475-959d-04b92fd4de75",
			"material_cost_code_name": "UG-123",
			"cinx_category_guid": "a5f91c07-7c5b-5b0c-863b-16b2f6d960c6",
			"category_guid": "Expense 12"
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
			"drawing_number": null,
			"drawing_name": null
		}
	}]
}
```
