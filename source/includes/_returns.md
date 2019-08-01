# Returns

## Return Definition
### CINX Object Defintion - Requisition

A CINX Return is a contractor initiatd process of returning previously purchased products to the vendor from which it was sourced. Part of the return process is receiving an RMA from a vendor which will be attached the the return. In CINX an organization may establish the return reasons and actions that are avaialable to users when returning products.

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must have a unique number
  - Must have at least one item before it can be submitted

**Supported API Services**

  - Get a List of Returns
  - Get a Return
  - Get a Return Template
  - Get a Return Number
  - Create a Return
  - Modify a Return

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
This endpoint will be used to get a list of returns. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/returns**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/returns`

HTTP Method: `GET`

**Supported Filters**

Delivery Location Type: will limit results to a specific delivery type location
URL Parameter: **delivery={option from below}**
Available options are: JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR

Procurement Status: will limit results to a specific procurement status
URL Parameter: **procurement={option from below}**
Available options are: OPEN, SUBMITTED, IN-REVIEW, APPROVED, APPROVED W/MODS, REJECTED, PENDING ORDER, COMPLETE, CLOSED, CANCELLED, RESUBMITTED

Project Reference: will limit results to a single project
URL parameter:  **project={CINX project Id}**

Vendor Reference: will limit results to a single vendor
URL parameter:  **vendor={CINX vendor Id}**

Ship Via: will limit results to a specific ship via value
URL Parameter: **ship_via={option from below}**
Available options are: SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE

Deliver By Date: will limit results to a specific date
URL Parameter: **deliver_date={date}**
Date Format: YYYY-MM-DD

Submitter: will limit results to a specified CINX user
URL parameter:  **submitter={submitter CINX User Id}**

Current Owner: will limit results to a specified CINX user to whom the transaction is assigned
URL parameter:  **owner={CINX User Id}**

Transaction Number: will limit results to a specified transaction number
URL parameter:  **number={transaction number}**


## Get Return
### API Endpoint - Get a Return

This request will be used to get the details of a specific return  Note: This response will include the return’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/return{cinx_guid}**

The cinx_guid will be the return's CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/return/03dfb081-fc43-5196-8b58-d8277278bc59`

HTTP Method: `GET`

## Get Return Template
### API Endpoint - Get a Return Template

This request will be used to get a CINX Template for a return.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/return**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/return`

HTTP Method: `GET`

## Return Template Fields
### Definition of the Return template's Fields

The table below defines the fields within the template.

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
This endpoint will be used to get a value to be used in the number field of a new return.

**Notes**

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/return**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/return`

HTTP Method: `GET`

## Create Return
### API Endpoint - Create a New Return

This endpoint will be used to create a new return.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-return-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-return-import?body=json`

HTTP Method: `POST`

## Modify Return
### API Endpoint - Modify a Return

This API call will be used to modify an existing CINX return.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-return-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-return-import?body=json`

HTTP Method: `PUT`
