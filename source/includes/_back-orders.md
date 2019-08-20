# Back-Orders

## Back-Order Definition
### CINX Object Defintion - Back-Order

A back-order is an item from a submitted PO that cannot be delivered by the requested delivery date, and for which the customer is prepared to wait for the vendor to replenish its inventory.

**Dependencies and Business Rules**

  - The item must be on a CINX PO

**Supported API Services**

  - [Get a List of Back-Orders](#get-back-order-list)
  - [Get a Back-Order](#get-back-order)
  - [Get a Back-Order Update Template](#get-back-order-upd-template)


## Get Back-Order List
### API Endpoint - Get a List of Back-Orders

> The above code returns JSON structured like this:

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "076bd4bb-d6d9-5096-96f2-ec105d0562b1",
		"date_expected_delivery": "2019-06-11",
		"date_need_by": "2019-06-08",
		"date_informed": "2019-06-08",
		"date_last_updated": "2019-06-11",
		"back_order_reason": null,
		"quantity_back_ordered": 1,
		"quantity_shipped": 0,
		"quantity_ordered": 1,
		"org_item_id": null,
		"vendor_item_id": null,
		"mfr_part_number": null,
		"hph_code": "326ZU6542",
		"upc": "67024006745",
		"description": null,
		"mfr_name": "ZURN",
		"delivery_location_type": null,
		"delivery_location_name": "",
		"vendor_number": "V101",
		"vendor_name": "Hilti",
		"work_order_id": null,
		"work_order_name": null,
		"spool_id": null,
		"spool_name": null,
		"project_number": "WTS-2017-03",
		"project_name": "HPH HQ Renovation",
		"po_number": "P19-062819",
		"po_name": "P19-062819",
		"po_submitter": "Will Stone",
		"update_count": ""
	}]
}
```
`GET`

This endpoint will be used to get a list of back-orders. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/back-orders**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/back-orders`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
po-guid | Limits results to a specific purchase order. | {cinx_po_id}

## Get Back-Order
### API Endpoint - Get a Back-Order

`GET`

This endpoint will be used to get the details of a specific back-order.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/back-order/{cinx_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/back-order/076bd4bb-d6d9-5096-96f2-ec105d0562b1`

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "076bd4bb-d6d9-5096-96f2-ec105d0562b1",
		"unit_price": 270.05,
		"price_uom": "E",
		"currency": "USD",
		"allow_substitutes": true,
		"hph_code": "326ZU6542",
		"org_item_id": null,
		"org_system_id": null,
		"mfr_part_number": null,
		"upc": "67024006745",
		"size": "4",
		"description": "Floor, Z1400 Adjustable, 4",
		"mfr_name": "ZURN",
		"item_type": "MATERIAL",
		"procurement_status": "BACKORDERED",
		"update_count": 0,
		"quantities": {
			"ordered": 1,
			"received": 0,
			"back_ordered": 1,
			"shipped": 0
		},
		"dates": {
			"need_by": "2019-06-08",
			"po_submitted": "2019-06-28",
			"informed": "2019-06-08",
			"expected_delivery": "2019-06-11",
			"last_updated": "2019-06-11",
			"cleared": ""
		},
		"customer": {
			"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
			"numer": "C101",
			"name": "WTS Mechanical -DEV"
		},
		"vendor": {
			"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
			"number": "V101",
			"name": "Hilti",
			"item_id": null,
			"system_id": null,
			"back_order_reason": null
		},
		"project": {
			"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
			"number": "WTS-2017-03",
			"name": "WHPH HQ Renovation"
		},
		"requisition": {
			"cinx_guid": null,
			"number": null,
			"name": null
		},
		"purchase_order": {
			"cinx_guid": "0435078e-fc66-53a8-b69e-7641e2247437",
			"number": "P19-062819",
			"name": "P19-062819",
			"submitter": {
				"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
				"name": "Will Stone",
				"email": "willstone@cinx.com"
			}
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
		"design": {
			"model_item_guid": null,
			"model_name": null,
			"model_file": null,
			"drawing_number": "P1.0",
			"drawing_name": null
		},
		"updates": []
	}]
}
```

## Get Back-Order Upd Template
### API Endpoint - Get a Back-Order Update Template

`GET`

This endpoint will be used to get a CINX Template for a updating a back-ordered item.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/back-order**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/back-order`


The table below defines the input fields within the template.