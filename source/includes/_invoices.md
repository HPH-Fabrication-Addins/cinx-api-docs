# Invoices

## Invoice Definition
### CINX Object Defintion - Invoices

An Invoice is a vendor document is that indicates the quantities and costs of the products or services provider by the vendor. The invoice document will also define payment terms and dates.

**Supported API Services**
- Get a List of Invoices
- Get an Invoice
- Get an Invoice Template
- Create an Invoice
- Modify an Invoice

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
This endpoint will be used to get a list of invoices. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/invoices**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/invoices`

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


## Get Invoice
### API Endpoint - Get an Invoice

This request will be used to get the details of a specific invoice.  Note: This response will include the invoice’s items.

URL Pattern: **{api path}/{api_version}sub/{api_token}/invoice/{cinx_guid}**

The cinx_guid will be the invoice’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/invoice/8ead0386-496b-571c-b14f-09eafeeb6758`

HTTP Method: `GET`

## Get Invoice Template
### API Endpoint - Get an Invoice Template

This request will be used to get a CINX Template for an invoice.

URL Pattern: **{api path}/{api_version}sub/{api_token}/template/invoice**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/invoice`

HTTP Method: `GET`

## Invoice Template Fields
### Definition of the Invoice Template's Fields

The table below defines the fields within the template.

## Create Invoice
### API Endpoint - Create a New Invoice

This endpoint will be used to create a new invoice.

**Notes**

- A CINX Template is available that documents the available fields that can be populated.
- A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-invoice-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-invoice-import?body=json`

HTTP Method: `POST`

## Modify Invoice
### API Endpoint - Modify an Invoice

This API call will be used to modify an existing CINX invoice.

**Notes**

- A CINX Template is available that documents the available fields that can be populated.
- A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-invoice-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-invoice-import?body=json`

HTTP Method: `PUT`
