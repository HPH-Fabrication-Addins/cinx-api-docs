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
  - Will be locked after it is submitted

**Supported API Services**

  - [Get a List of PO Change Orders](#get-po-co-list)
  - [Get a PO Change Order](#get-po-co)
  - [Get a PO Change Order Template](#get-po-co-template)
  - [Create a PO Change Order](#create-po-co)
  - [Modify a PO Change Order](#modify-po-co)

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
			"workflow_status": "SUBMITTED",
			"procurement_status": "ORDERED",
			"po_number": "PO-123",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
			"vendor_number": "H125",
			"vendor_name": "Hilti",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_submitted": "2019-06-06",
			"submitted_by": "Will Stone",
			"date_need_by": "2019-06-14",
			"phase": "First Floor",
			"material_cost_code": "101-1025",
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
`GET`

This endpoint will be used to get a list of PO Change Orders. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/pocos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/pocos`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
procurement | Limits results to a specific procurement status. | NOT ORDERED, ORDER PENDING, ORDERED, BACK-ORDERED, DELIVERED, RETURNED, CANCELLED, CLOSED, ON-HOLD, INVOICE-APPROVED
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, ERP PENDING, ERP ACCEPTED, ERP FAILED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}

## Get PO CO
### API Endpoint - Get a PO Change Order

`GET`

This endpoint will be used to get the details of a specific PO Change Order.  Note: This response will include the PO Change Order’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/poco/{cinx_guid}**

The cinx_guid will be the PO Change Order’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/poco/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

## Get PO CO Template
### API Endpoint - Get a PO Change Order Template

`GET`

This endpoint will be used to get a CINX Template for a PO Change Order.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/poco**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/poco`


The table below defines the input fields within the template.

## Create PO CO
### API Endpoint - Create a PO Change Order

`POST`

This endpoint will be used to create a new PO Change Order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-poco-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-poco-import?body=json`

<aside class="notice">
The POST payload will be processed asynchronously.
</aside>

## Modify PO CO
### API Endpoint - Modify a PO Change Order

`PUT`

This API endpoint will be used to modify an existing CINX PO Change Order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-poco-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-poco-import?body=json`

<aside class="notice">
The PUT payload will be processed asynchronously.
</aside>