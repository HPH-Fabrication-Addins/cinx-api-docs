# Returns

## Return Definition
### CINX Object Defintion - Requisition

A CINX Return is a contractor initiated process of returning previously purchased products to the vendor from which it was sourced. Part of the return process is receiving an RMA from a vendor which will be attached the the return. In CINX an organization may establish the return reasons and actions that are avaialable to users when returning products.

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must have a unique number
  - Must have at least one item before it can be submitted

**Supported API Services**

  - [Get a List of Returns](#get-return-list)
  - [Get a Return](#get-return)
  - [Get a Return Template](#get-return-template)
  - [Get a Return Number](#get-return-number)
  - [Create a Return](#create-return)
  - [Modify a Return](#modify-return)

## Get Return List
### API Endpoint - Get a List of Returns

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "03dfb081-fc43-5196-8b58-d8277278bc59",
			"number": "R000001",
			"name": "R000001",
			"workflow_status": "RMA REQUESTED",
			"rma_number": null,
			"date_rma_expires": null,
			"reason_name": null,
			"action_name": "Replace Item",
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

This endpoint will be used to get a list of returns. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/returns**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/returns`


**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}

## Get Return
### API Endpoint - Get a Return

`GET`

This endpoint will be used to get the details of a specific return. Note: This response will include the return’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/return{cinx_guid}**

The cinx_guid will be the return's CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/return/03dfb081-fc43-5196-8b58-d8277278bc59`

## Get Return Template
### API Endpoint - Get a Return Template

`GET`

This endpoint will be used to get a CINX Template for a return.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/return**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/return`


The table below defines the input fields within the template.

## Get Return Number
### API Endpoint - Get a New Return Number

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"return": "RET-000001"
		}
    ]
}
```
`GET`

This endpoint will be used to get a value to be used in the number field of a new return.

**Notes**

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/return**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/return`

## Create Return
### API Endpoint - Create a New Return

`POST`

This endpoint will be used to create a new return.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-return-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-return-import?body=json`

<aside class="notice">
The POST payload will be processed asynchronously.
</aside>

## Modify Return
### API Endpoint - Modify a Return

`PUT`

This API endpoint will be used to modify an existing CINX return.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-return-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-return-import?body=json`

<aside class="notice">
The PUT payload will be processed asynchronously.
</aside>
