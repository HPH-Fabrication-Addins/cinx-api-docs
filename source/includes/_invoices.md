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
`GET`

This endpoint will be used to get a list of invoices. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/invoices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/invoices`


## Get Invoice
### API Endpoint - Get an Invoice

`GET`

This request will be used to get the details of a specific invoice.  Note: This response will include the invoice’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/invoice/{cinx_guid}**

The cinx_guid will be the invoice’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/invoice/8ead0386-496b-571c-b14f-09eafeeb6758`

## Get Invoice Template
### API Endpoint - Get an Invoice Template

`GET`

This request will be used to get a CINX Template for an invoice.

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

This API call will be used to modify an existing CINX invoice.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-invoice-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-invoice-import?body=json`

<aside class="notice">
The PUT payload will be processed asynchronously.
</aside>
