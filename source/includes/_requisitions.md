# Requisitions

## Req Definition
### CINX Object Defintion - Requisition

A CINX Material Requisition is a compilation of parts that need to be purchased.  The list might be for a whole project, phase, system, pre-fab work-order, spool, or a general list created by a project foreman in the field. The parts on a requisition might also contain items from multiple projects that are combined into one purchase to achieve volume pricing.

It is important to understand that the parts on a requisition may be divided onto different purchase orders which might be sent to different vendors.

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must have a unique number
  - Must have a procurement status
  - Must be assigned to a valid CINX user
  - Must have at least one item before it can be submitted

**Supported API Services**

  - [Get a List of Requisitions](#get-req-list)
  - [Get a Requisition](#get-req)
  - [Get a Requisition Template](#get-req-template)
  - [Get a Requisition Number](#get-req-number)
  - [Create a Requisition](#create-req)
  - [Modify a Requisition](#modify-req)

## Get Req List
### API Endpoint - Get a List of Requisitions

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "e98e2fc5-f59b-5091-8b05-54edaa9284cc",
			"number": "requistion 101",
			"name": "req101",
			"description": "req description",
			"tx_sub_type": "FIELD",
			"current_owner_name": "Karl Stone",
			"procurement_status": "SUBMITTED",
			"submitted_by": "Will Stone",
			"date_submitted": "2019-06-12",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "JOB SITE",
			"delivery_location_name": null,
			"date_need_by": "2019-06-14",
			"vendor_number": null,
			"vendor_name": "National Sales Company",
			"links": [],
			"project_number": "WTS-2017-04",
			"project_name": "WTS-2017-04 - ATC Denver",
			"phase": "First Floor",
			"material_cost_code": "101-1025",
			"category": "MAT",
			"work_order": null,
			"spool": null,
			"allow_substitutes": true,
			"item_count": 4
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of requisitions. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/reqs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/reqs`


**OPTIONAL URL PARAMETERS**

**delivery**: will limit results to a specific delivery type location

  - Available options are: JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR

**procurement**: will limit results to a specific procurement status

  - Available options are: OPEN, SUBMITTED, IN-REVIEW, APPROVED, APPROVED W/MODS, REJECTED, PENDING ORDER, COMPLETE, CLOSED, CANCELLED, RESUBMITTED

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

**owner**: will limit results to a specified CINX user to whom the transaction is assigned

  - {CINX_User_Id}

**number**: will limit results to a specified transaction number

  - {transaction_number}

## Get Req
### API Endpoint - Get a Requisition

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "40b43924-e7b8-5827-935e-14bd70c1d04e",
		"locked": "0",
		"number": "REQ-0005",
		"name": "REQ-TEST EMS",
		"description": null,
		"tx_sub_type": "SHOP",
		"user_comment": null,
		"procurement_status": "OPEN",
		"allow_substitutes": true,
		"assigned_to": {
			"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
			"name": "Will Stone",
			"email": "willstone@cinx.com"
		},
		"submitter": {
			"cinx_quid": null,
			"name": null,
			"email": null
		},
		"dates": {
			"created": "2019-08-06",
			"last_modified": "2019-08-06",
			"submitted": null,
			"need_by": null,
			"approved": null,
			"closed": null
		},
		"vendor": {
			"cinx_commerce_guid": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f",
			"number": "99999",
			"name": "Keegan Supply"
		},
		"project": {
			"cinx_guid": "e1e3cb54-b00a-55ae-a079-072732542bf4",
			"number": "WTS-2017-04",
			"name": "WTS-2017-04 - ATC Denver"
		},
		"delivery": {
			"address1": "995 Industrial Park Rd",
			"address2": "",
			"address3": "",
			"city": "Littleton",
			"state": "NH",
			"postal_code": "03561",
			"country": "USA",
			"ship_via": "MOTOR COMMON CARRIER",
			"fob_type": null,
			"ship_from": null,
			"attention": null,
			"location_type": "OFFICE",
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
			"cinx_guid": null,
			"tax_group_name": null
		},
		"external_references": [],
		"items": [{
				"cinx_guid": "090e00f4-b942-5234-acc0-4ead0b2e3538",
				"sequence": 1,
				"order_status": "REQUEST PENDING",
				"quantity": 1,
				"date_need_by": "",
				"order_lead_time": null,
				"date_order_by": "",
				"allow_substitutes": true,
				"hph_code": "512EK0232",
				"org_item_id": null,
				"org_system_id": null,
				"mfr_part_number": "10020189",
				"upc": "683264201897",
				"size": "1-3/8\"",
				"description": "1-3/8\" ACR CXC 45 ELBOW",
				"mfr_name": "Elkhart Products Corporation",
				"item_type": "MATERIAL",
				"vendor": {
					"cinx_commerce_guid": null,
					"number": null,
					"name": null,
					"item_id": null,
					"system_id": null
				},
				"project": {
					"cinx_guid": null,
					"number": null,
					"name": null
				},
				"delivery": {
					"deliver_to": null,
					"location_type": "JOBSITE",
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
					"material_cost_code": null,
					"cinx_category_guid": null,
					"category_name": null
				},
				"taxes": {
					"taxable": true,
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
			}
		]
	}]
}
```
`GET`

This endpoint will be used to get the details of a specific requisition.  Note: This response will include the requisition’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/req/{cinx_guid}**

The cinx_guid will be the requisition’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/req/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

## Get Req Template
### API Endpoint - Get a Requisition Template

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
			"tx_sub_type": null,
			"user_comment": null,
			"procurement_status": "OPEN",
			"allow_substitutes": true,
			"cinx_user_guid_assign_to": null,
			"dates": {
				"need_by": null,
				"approved": null,
				"closed": null
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
				"cinx_guid": null,
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

This endpoint will be used to get a CINX Template for a requisition.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/req**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/req`


The table below defines the input fields within the template.

Name | Data Type | Required | Default Value | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID format) | POST = No; PUT = Yes |  | CINX System Id.
number | String | Yes |  | Public number for the object.
name | String | Yes |  | Public name for the object.
description | String | No |  | Public description for the object.
tx_sub_type | String | No |  | Used to define the specific type of requisition. See template for available options.
user_comment | String | No |  | General comment defined by a CINX user.
procurement_status | String | Yes | OPEN | Status used to track the procurement activities of the requisition. Template has a list of optional values.
allow_substitutes | Boolean | Yes | TRUE | Transaction level default used to indicate if the items on the requisition can be sourced from an alternate manufacturer.
cinx_user_guid_assign_to | String (GUID format) | No |  | CINX Id for the user to whom the requisition should be assigned.
dates.need_by | Date (YYYY-MM-DD) | No |  | Date the products on the requisition need to be delivered to the specified delivery location.
dates.approved | Date (YYYY-MM-DD) | No |  | Date the requisition was approved for ordering.
dates.closed | Date (YYYY-MM-DD) | No |  | Date the requisition was closed.
vendor.cinx_commerce_guid | String (GUID format) | No |  | Transaction level default. CINX Commerce Id for the requested vendor.
vendor.number | String | No |  | Transaction level default. The public number of the vendor from whom the requester would like the products to be sourced.
project.cinx_guid | String (GUID format) | No |  | Transaction level default. CINX Project Id.
project.number | String | No |  | Transaction level default. The public number of the project from which the items are being requested.
delivery.address1 | String | No |  | Address 1 value for the location to which the products on the requisition are to be delivered.
delivery.address2 | String | No |  | Address 2 value for the location to which the products on the requisition are to be delivered.
delivery.address3 | String | No |  | Address 3 value for the location to which the products on the requisition are to be delivered.
delivery.city | String | No |  | City to which the products on the requisition are to be delivered.
delivery.state | String (2 character alpha abbreviation) | No |  | State to which the products on the requisition are to be delivered.
delivery.postal_code | String | No |  | Postal/Zip Code to which the products on the requisition are to be delivered.
delivery.country | String (3 character alpha abbreviation) | No | USA | Country to which the products on the requisition are to be delivered.
delivery.ship_via | String | No |  | How the products are to be delivered or otherwise acquired. Template has a list of optional values.
delivery.fob_type | String | No |  | F.O.B. Type. Template has a list of optional values.
delivery.ship_from | String | No |  | Location from which the requester would like the materials on the requisition to be shipped.
delivery.attention | String | No |  | User-defined delivery attention.
delivery.location_type | String | No | JOB SITE | Transaction level default. Type of location where the requester would like the materials delivered. Template has a list of optional values.
delivery.location_name | String | No |  | Name of the location where the requester would like the materials delivered.
job_cost_defaults .cinx_phase_guid | String (GUID format) | No |  | Transaction level default. CINX Id for the Phase/Sub-Job assigned to the items on the requisition.
job_cost_defaults.phase_name | String | No |  | Transaction level default. Name for the Phase/Sub-Job assigned to the items on the requisition.
job_cost_defaults.cinx_material_cost_code_guid | String (GUID format) | No |  | Transaction level default. CINX Id for the Material Cost Code assigned to the items on the requisition.
job_cost_defaults.material_cost_code_name | String | No |  | Transaction level default. Name for the Material Cost Code assigned to the items on the requisition.
job_cost_defaults.cinx_category_guid | String (GUID format) | No |  | Transaction level default. CINX Id for the Category assigned to the items on the requisition.
job_cost_defaults.category_name | String | No |  | Transaction level default. Name for the Category assigned to the items on the requisition.
taxes.taxable | Boolean | Yes | FALSE | Transaction level default. Indicator defining if the products on the requisition are taxable.
taxes.cinx_guid | String (GUID format) | No |  | Transaction level default. CINX Id for the Tax Group assigned to the items on the requisition.
taxes.tax_group_name | String | No |  | Transaction level default. Name for the Tax Group assigned to the items on the requisition.
external_references.type | String | No |  | Non-CINX system reference type name.
external_references.description | String | No |  | Non-CINX system reference description.
external_references.value | String | No |  | Non-CINX system reference value.
items.cinx_guid | String (GUID format) | POST = No; PUT = Yes |  | CINX System Id.
items.quantity | Real | No | 1 | Quantity of the item that needs to be ordered.
items.date_need_by | Date (YYYY-MM-DD) | No |  | Date the product needs to be delivered to the specified delivery location.
items.allow_substitutes | Boolean | Yes | TRUE | Indicator if the product can be sourced from an alternate manufacturer.
items.hph_code | String | No |  | HPH Item Code for the item that needs to be ordered.
items.org_item_id | String | No |  | The requesting company's Org Item Id for the product that needs to be ordered. User-friendly code.
items.org_system_id | String | No |  | The requesting company's Org System Item Id for the product that needs to be ordered. Unique Id code.
items.mfr_part_number | String | No |  | Manufacturer defined Part/Catalog Number for the product that needs to be ordered.
items.upc | String | No |  | Manufacturer defined UPC Number for the product that needs to be ordered.
items.size | String | No |  | Size or rating of the item that needs to be ordered.
items.description | String | No |  | Description of the item that needs to be ordered.
items.mfr_name | String | No |  | Name of the manufacturer or fabricator that produces the item that needs to be ordered.
items.item_type | String | No |  | Classification name of the item that needs to be ordered.
items.vendor.cinx_commerce_guid | String (GUID format) | No |  | CINX Commerce Id for the requested vendor.
items.vendor.number | String | No |  | The public number of the vendor from whom the requester would like the product to be sourced.
items.project.cinx_guid | String (GUID format) | No |  | CINX Project Id.
items.project.number | String | No |  | The public number of the project from which the item are being requested.
items.delivery.deliver_to | String | No |  | Deliver To text.
items.delivery.location_type | String | No | JOB SITE | Where the requester would like the product to be delivered. Template has a list of optional values.
items.delivery.instructions | String | No |  | Delivery instructions the requester would like submitted to the vendor responsible for delivering the items.
items.delivery.labeling_instructions | String | No |  | Labeling instructions the requester would like submitted to the vendor responsible for delivering the items.
items.delivery.packaging_instructions | String | No |  | Packaging instructions the requester would like submitted to the vendor responsible for delivering the items.
items.work_breakdown.work_order_id | String | No |  | Contractor defined Work Order Id that was assigned to the product.
items.work_breakdown.work_order_name | String | No |  | Contractor defined Work Order Name that was assigned to the product.
items.work_breakdown.spool_id | String | No |  | Contractor defined Spool Id that was assigned to the product.
items.work_breakdown.spool_name | String | No |  | Contractor defined Spool name that was assigned to the product.
items.work_breakdown.building_name | String | No |  | Name of the building in which the product will be installed.
items.work_breakdown.level | String | No |  | Level of the building in which the product will be installed.
items.work_breakdown.space | String | No |  | Space of the building in which the product will be installed.
items.work_breakdown.sub_space | String | No |  | Sub-space of the building in which the product will be installed.
items.work_breakdown.system | String | No |  | Name of the system in which the product will be installed.
items.work_breakdown.arch_symbol | String | No |  | Architectural symbol of the product.
items.work_breakdown.tag | String | No |  | Text of what should appear on a tag for the item.
items.job_cost .cinx_phase_guid | String (GUID format) | No |  | CINX Id for the Phase/Sub-Job assigned to the item.
items.job_cost.phase_name | String | No |  | Name for the Phase/Sub-Job assigned to the item.
items.job_cost.cinx_material_cost_code_guid | String (GUID format) | No |  | CINX Id for the Material Cost Code assigned to the item.
items.job_cost.material_cost_code_name | String | No |  | Name for the Material Cost Code assigned to the item.
items.job_cost.cinx_category_guid | String (GUID format) | No |  | CINX Id for the Category assigned to the item.
items.job_cost.category_name | String | No |  | Name for the Category assigned to the item.
items.taxes.taxable | Boolean | Yes | FALSE | Indicator defining if the product is taxable.
items.taxes.cinx_guid | String (GUID format) | No |  | CINX Id for the Tax Group assigned to the item.
items.taxes.tax_group_name | String | No |  | Name of the Tax Group assigned to the item.
items.design.model_item_guid | String | No |  | Id assigned by the authoring system that placed the item in the model.
items.design.model_name | String | No |  | Name of the model in which the item is located.
items.design.model_file | String | No |  | File name of the model in which the item is located.


## Get Req Number
### API Endpoint - Get a New Requisition Number

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"req": "REQ-0003"
		}
    ]
}
```
 `GET`

This endpoint will be used to get a value to be used in the number field of a new requisition.

**Notes** 

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/req**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/req`


## Create Req
### API Endpoint - Create a New Requisition

`POST`

This endpoint will be used to create a new requisition.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-req-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-req-import?body=json`

<aside class="notice">
The POST payload will be processed asynchronously.
</aside>

## Modify Req
### API Endpoint - Modify a Requisition

`PUT`

This API call will be used to modify an existing CINX requisition.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-req-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-req-import?body=json`

<aside class="notice">
The PUT payload will be processed asynchronously.
</aside>
