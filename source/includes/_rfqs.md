# RFQs

## RFQ Definition
### CINX Object Definition - Request for Quotation

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
			"number": "RFQ-1254",
			"name": "RFQ-1254",
			"description": "Sample RFQ Description Text",
			"workflow_status": "SUBMITTED",
			"submitter": "Will Stone",
			"date_submitted": "2019-06-01",
			"date_respond_by": "2019-06-03",
			"vendors": [
				{
					"number": "H125",
					"name": "Hilti"
				}
			],
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "OFFICE",
			"delivery_location_name": null,
			"date_need_by": "2019-06-08",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
			"req_number": null,
			"req_name": null,
			"phase": null,
			"material_cost_code": null,
			"category": null,
			"external_references": [],
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

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, QUOTED
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

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
		"item_count": 3,
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
			"cinx_guid": null,
			"number": null,
			"name": null
		},
		"requisition": {
			"cinx_guid": null,
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
				"requisition": {
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
				},
				"attributes": []
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

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

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
				"taxable": true,
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
				"quantity": 1,
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
				},
				"attributes": [
					{
						"name": null,
						"value": null
					}]
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


**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml


The table below defines the input fields within the template.

**TEMPLATE FIELDS**

Name | Data Type | Required | Default | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; PUT = Yes |  | CINX System Id.
number | String | Yes |  | Public number for the object.
name | String | Yes |  | Public name for the object.
description | String | No |  | Public description for the object.
terms | String | No |  | Transaction terms.
user_comment | String | No |  | General comment defined by a CINX user.
dates.respond_by | Date (YYYY-MM-DD) | No |  | Date the requester would like the vendor to provide the quoted prices.
dates.need_by | Date (YYYY-MM-DD) | No |  | Date the products on the RFQ need to be delivered to the specified delivery location.
dates.submitted | Date (YYYY-MM-DD) | No |  | Date the RFQ was submitted to the vendor. Field is not modifiable.
vendor.cinx_commerce_guid | String (GUID Format) | No |  | CINX Commerce Id for the vendor that will receive the RFQ.
vendor.number | String | No |  | The public number of the vendor that will receive the RFQ.
project.cinx_guid | String (GUID Format) | No |  | CINX Project Id.
project.number | String | No |  | The public number of the project for which the items are linked.
delivery.address1 | String | No |  | Address 1 value for the location to which the products on the RFQ are to be delivered.
delivery.address2 | String | No |  | Address 2 value for the location to which the products on the RFQ are to be delivered.
delivery.address3 | String | No |  | Address 3 value for the location to which the products on the RFQ are to be delivered.
delivery.city | String | No |  | City to which the products on the RFQ are to be delivered.
delivery.state | String | No |  | State to which the products on the RFQ are to be delivered. Two-character alpha abbreviation.
delivery.postal_code | String | No |  | Postal/Zip Code to which the products on the RFQ are to be delivered.
delivery.country | String | Yes | USA | Country to which the products on the RFQ are to be delivered. Three-character alpha abbreviation.
delivery.ship_via | String | No |  | How the products are to be delivered or otherwise acquired. Template has a list of optional values.
delivery.fob_type | String | No |  | F.O.B. Type. Template has a list of optional values.
delivery.ship_from | String | No |  | Location from which the requester would like the materials on the RFQ to be shipped.
delivery.attention | String | No |  | User-defined delivery attention.
delivery.location_type | String | Yes | JOB SITE | Type of location where the requester would like the materials delivered. Template has a list of optional values.
delivery.Instructions | String | No |  | General delivery instructions to be used on an order.
job_cost_defaults.cinx_phase_guid | String (GUID Format) | No |  | Transaction level default. CINX Id for the Phase/Sub-Job assigned to the items on the RFQ.
job_cost_defaults.phase_name | String | No |  | Transaction level default. Name for the Phase/Sub-Job assigned to the items on the RFQ.
job_cost_defaults.cinx_material_cost_code_guid | String (GUID Format) | No |  | Transaction level default. CINX Id for the Material Cost Code assigned to the items on the RFQ.
job_cost_defaults.material_cost_code_name | String | No |  | Transaction level default. Name for the Material Cost Code assigned to the items on the RFQ.
job_cost_defaults.cinx_category_guid | String (GUID Format) | No |  | Transaction level default. CINX Id for the Category assigned to the items on the RFQ.
job_cost_defaults.category_name | String | No |  | Transaction level default. Name for the Category assigned to the items on the RFQ.
taxes.taxable | Boolean | Yes | TRUE | Transaction level default. Indicator defining if the products on the RFQ are taxable.
taxes.cinx_guid | String (GUID Format) | No |  | Transaction level default. CINX Id for the Tax Group assigned to the items on the RFQ.
taxes.tax_group_name | String | No |  | Transaction level default. Name for the Tax Group assigned to the items on the RFQ.
external_references.type | String | No |  | Non-CINX system reference type.
external_references.description | String | No |  | Non-CINX system reference description.
external_references.value | String | No |  | Non-CINX system reference value.
items.cinx_guid | String (GUID Format) | POST = No; Put = Yes |  | CINX System Id.
items.quantity | Real | Yes | 1 | Quantity of the item.
items.date_need_by | Date (YYYY-MM-DD) | No |  | Date the product needs to be delivered to the specified delivery location.
items.allow_substitutes | Boolean | Yes | TRUE | Indicator if the product can be sourced from an alternate manufacturer.
items.hph_code | String | No |  | HPH Item Code for the item.
items.org_item_id | String | No |  | The requesting company's Org Item Id. User-friendly code.
items.org_system_id | String | No |  | The requesting company's Org System Item Id. Unique Id code.
items.mfr_part_number | String | No |  | Manufacturer-defined Part/Catalog Number.
items.upc | String | No |  | Manufacturer-defined UPC Number.
items.size | String | No |  | Size of the item.
items.description | String | No |  | Description of the item.
items.mfr_name | String | No |  | Name of the manufacturer or fabricator that produces the item.
items.item_type | String | No |  | Classification name of the item.
items.project.cinx_guid | String | No |  | CINX Project Id.
items.project.number | String | No |  | The public number of the project.
items.delivery.ship_via | String | No |  | How the product is to be delivered or otherwise acquired. Template has a list of optional values.
items.delivery.deliver_to | String | No |  | Deliver To text.
items.delivery.location_type | String | Yes | JOB SITE | Where the requester would like the product to be delivered. Template has a list of optional values.
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
items.design.model_item_guid | String (GUID Format) | No |  | Id assigned by the authoring system that placed the item in the model.
items.design.model_name | String | No |  | Name of the model in which the item is located.
items.design.model_file | String | No |  | File name of the model in which the item is located.
items.design.drawing_number | String | No |  | Number of the drawing on which the item is located.
items.design.drawing_name | String | No |  | Name of the drawing on which the item is located.
items.attributes.name | String | No |  | Name of the attribute.
items.attributes.value | String | No |  | Value of the attribute.

<aside class="notice">
If modifying the vendor array, please submit all the desired vendors in the PUT request. 
</aside>

## Get RFQ Number
### API Endpoint - Get a New RFQ Number

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getRfqNumber(cinx_api_token)
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

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Create RFQ
### API Endpoint - Create a New RFQ

`POST`

This endpoint will be used to create a new RFQ.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-rfq-import?body=json**

URL Samples: 

  - Asynchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-rfq-import?body=json`
  - Synchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-rfq-import?body=json&synchronous=1`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json
synchronous | Switch to have the payload processed synchronously. | 1

<aside class="notice">
By default the POST payload will be processed asynchronously.  See the optional URL parameters table for a synchronous option.
</aside>

## Modify RFQ
### API Endpoint - Modify an RFQ

`PUT`

This API endpoint will be used to modify an existing CINX RFQ.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-rfq-import?body=json**

URL Samples: 

  - Asynchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-rfq-import?body=json`
  - Synchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-rfq-import?body=json&synchronous=1`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
synchronous | Switch to have the payload processed synchronously. | 1


<aside class="notice">
Modifications in a PUT request will be processed only if the RFQ is UNLOCKED and the workflow status is IN-PROCESS.
</aside>

<aside class="notice">
By default the PUT payload will be processed asynchronously.  See the optional URL parameters table for a synchronous option.
</aside>

## Get RFQ Quotes
### API Endpoint - Get a List of Quotes for an RFQ

> The above code returns JSON structured like this:

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "1eb08930-8744-5213-90f0-3ad63a216b20",
		"number": "Q19-789456",
		"name": "Q19-789456",
		"description": "",
		"workflow_status": "RECEIVED",
		"vendor_number": "99999",
		"vendor_name": "Keegan Supply",
		"submitted_by": "eb stone",
		"date_received": "2019-07-25",
		"date_expires": "2019-08-26",
		"date_requested": "",
		"links": [],
		"project_number": "WTS-2019-06",
		"project_name": "HPH HQ Renovation",
		"rfq_number": "RFQ-456464",
		"rfq_name": "RFQ-456464",
		"item_count": 11
	}]
}
```
`GET`

This endpoint will be used to get a list of Quotes for a specified RFQ. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/rfq/{rfq_guid}/quotes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/rfq/8902980f-4a4f-504c-8fc3-2e71067ab59b/quotes`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ERP PENDING, ERP ACCEPTED, ERP FAILED
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_uer_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml