# Project Transactions

## Get Project Reqs
### API Endpoint - Get a List of Requisitions for a Project

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "0854d705-707e-56f2-a230-9440e2472aeb",
			"number": "11 20 17",
			"name": "2017 11 20 test req",
			"description": null,
			"tx_type": "FIELD",
			"current_owner_name": null,
			"procurement_status": "OPEN",
			"submitted_by": "User Not Found",
			"date_submitted": "",
			"ship_via": null,
			"delivery_location_type": "JOB SITE",
			"delivery_location_name": null,
			"date_deliver_by": "",
			"vendor_number": null,
			"vendor_name": null,
			"links": [],
			"project_number": "WTS-2017-04",
			"project_name": "WTS-2017-04 - ATC Denver",
			"phase": null,
			"cost_code": null,
			"category": null,
			"work_order": null,
			"spool": null,
			"allow_substitutes": true,
			"item_count": 5
		}
    ]
}
```
This endpoint will be used to get a list of Requisitions linked to a project. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}/reqs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/reqs`

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

Project Reference: will limit results to a single Project
URL parameter:  **Project={CINX Project Id}**

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

## Get Project RFQs
### API Endpoint - Get a List of RFQs Linked to a Project

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
This endpoint will be used to get a list of RFQs linked to a project. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}/rfqs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/rfqs`

HTTP Method: `GET`

## Get Project Quotes
### API Endpoint - Get a List of Quotes for a Project

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "80e6d9c8-d2e4-5aaa-9bd3-3957430741dd",
			UPDATE PICTURE
		}
    ]
}
```
This endpoint will be used to get a list of Quotes linked to a project. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid/quotes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/quotes`

HTTP Method: `GET`

## Get Project POs
### API Endpoint - Get a List of POs for a Project

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
			"Project_number": "H125",
			"Project_name": "Hilti-6",
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
This endpoint will be used to get a list of POs linked to a specified project. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}/pos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/pos`

HTTP Method: `GET`

## Get Project POCOs
### API Endpoint - Get a List of PO Change Orders for a Project

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
			"Project_number": "H125",
			"Project_name": "Hilti-6",
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
This endpoint will be used to get a list of PO Change Orders linked to a specified project. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}/pocos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/pocos`

HTTP Method: `GET`

## Get Project Deliveries
### API Endpoint - Get a List of Deliveries for a Project

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
			"Project_number": "H125",
			"Project_name": "Hilti-6",
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
This endpoint will be used to get a list of Deliveries for a project. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}/deliveries**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/deliveries`

HTTP Method: `GET`

## Get Project Invoices
### API Endpoint - Get a List of Invoices for a Project

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
			"Project_number": "H125",
			"Project_name": "Hilti-6",
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
This endpoint will be used to get a list of Invoices linked to a project. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}/invoices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/invoices`

HTTP Method: `GET`

## Get Project Returns
### API Endpoint - Get a List of Returns for a Project

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
			"Project_number": "H125",
			"Project_name": "Hilti-6",
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
This endpoint will be used to get a list of Returns linked to a Project. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}/returns**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/returns`

HTTP Method: `GET`

## Get Project Back-Orders
### API Endpoint - Get a List of Back-Orders for a Project

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
This endpoint will be used to get a list of Back-Orders linked to a project. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}/back-orders**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/back-orders`

HTTP Method: `GET`