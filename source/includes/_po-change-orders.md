# PO Change Orders

## PO Change Order Definition
### CINX Object Defintion - PO Change Order

A CINX Purchase Order Change Order is created when changes need to be made to a previously submitted purchase order. Example of changes include: changing a price or quantity; adding or modifying job costing information; adding or removing a item row. 

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must be linked to a previously created purchase order
  - PO Change Orders will be automatically numbered by the system
  - Must have a procurement status
  - Must have at least one item before it can be submitted

**Supported API Services**

  - Get a List of PO Change Orders
  - Get a PO Change Order
  - Get a PO Change Order Template
  - Create a PO Change Order
  - Modify a PO Change Order

## Get PO CO List
### API Endpoint - Get a List of PO Change Orders

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "a9863525-d926-5441-9f9c-aa47a285a19b",
			"number": "-01",
			"name": "PO123-01",
			"description": null,
			"status": "SUBMITTED",
			"procurement_status": "ORDERED",
			"tx_type": "CHANGE ORDER",
			"po_number": "PO-123",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_submitted": "2019-06-06",
			"submitted_by": "Will Stone",
			"date_deliver_by": "2019-06-14",
			"phase": "First Floor",
			"cost_code": "101-1025",
			"category": null,
			"tax_group": "TAX-03",
			"terms": "0/0",
			"erp_status": "NOT SUBMITTED",
			"links": [],
			"item_count": 2
		}
    ]
}
```
This endpoint will be used to get a list of PO Change Orders. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/pocos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/pocos`

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


## Get PO CO
### API Endpoint - Get a PO Change Order

This request will be used to get the details of a specific PO Change Order.  Note: This response will include the PO Change Order’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/poco/{cinx_guid}**

The cinx_guid will be the PO Change Order’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/poco/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

HTTP Method: `GET`

## Get PO CO Template
### API Endpoint - Get a PO Change Order Template

This request will be used to get a CINX Template for a PO Change Order.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/poco**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/poco`

HTTP Method: `GET`


The table below defines the input fields within the template.

## Create PO CO
### API Endpoint - Create a PO Change Order

This endpoint will be used to create a new PO Change Order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-poco-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-poco-import?body=json`

HTTP Method: `POST`

Processing Type: `Asynchronous`

## Modify PO CO
### API Endpoint - Modify a PO Change Order

This API call will be used to modify an existing CINX PO Change Order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-poco-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-poco-import?body=json`

HTTP Method: `PUT`

Processing Type: `Asynchronous`
