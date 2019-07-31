# Requisitions

## Req Definition
### CINX Object Defintion - Requisition

A CINX Material Requisition is a compilation of parts that need to be purchased.  The list might be for a whole project, phase, system, pre-fab work-order, spool, or a general list created by a project foreman in the field. Requisitions are created to request the materials.  The parts on a requisition might also contain items from multiple projects that are combined into one purchase to achieve volume pricing.

It is important to understand that the parts on a requisition may be divided onto different purchase orders which might be sent to different vendors.

**Dependencies and Business Rules**
- Must be created by a CINX user linked to an active CINX company.
- Must have a unique number
- Must have a procurement status
- Must be assigned to a valid CINX user
- Must have at least one item before it can be submitted

**Supported API Services**
- Get a List of Requisitions
- Get a Requisition
- Get a Requisition Template
- Get a Requisition Number
- Create a Requisition
- Modify a Requisition

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
			"tx_type": "FIELD",
			"current_owner_name": "Karl Stone",
			"procurement_status": "SUBMITTED",
			"submitted_by": "Will Stone",
			"date_submitted": "2019-06-12 22:25:21Z",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "JOB SITE",
			"delivery_location_name": null,
			"date_deliver_by": "2019-06-14 22:21:07Z",
			"vendor_number": null,
			"vendor_name": "National Sales Company",
			"links": [],
			"project_number": "WTS-2017-04",
			"project_name": "WTS-2017-04 - ATC Denver",
			"phase": "First Floor",
			"cost_code": "101-1025",
			"category": "MAT",
			"work_order": null,
			"spool": null,
			"allow_substitutes": true,
			"item_count": 4
		}
    ]
}
```
This endpoint will be used to get a list of requisitions. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/reqs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/reqs`

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


## Get Req
### API Endpoint - Get a Requisition

This request will be used to get the details of a specific requisition.  Note: This response will include the requisition’s items.

URL Pattern: **{api path}/{api_version}sub/{api_token}/req/{cinx_guid}**

The cinx_guid will be the Requisition’s CINX GUID.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/req/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

HTTP Method: `GET`

## Get Req Template
### API Endpoint - Get a Requisition Template

This request will be used to get a CINX Template for a requisition.

URL Pattern: **{api path}/{api_version}sub/{api_token}/template/req**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/req`

HTTP Method: `GET`

## Req Template Fields
### Definition of the Req Template's Fields

The table below defines the fields within the template.

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
This endpoint will be used to get a value to be used in the number field of a new requisition.

**Notes** 
- The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.
- If a company is using a project number as a component within the numbering of the requisition, the CINX project Id can be added to the url using this syntax: **?project={CINX Project Id}**

URL Pattern: **{api path}/{api_version}sub/{api_token}/auto-number/req**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/req`

HTTP Method: `GET`

## Create Req
### API Endpoint - Create a New Requisition

This endpoint will be used to create a new requisition.

**Notes**

- A CINX Template is available that documents the available fields that can be populated.
- A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-req-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-req-import?body=json`

HTTP Method: `POST`

## Modify Req
### API Endpoint - Modify a Requisition

This API call will be used to modify an existing CINX requisition.

**Notes**

- A CINX Template is available that documents the available fields that can be populated.
- A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-req-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-req-import?body=json`

HTTP Method: `PUT`
