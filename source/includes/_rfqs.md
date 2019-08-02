# RFQs

## RFQ Definition
### CINX Object Defintion - Request for Quotation

A CINX Request for Quotation is a compilation of  that a customer wants a vendor(s) to provide pricing on before making ordering/sourcing decisions. The list might be for a whole project, phase, system, pre-fab work-order, spool, or a general list created by a project foreman in the field. 

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Can be submitted to multiple vendors
  - Will be locked after it is submitted

**Supported API Services**

  - Get a List of RFQs
  - Get an RFQ
  - Get an RFQ Template
  - Get an RFQ Number
  - Create an RFQ
  - Modify an RFQ

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
			"status": "IN-PROCESS",
			"submitted_by": "User Not Found",
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
			"date_deliver_by": "2019-06-08",
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"req_number": null,
			"req_name": null,
			"phase": null,
			"cost_code": null,
			"category": null,
			"item_count": 113
		}
    ]
}
```
This endpoint will be used to get a list of RFQs. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/rfqs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/rfqs`

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


## Get RFQ
### API Endpoint - Get an RFQ

This request will be used to get the details of a specific RFQ.  Note: This response will include the RFQ’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/rfq/{cinx_guid}**

The cinx_guid will be the RFQ’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/rfq/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

HTTP Method: `GET`

## Get RFQ Template
### API Endpoint - Get an RFQ Template

This request will be used to get a CINX Template for an RFQ.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/rfq**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/rfq`

HTTP Method: `GET`

## RFQ Template Fields
### Definition of the RFQ Template's Fields

The table below defines the fields within the template.

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
This endpoint will be used to get a value to be used in the number field of a new RFQ.

**Notes** 

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.
  - If a company is using a project number as a component within the numbering of the requisition, the CINX project Id can be added to the url using this syntax: **?project={CINX Project Id}**

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/rfq**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/rfq`

HTTP Method: `GET`

## Create RFQ
### API Endpoint - Create a New RFQ

This endpoint will be used to create a new RFQ.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-rfq-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-rfq-import?body=json`

HTTP Method: `POST`

Processing Type: `Asynchronous`

## Modify RFQ
### API Endpoint - Modify an RFQ

This API call will be used to modify an existing CINX RFQ.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-rfq-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-rfq-import?body=json`

HTTP Method: `PUT`

Processing Type: `Asynchronous`
