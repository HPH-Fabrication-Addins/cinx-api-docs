# Invoices

## Invoice Definition
### CINX Object Defintion - Invoices

An Invoice is a vendor document is that indicates the quantities and costs of the products or services provider by the vendor. The invoice document will also define payment terms and dates.

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must be linked to a CINX purchase order
  - Must have at least one item before it can be submitted

**Supported API Services**

  - [Get a List of Invoices](#get-invoice-list)
  - [Get an Invoice](#get-invoice)
  - [Get an Invoice Template](#get-invoice-template)
  - [Create an Invoice](#create-invoice)
  - [Modify an Invoice](#modify-invoice)

## Get Invoice List
### API Endpoint - Get a List of Invoices

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
		"item_count": 15
	}]
}
```
`GET`

This endpoint will be used to get a list of invoices. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/invoices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/invoices`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
po-guid | Limits results to a specific purchase order. | {cinx_po_id}
status | Limits results to a specific status. | PENDING E-INVOICE, ENTERED, REVIEWED, ACCEPTED, IN-DISPUTE, ON-HOLD, REJECTED, SUBMITTED
erp | Limits results to a specific erp status. | NOT SUBMITTED, PENDING, SUBMITTED, APPLIED
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
owner | Limits results to a specified CINX user to whom the transaction is assigned | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}

## Get Invoice
### API Endpoint - Get an Invoice

`GET`

This endpoint will be used to get the details of a specific invoice.  Note: This response will include the invoice’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/invoice/{cinx_guid}**

The cinx_guid will be the invoice’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/invoice/8ead0386-496b-571c-b14f-09eafeeb6758`

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "8ead0386-496b-571c-b14f-09eafeeb6758",
		"locked": "0",
		"number": "I456123",
		"name": "I456123",
		"workflow_status": "PENDING E-INVOICE",
		"entry_type": "MANUAL",
		"accepted_type": "MANUAL",
		"erp_status": "NOT SUBMITTED",
		"counts": {
			"credits": 0,
			"charges": 0,
			"items": 1
		},
		"entered_by": {
			"cinx_guid": null,
			"name": null,
			"email": null
		},
		"accepted_by": {
			"cinx_guid": null,
			"name": null,
			"email": null
		},
		"assigned_to": {
			"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
			"name": "Will Stone",
			"email": "willstone@cinx.com"
		},
		"dates": {
			"created": "2019-06-07",
			"last_modified": "2019-06-07",
			"issued": "2019-06-08",
			"received": "2019-06-09",
			"payment_due": "2019-06-21",
			"discount_due": "2019-06-10",
			"entered": "",
			"accepted": ""
		},
		"vendor": {
			"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
			"number": "V101",
			"name": "Hilti",
			"file_url": null
		},
		"customer": {
			"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
			"number": "C101",
			"name": "WTS Mechanical"
		},
		"purchase_order": {
			"cinx_guid": "80e6d9c8-d2e4-5aaa-9bd3-3957430741dd",
			"number": "PO123",
			"name": "PO123"
		},
		"project": {
			"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
			"number": "WTS-2017-03",
			"name": "HPH HQ Renovation"
		},
		"payment_terms": {
			"discount_percent": 1.5,
			"discount_days_type": null,
			"discount_days": 10,
			"due_days": null,
			"late_fee_percent": null
		},
		"bill_to": {
			"address1": null,
			"address2": null,
			"address3": null,
			"city": null,
			"state": null,
			"postal_code": null,
			"location_name": null,
			"attention": null
		},
		"remit_to": {
			"address1": null,
			"address2": null,
			"address3": null,
			"city": null,
			"state": null,
			"postal_code": null,
			"location_name": null,
			"attention": null
		},
		"credits": [],
		"charges": [],
		"items": [{
				"cinx_guid": "73d55d4b-4436-5539-aad2-7f2a11666146",
				"sequence": 1,
				"quantity": 1,
				"unit_price": 270.05,
				"price_uom": "E",
				"currency": "USD",
				"invoice_status": "PENDING",
				"allow_substitutes": true,
				"hph_code": "326ZU6542",
				"org_item_id": null,
				"org_system_id": null,
				"mfr_part_number": null,
				"upc": "67024006745",
				"size": "4",
				"description": null,
				"mfr_name": null,
				"item_type": "MATERIAL",
				"vendor": {
					"cinx_commerce_guid": "7880c854-017f-5359-96de-fdef626c33cf",
					"number": "V101",
					"name": "Hilti",
					"item_id": null,
					"system_id": null
				},
				"purchase_order": {
					"cinx_guid": "80e6d9c8-d2e4-5aaa-9bd3-3957430741dd",
					"number": "PO-123",
					"name": "PO123",
					"quantity": 1,
					"quantity_received": 1,
					"unit_price": 270.05,
					"price_uom": "E",
					"currency": "USD"
				},
				"project": {
					"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
					"number": "WTS-2017-03",
					"name": "WTS-2017-03"
				},
				"job_cost": {
					"cinx_phase_guid": null,
					"phase_name": "124",
					"cinx_material_cost_code_guid": null,
					"material_cost_code_name": null,
					"cinx_category_guid": null,
					"category_name": null
				},
				"taxes": {
					"taxable": true,
					"cinx_guid": null,
					"tax_group_name": null,
					"tax_type": null,
					"tax_rate": 0,
					"tax_amount": 0
				}
			}
		]
	}]
}
```

## Get Invoice Template
### API Endpoint - Get an Invoice Template

`GET`

This endpoint will be used to get a CINX Template for an invoice.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/invoice**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/invoice`


The table below defines the input fields within the template.

## Create Invoice
### API Endpoint - Create a New Invoice

`POST`

This endpoint will be used to create a new invoice.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-invoice-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-invoice-import?body=json`

<aside class="notice">
The POST payload will be processed asynchronously.
</aside>

## Modify Invoice
### API Endpoint - Modify an Invoice

`PUT`

This API endpoint will be used to modify an existing CINX invoice.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-invoice-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-invoice-import?body=json`

<aside class="notice">
The PUT payload will be processed asynchronously.
</aside>
