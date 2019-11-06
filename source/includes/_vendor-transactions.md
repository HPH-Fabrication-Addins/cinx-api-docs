# Vendor Transactions

## Get Vendor RFQs
### API Endpoint - Get a List of RFQs Submitted to a Vendor

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

 This endpoint will be used to get a list of RFQs submitted to a specified vendor. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendor/{cinx_commerce_guid}/rfqs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/7880c854-017f-5359-96de-fdef626c33cf/rfqs`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, QUOTED
project | Limits results to a single project. | {cinx_project_id}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Vendor Quotes
### API Endpoint - Get a List of Quotes Submitted by a Vendor

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
		"submitter": "eb stone",
		"date_received": "2019-07-25",
		"date_expires": "2019-08-26",
		"date_requested": "",
		"project_number": "WTS-2019-06",
		"project_name": "HPH HQ Renovation",
		"rfq_number": "RFQ-456464",
		"rfq_name": "RFQ-456464",
		"links": [],
		"item_count": 11
	}]
}
```
 `GET`

This endpoint will be used to get a list of Quotes submitted by a specified vendor. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendor/{cinx_commerce_guid}/quotes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/7880c854-017f-5359-96de-fdef626c33cf/quotes`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ERP PENDING, ERP ACCEPTED, ERP FAILED
project | Limits results to a single project. | {cinx_project_id}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Vendor POs
### API Endpoint - Get a List of POs Submitted to a Vendor

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
			"workflow_status": "SUBMITTED",
			"procurement_status": "ORDERED",
			"vendor_number": "H125",
			"vendor_name": "Hilti",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"date_order_by": "2019-06-07",
			"date_submitted": "2019-06-06",
			"submitter": "Will Stone",
			"date_need_by": "2019-06-11",
			"date_received": "",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
			"phase": "First Floor",
			"material_cost_code": "101-1025",
			"category": null,
			"tax_group": "TAX-03",
			"terms": "0/0",
			"quote_number": null,
			"quote_name": null,
			"erp_status": "NOT SUBMITTED",
			"external_references": [],
			"item_count": 15
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of POs submitted to a specified vendor. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendor/{cinx_commerce_guid}/pos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/7880c854-017f-5359-96de-fdef626c33cf/pos`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
procurement | Limits results to a specific procurement status. | NOT ORDERED, ORDER PENDING, ORDERED, BACK-ORDERED, DELIVERED, RETURNED, CANCELLED, CLOSED, ON-HOLD, INVOICE-APPROVED
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, ERP PENDING, ERP ACCEPTED, ERP FAILED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
project | Limits results to a single project. | {cinx_project_id}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Vendor POCOs
### API Endpoint - Get a List of PO Change Orders Submitted to a Vendor

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
			"submitter": "Will Stone",
			"date_need_by": "2019-06-14",
			"phase": "First Floor",
			"material_cost_code": "101-1025",
			"category": null,
			"tax_group": "TAX-03",
			"terms": "0/0",
			"erp_status": "NOT SUBMITTED",
			"external_references": [],
			"item_count": 2
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of PO Change Orders submitted to a specified vendor. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendor/{cinx_commerce_guid}/pocos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/7880c854-017f-5359-96de-fdef626c33cf/pocos`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
procurement | Limits results to a specific procurement status. | NOT ORDERED, ORDER PENDING, ORDERED, BACK-ORDERED, DELIVERED, RETURNED, CANCELLED, CLOSED, ON-HOLD, INVOICE-APPROVED
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, ERP PENDING, ERP ACCEPTED, ERP FAILED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
project | Limits results to a single project. | {cinx_project_id}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Vendor Deliveries
### API Endpoint - Get a List of Deliveries for a Vendor

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
			"workflow_status": "INCOMPLETE",
			"vendor_number": "H125",
			"vendor_name": "Hilti",
			"ship_via": "SUPPLIER TRUCK",
			"location_type": "FABRICATION SHOP",
			"location_name": null,
			"date_received": "2019-06-07",
			"receiver": "Will Stone",
			"total_weight": "456",
			"packing_slip_number": "54654645",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
			"po_number": "PO-123",
			"po_name": "PO123",
			"date_need_by": "2019-06-11",
			"external_references": [],
			"item_count": 15
		}
    ]
}
```
 `GET`

This endpoint will be used to get a list of Deliveries for a vendor. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendor/{cinx_commerce_guid}/deliveries**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/7880c854-017f-5359-96de-fdef626c33cf/deliveries`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
project | Limits results to a single project. | {cinx_project_id}
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Vendor Invoices
### API Endpoint - Get a List of Invoices from a Vendor

> The above code returns JSON structured like this:

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "8ead0386-496b-571c-b14f-09eafeeb6758",
		"number": "I456123",
		"name": "I456123",
		"workflow_status": "PENDING E-INVOICE",
		"erp_status": "NOT SUBMITTED",
		"assigned_to": "Will Stone",
		"entry_type": "MANUAL",
		"entered_by": null,
		"date_entered": "",
		"accept_type": "MANUAL",
		"accepted_by": null,
		"date_accepted": "",
		"date_issued": "2019-06-08",
		"date_payment_due": "2019-07-08",
		"vendor_number": "H125",
		"vendor_name": "Hilti",
		"po_number": "PO123",
		"po_name": "PO123",
		"project_number": "WTS-2017-03",
		"project_name": "HPH HQ Renovation",
		"external_references": [],
		"item_count": 15
	}]
}
```
`GET`

This endpoint will be used to get a list of Invoices from a vendor. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendor/{cinx_commerce_guid}/invoices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/7880c854-017f-5359-96de-fdef626c33cf/invoices`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
status | Limits results to a specific status. | PENDING E-INVOICE, ENTERED, REVIEWED, ACCEPTED, IN-DISPUTE, ON-HOLD, REJECTED, SUBMITTED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
project | Limits results to a single project. | {cinx_project_id}
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Vendor Returns
### API Endpoint - Get a List of Returns for a Vendor

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
			"reason_name": "Wrong Product",
			"action_name": "Replace Item",
			"assigned_to": "Will Stone",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "FABRICATION SHOP",
			"delivery_location_name": null,
			"vendor_number": "H125",
			"vendor_name": "Hilti",
			"po_number": "PO-123",
			"po_name": "PO123",
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
			"external_references": [],
			"item_count": 1
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of Returns for a vendor. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendor/{cinx_commerce_guid}/returns**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/7880c854-017f-5359-96de-fdef626c33cf/returns`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
project | Limits results to a single project. | {cinx_project_id}
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Vendor Back-Orders
### API Endpoint - Get a List of Back-Orders from a Vendor

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
			"vendor_name": "Hilti",
			"work_order_id": null,
			"work_order_name": null,
			"spool_id": null,
			"spool_name": null,
			"project_number": "WTS-2017-03",
			"project_name": "HPH HQ Renovation",
			"po_number": "P19-062819",
			"po_name": "P19-062819",
			"po_submitted_by": "Will Stone"
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of Back-Orders for a vendor. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendor/{cinx_commerce_guid}/back-orders**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/7880c854-017f-5359-96de-fdef626c33cf/back-orders`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
project | Limits results to a single project. | {cinx_project_id}
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
format | Defines the response format type. If not specified, json will be used. | json, xml