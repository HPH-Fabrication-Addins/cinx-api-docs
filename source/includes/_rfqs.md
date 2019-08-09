# RFQs

## RFQ Definition
### CINX Object Defintion - Request for Quotation

A CINX Request for Quotation is a compilation of  that a customer wants a vendor(s) to provide pricing on before making ordering/sourcing decisions. The list might be for a whole project, phase, system, pre-fab work-order, spool, or a general list created by a project foreman in the field. 

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Can be submitted to multiple vendors
  - Will be locked after it is submitted

**Supported API Services**

  - [Get a List of RFQs](#get-rfq-list)
  - [Get an RFQ](#get-rfq)
  - [Get an RFQ Template](#get-rfq-template)
  - [Get an RFQ Number](#get-rfq-number)
  - [Create an RFQ](#create-rfq)
  - [Modify an RFQ](#modify-rfq)

## Get RFQ List
### API Endpoint - Get a List of RFQs

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "f823d544-15dc-551f-94f9-f04283bfddb0",
			"number": "",
			"name": "RFQ-1254",
			"description": "",
			"workflow_status": "SUBMITTED",
			"submitted_by": "Will Stone",
			"date_submitted": "",
			"date_respond_by": "",
			"vendors": [
				{
					"number": "H125",
					"name": "Hilti-6"
				}
			],
			"links": [],
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "OFFICE",
			"delivery_location_name": null,
			"date_need_by": "2019-06-08",
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"req_number": null,
			"req_name": null,
			"phase": null,
			"material_cost_code": null,
			"category": null,
			"item_count": 113
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of RFQs. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/rfqs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/rfqs`


**OPTIONAL URL PARAMETERS**

**delivery**: will limit results to a specific delivery type location

  - Available options are: JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR

**workflow**: will limit results to a specific workflow status

  - Available options are: IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, QUOTED

**project**: will limit results to a single project

  - {cinx_project_guid}

**vendor**: will limit results to a single vendor

  - {organization's vendor number}

**ship-via**: will limit results to a specific ship via value

  - Available options are: SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE

**need-by**: will limit results to a specific need-by or delivery-by date

  - Date Format: YYYY-MM-DD

**submitter**: will limit results to a specified CINX user

  - {CINX_User_Id}

**number**: will limit results to a specified transaction number

  - {transaction_number}

## Get RFQ
### API Endpoint - Get an RFQ

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "a71e023c-f809-5a51-a51f-d4546ed0c9fd",
		"locked": "1",
		"number": "",
		"name": "TestNSCXRef",
		"description": "",
		"terms": null,
		"user_comment": "",
		"workflow_status": "SUBMITTED",
		"submitter": {
			"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
			"name": "Will Stone",
			"email": "willstone@cinx.com"
		},
		"dates": {
			"created": "2019-03-29",
			"last_modified": "2019-03-29",
			"respond_by": "2019-03-30",
			"need_by": null,
			"submitted": "2019-03-29",
			"quoted": null
		},
		"customer": {
			"cinx_commerce_guid": null,
			"number": null,
			"name": "WTS Mechanical -DEV"
		},
		"vendors": [{
			"cinx_commerce_guid": "de0cf849-6f7b-5df6-9ae9-f924659f2d25",
			"number": "CXV101",
			"name": "National Sales Company"
		}],
		"project": {
			"cinx_id": null,
			"number": null,
			"name": null
		},
		"delivery": {
			"address1": "995 Industrial Park Rd",
			"address2": "",
			"address3": "",
			"city": "Littleton",
			"state": "NH",
			"postal_code": "03561",
			"country": "USA",
			"ship_via": null,
			"fob_type": null,
			"ship_from": null,
			"attention": null,
			"location_type": "JOB SITE",
			"location_name": null,
			"instructions": null
		},
		"job_cost_defaults": {
			"cinx_phase_guid": null,
			"phase_name": null,
			"cinx_material_cost_code_guid": null,
			"material_cost_code": null,
			"cinx_category_guid": null,
			"category_name": null
		},
		"taxes": {
			"taxable": true,
			"cinx_id": null,
			"tax_group_name": null
		},
		"external_references": [],
		"items": [{
				"cinx_guid": "ca43c356-f686-5211-92ca-484d4ad4ef08",
				"sequence": 1,
				"quantity": 1,
				"date_need_by": null,
				"allow_substitutes": true,
				"hph_code": "012NI0010",
				"org_item_id": null,
				"org_system_id": null,
				"mfr_part_number": "9055450",
				"upc": "039923312723",
				"size": "1/2\"",
				"description": "1/2\" WROT CXC 90 ELBOW",
				"mfr_name": "NIBCO, Inc.",
				"item_type": "MATERIAL",
				"project": {
					"cinx_guid": null,
					"number": null,
					"name": null
				},
				"delivery": {
					"deliver_to": null,
					"location_type": "JOBSITE",
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
					"drawing_number": null,
					"drawing_name": null
				}
			}
		]
	}]
}
```

`GET`

This endpoint will be used to get the details of a specific RFQ.  Note: This response will include the RFQ’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/rfq/{cinx_guid}**

The cinx_guid will be the RFQ’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/rfq/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

## Get RFQ Template
### API Endpoint - Get an RFQ Template

```json
{
	"response": {},
	"rows": [{
		"doc_info": {},
		"template": {
			"cinx_id": null,
			"number": null,
			"name": null,
			"description": null,
			"terms": null,
			"user_comment": null,
			"workflow_status": "IN-PROCESS",
			"dates": {
				"respond_by": null,
				"need_by": null,
				"submitted": null
			},
			"vendors": [{
				"cinx_commerce_guid": null,
				"number": null
			}],
			"project": {
				"cinx_id": null,
				"number": null
			},
			"delivery": {
				"address1": null,
				"address2": null,
				"address3": null,
				"city": null,
				"state": null,
				"postal_code": null,
				"country": "USA",
				"ship_via": null,
				"fob_type": null,
				"ship_from": null,
				"attention": null,
				"location_type": "JOB SITE",
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
				"taxable": false,
				"cinx_id": null,
				"tax_group_name": null
			},
			"external_references": [{
				"type": null,
				"description": null,
				"value": null
			}],
			"items": [{
				"cinx_guid": null,
				"quantity": null,
				"date_need_by": null,
				"allow_substitutes": "true",
				"hph_code": null,
				"org_item_id": null,
				"org_system_id": null,
				"mfr_part_number": null,
				"upc": null,
				"size": null,
				"description": null,
				"mfr_name": null,
				"item_type": null,
				"vendor": {
					"cinx_commerce_guid": null,
					"number": null
				},
				"project": {
					"cinx_guid": null,
					"number": null
				},
				"delivery": {
					"deliver_to": null,
					"location_type": "JOB SITE",
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
					"taxable": false,
					"cinx_guid": null,
					"tax_group_name": null
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

This endpoint will be used to get a CINX Template for an RFQ.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/rfq**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/rfq`


The table below defines the input fields within the template.

## Get RFQ Number
### API Endpoint - Get a New RFQ Number

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"rfq": "RFQ-0001"
		}
    ]
}
```
`GET`

This endpoint will be used to get a value to be used in the number field of a new RFQ.

**Notes** 

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/rfq**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/rfq`

HTTP Method: 

## Create RFQ
### API Endpoint - Create a New RFQ

`POST`

This endpoint will be used to create a new RFQ.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-rfq-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-rfq-import?body=json`

<aside class="notice">
The POST payload will be processed asynchronously.
</aside>

## Modify RFQ
### API Endpoint - Modify an RFQ

`PUT`

This API endpoint will be used to modify an existing CINX RFQ.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-rfq-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-rfq-import?body=json`

<aside class="notice">
The PUT payload will be processed asynchronously.
</aside>

## Get RFQ Quotes
### API Endpoint - Get a List of Quotes for an RFQ

> The above code returns JSON structured like this:

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "1eb08930-8744-5213-90f0-3ad63a216b20",
		"number": "",
		"name": "WTS Mechanical -DEV[ 2019 07 25 a ]",
		"description": "",
		"workflow_status": "RECEIVED",
		"vendor_number": "99999",
		"vendor_name": "Keegan Supply",
		"submitted_by": "eb stone",
		"date_received": "2019-07-25",
		"date_expires": "2019-07-26",
		"date_requested": "",
		"links": [],
		"project_number": "WTS-2019-06",
		"project_name": "2019 01 30",
		"rfq_number": "2019 07 25 a",
		"rfq_name": "2019 07 25 a",
		"item_count": 11
	}]
}
```
`GET`

This endpoint will be used to get a list of Quotes for a specified RFQ. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/rfq/{rfq_guid}/quotes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/rfq/8902980f-4a4f-504c-8fc3-2e71067ab59b/quotes`
