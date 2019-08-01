# Purchase Orders

## PO Definition
### CINX Object Defintion - Purchase Order

A CINX Purchase Order is a compilation of parts that are being ordered  The list might be for a whole project, phase, system, pre-fab work-order, spool, or a general list created by a project foreman in the field. Requisitions are created to request the materials.  The parts on a requisition might also contain items from multiple projects that are combined into one purchase to achieve volume pricing.

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must have a unique number
  - Must have a procurement status
  - Must have at least one item before it can be submitted

**Supported API Services**

  - Get a List of Purchase Orders
  - Get a Purchase Order
  - Get a Purchase Order Template
  - Get a Purchase Order Number
  - Create a Purchase Order
  - Modify a Purchase Order
  - Get a List of Change Orders for a Purchase Order
  - Get a List of Deliveries for a Purchase Order
  - Get a List of Invoices for a Purchase Order
  - Get a List of Returns for a Purchse Order
  - Update a Purchase Order's ERP Status

## Get PO List
### API Endpoint - Get a List of Purchase Orders

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "80e6d9c8-d2e4-5aaa-9bd3-3957430741dd",
			"number": "PO-123",
			"name": "PO123",
			"description": null,
			"status": "SUBMITTED",
			"procurement_status": "ORDERED",
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_order_by": "2019-06-07",
			"date_submitted": "2019-06-06",
			"submitted_by": "Will Stone",
			"date_deliver_by": "2019-06-11",
			"date_received": "",
			"links": [],
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"phase": "First Floor",
			"cost_code": "101-1025",
			"category": null,
			"tax_group": "TAX-03",
			"terms": "0/0",
			"quote_number": null,
			"quote_name": null,
			"erp_status": "NOT SUBMITTED",
			"item_count": 15
		}
    ]
}
```
This endpoint will be used to get a list of purchase orders. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/pos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/pos`

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


## Get PO
### API Endpoint - Get a Purchase Order

This request will be used to get the details of a specific purchase order.  Note: This response will include the purchase order’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid}**

The cinx_guid will be the purchase orders’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

HTTP Method: `GET`

## Get PO Template
### API Endpoint - Get a Purchase Order Template

This request will be used to get a CINX Template for a purchase order.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/po**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/po`

HTTP Method: `GET`

## PO Template Fields
### Definition of the Purchase Order Template's Fields

The table below defines the fields within the template.

## Get PO Number
### API Endpoint - Get a New Purchase Order Number

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"po": "PO-000001"
		}
    ]
}
```
This endpoint will be used to get a value to be used in the number field of a new purchase order.

**Notes** 

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.
  - If a company is using a project number as a component within the numbering of the requisition, the CINX project Id can be added to the url using this syntax: **?project={CINX Project Id}**

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/po**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/po`

HTTP Method: `GET`

## Create PO
### API Endpoint - Create a New Purchase Order

This endpoint will be used to create a new purchase order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-po-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-po-import?body=json`

HTTP Method: `POST`

## Modify PO
### API Endpoint - Modify a Purchase Order

This API call will be used to modify an existing CINX purchase order.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-po-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-po-import?body=json`

HTTP Method: `PUT`

## Get PO Change Orders
### API Endpoint - Get a List of PO Change Orders for a Purchase Order

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
This endpoint will be used to get a list of PO Change Orders for a specified purchase order. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid}/pocos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/pocos`

HTTP Method: `GET`

## Get PO Deliveries
### API Endpoint - Get a List of Deliveries for a Purchase Order

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "f116ad07-ab08-5b87-ad42-18cab454e086",
			"number": "D000012",
			"name": "D000012",
			"description": null,
			"status": "INCOMPLETE",
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_received": "2019-06-07",
			"received_by": "Will Stone",
			"total_weight": "456",
			"packing_slip": "54654645",
			"links": [],
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"po_number": "PO-123",
			"po_name": "PO123",
			"date_deliver_by": "2019-06-11",
			"item_count": 15
		}
    ]
}
```
This endpoint will be used to get a list of Deliveries for a vendor. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid}/deliveries**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/deliveries`

HTTP Method: `GET`

## Get PO Invoices
### API Endpoint - Get a List of Invoices for a Purchase Order

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "8ead0386-496b-571c-b14f-09eafeeb6758",
			"number": "I456123",
			"name": "I456123",
			"status": "PENDING E-INVOICE",
			"erp_status": "NOT SUBMITTED",
			"current_owner_name": "Will Stone",
			"entry_method": "MANUAL",
			"entered_by": null,
			"date_entered": "",
			"accept_method": "MANUAL",
			"accepted_by": null,
			"date_issued": "2019-06-08",
			"payment_due": "2019-06-21 00:00:00Z",
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"po_number": "",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"links": [],
			"item_count": 15
		}
    ]
}
```
This endpoint will be used to get a list of Invoices for a purchase order. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid}/invoices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/invoices`

HTTP Method: `GET`

## Get PO Returns
### API Endpoint - Get a List of Returns for a Purchase Order

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
This endpoint will be used to get a list of Returns for a purchase order. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid/returns**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/returns`

HTTP Method: `GET`

## Get PO Back-Orders
### API Endpoint - Get a List of Back-Orders for a Purchase Order

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "076bd4bb-d6d9-5096-96f2-ec105d0562b1",
			"date_expected_delivery": null,
			"date_po_deliver_by": null,
			"date_informed": null,
			"date_last_updated": null,
			"reason": null,
			"quantity_backordered": 1,
			"quantity_shipped": 0,
			"quantity_po": 1,
			"org_item_id": null,
			"vendor_item_id": null,
			"mfr_part_number": null,
			"mfr_order": null,
			"hph_code": "326ZU6542",
			"upc": "67024006745",
			"org_description": "Floor, Z1400 Adjustable, 4",
			"cinx_description": null,
			"mfr_description": null,
			"mfr_name": null,
			"delivery_location_type": null,
			"delivery_location_name": "",
			"vendor_number": "",
			"vendor_name": "Hilti-6",
			"work_order_id": null,
			"work_order_name": null,
			"spool_id": null,
			"spool_name": null,
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"po_number": "P19-062819",
			"po_name": "P19-062819",
			"po_submitted_by": "Will Stone"
		}
    ]
}
```
This endpoint will be used to get a list of Back-Orders for a purchase order. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid/back-orders**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/back-orders`

HTTP Method: `GET`

## ERP Status Update
### API Endpoint - Update a Purchase Order's ERP Status

This API call will be used to modify the erp status for a purchase order in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/po/{cinx_guid/erp/applied**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/a9863525-d926-5441-9f9c-aa47a285a19b/erp/applied`

HTTP Method: `PUT`