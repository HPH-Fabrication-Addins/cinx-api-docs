# Deliveries

## Delivery Definition
### CINX Object Defintion - Delivery

A CINX Delivery is created when a shipment from a vendor is received. A Delivery references a purchase order on which the materials were ordered.  

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - Must have a unique number
  - Must be linked to a CINX purchase order
  - Must have at least one item before it can be submitted

**Supported API Services**

  - Get a List of Deliveries
  - Get a Delivery
  - Get a Delivery Template
  - Get a Delivery Number
  - Create a Delivery
  - Modify a Delivery

## Get Deliveries List
### API Endpoint - Get a List of Deliveries

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
This endpoint will be used to get a list of deliveries. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/deliveries**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/deliveries`

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


## Get Delivery
### API Endpoint - Get a Delivery

This request will be used to get the details of a specific delivery. Note: This response will include the delivery’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/delivery/{cinx_guid}**

The cinx_guid will be the delivery's CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/delivery/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

HTTP Method: `GET`

## Get Delivery Template
### API Endpoint - Get a Delivery Template

```json
{
	"response": {},
	"rows": [{
		"doc_info": {},
		"template": {
			"cinx_guid": null,
			"number": null,
			"name": null,
			"description": null,
			"date_received": null,
			"cinx_receiver_guid": null,
			"location_type": null,
			"location_name": null,
			"packing_slip_number": null,
			"total_weight": null,
			"condition": null,
			"was_insured": false,
			"fob_type": null,
			"fob_point": null,
			"user_comment": null,
			"workflow_status": "INCOMPLETE",
			"delivery": {
				"ship_via": null,
				"package_id": null,
				"driver": null,
				"truck": null
			},
			"purchase_order": {
				"cinx_guid": null,
				"number": null
			},
			"vendor": {
				"cinx_commerce_guid": null,
				"number": null
			},
			"project": {
				"cinx_guid": null,
				"number": null
			},
			"items": [{
				"cinx_po_item_guid": null,
				"quantity_accepted": null,
				"quantity_refused": null,
				"date_received": null,
				"cinx_receiver_guid": null,
				"workflow_status": "INCOMPLETE",
				"photo_url": null,
				"delivery": {
					"ship_via": null,
					"location_type": null,
					"location_name": null
				},
				"billable_weight": {
					"weight": null,
					"uom": null
				},
				"hazmat": {
					"is_hazmat": false,
					"hazmat_code": null
				}
			}]
		},
		"field_options": {},
		"api_calls": []
}
```

This request will be used to get a CINX Template for a delivery.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/delivery**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/delivery`

HTTP Method: `GET`


The table below defines the input fields within the template.

## Get Delivery Number
### API Endpoint - Get a New Delivery Number

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"delivery": "D-000001"
		}
    ]
}
```
This endpoint will be used to get a value to be used in the number field of a new delivery.

**Notes**

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/delivery**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/delivery`

HTTP Method: `GET`

## Create Delivery
### API Endpoint - Create a New Delivery

This endpoint will be used to create a new delivery.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-delivery-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-delivery-import?body=json`

HTTP Method: `POST`

Processing Type: `Asynchronous`

## Modify Delivery
### API Endpoint - Modify a Delivery

This API call will be used to modify an existing CINX delivery.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-delivery-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-delivery-import?body=json`

HTTP Method: `PUT`

Processing Type: `Asynchronous`