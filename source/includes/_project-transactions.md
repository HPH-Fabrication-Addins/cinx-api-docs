# Project Transactions

## Get Project Reqs
### API Endpoint - Get a List of Requisitions for a Project

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "e98e2fc5-f59b-5091-8b05-54edaa9284cc",
			"number": "R-101",
			"name": "req-101",
			"description": "Sample Req Description",
			"tx_sub_type": "FIELD",
			"assigned_to": "Karl Stone",
			"procurement_status": "SUBMITTED",
			"submitter": "Will Stone",
			"date_submitted": "2019-06-12",
			"ship_via": "SUPPLIER TRUCK",
			"delivery_location_type": "JOB SITE",
			"delivery_location_name": null,
			"date_need_by": "2019-06-14",
			"vendor_number": "N-123",
			"vendor_name": "National Sales Company",
			"project_number": "WTS-2017-04",
			"project_name": "HPH Fab Shop Air System",
			"phase": "First Floor",
			"material_cost_code": "101-1025",
			"category": "MAT",
			"work_order": null,
			"spool": null,
			"allow_substitutes": true,
			"external_references": [],
			"item_count": 4
		}
    ]
}
```
 `GET`

This endpoint will be used to get a list of Requisitions linked to a project. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/reqs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/reqs`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
procurement | Limits results to a specific procurement status. | OPEN, SUBMITTED, IN-REVIEW, APPROVED, APPROVED W/MODS, REJECTED, PENDING ORDER, COMPLETE, CLOSED, CANCELLED, RESUBMITTED
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

## Get Project RFQs
### API Endpoint - Get a List of RFQs Linked to a Project

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

This endpoint will be used to get a list of RFQs linked to a project. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/rfqs**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/rfqs`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, QUOTED
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

## Get Project Quotes
### API Endpoint - Get a List of Quotes for a Project

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
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
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of Quotes linked to a project. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid/quotes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/quotes`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ERP PENDING, ERP ACCEPTED, ERP FAILED
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

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

This endpoint will be used to get a list of POs linked to a specified project. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/pos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/pos`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
procurement | Limits results to a specific procurement status. | NOT ORDERED, ORDER PENDING, ORDERED, BACK-ORDERED, DELIVERED, RETURNED, CANCELLED, CLOSED, ON-HOLD, INVOICE-APPROVED
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, ERP PENDING, ERP ACCEPTED, ERP FAILED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

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

This endpoint will be used to get a list of PO Change Orders linked to a specified project. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/pocos**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/pocos`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
procurement | Limits results to a specific procurement status. | NOT ORDERED, ORDER PENDING, ORDERED, BACK-ORDERED, DELIVERED, RETURNED, CANCELLED, CLOSED, ON-HOLD, INVOICE-APPROVED
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, ERP PENDING, ERP ACCEPTED, ERP FAILED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

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

This endpoint will be used to get a list of Deliveries for a project. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/deliveries**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/deliveries`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
vendor | Limits results to a single vendor. | {organization's vendor number}
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

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
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of Invoices linked to a project. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/invoices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/invoices`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
status | Limits results to a specific status. | PENDING E-INVOICE, ENTERED, REVIEWED, ACCEPTED, IN-DISPUTE, ON-HOLD, REJECTED, SUBMITTED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
vendor | Limits results to a single vendor. | {organization's vendor number}
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

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

This endpoint will be used to get a list of Returns linked to a Project. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/returns**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/returns`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
vendor | Limits results to a single vendor. | {organization's vendor number}
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

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
`GET`

This endpoint will be used to get a list of Back-Orders linked to a project. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/back-orders**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/back-orders`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
vendor | Limits results to a single vendor. | {organization's vendor number}
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Project Lead-Times
### API Endpoint - Get a List of Lead-Times for a Project

> The above code returns JSON structured like this:

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "fe30ea8b-78bf-5dc4-962b-1fb034061b08",
		"lead_time": 5,
		"date_need_by": "2019-09-27",
		"date_order_by": "2019-09-22",
		"quantity": 1,
		"org_item_id": null,
		"vendor_item_id": null,
		"mfr_part_number": null,
		"hph_code": "505VC2080",
		"upc": null,
		"description": "10\" EPDM GASKET",
		"mfr_name": "Victaulic Company",
		"delivery_location_type": "JOB SITE",
		"delivery_location_name": null,
		"vendor_number": null,
		"vendor_name": null,
		"work_order_id": null,
		"work_order_name": null,
		"spool_id": null,
		"spool_name": null,
		"project_number": "PRJ-2019-04",
		"project_name": "Snow-making Pump House",
		"requisition_number": null,
		"requisition_name": null,
		"po_number": null,
		"po_name": null
	}]
}
```
`GET`

This endpoint will be used to get a list of items with a lead-time. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/lead-times**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/lead-times`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml