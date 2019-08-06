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

  - {cinx_commerce_guid}

**ship_via**: will limit results to a specific ship via value

  - Available options are: SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE

**deliver_date**: will limit results to a specific need-by or delivery-by date

  - Date Format: YYYY-MM-DD

**submitter**: will limit results to a specified CINX user

  - {CINX_User_Id}

**number**: will limit results to a specified transaction number

  - {transaction_number}

## Get RFQ
### API Endpoint - Get an RFQ

`GET`

This endpoint will be used to get the details of a specific RFQ.  Note: This response will include the RFQ’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/rfq/{cinx_guid}**

The cinx_guid will be the RFQ’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/rfq/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

## Get RFQ Template
### API Endpoint - Get an RFQ Template

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
