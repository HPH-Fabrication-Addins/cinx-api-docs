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

  - [Get a List of Deliveries](#get-deliveries-list)
  - [Get a Delivery](#get-delivery)
  - [Get a Delivery Template](#get-delivery-template)
  - [Get a Delivery Number](#get-delivery-number)
  - [Create a Delivery](#create-delivery)
  - [Modify a Delivery](#modify-delivery)

## Get Delivery List
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
			"workflow_status": "INCOMPLETE",
			"vendor_number": "H125",
			"vendor_name": "Hilti-6",
			"ship_via": "SUPPLIER TRUCK",
			"location_type": "FABRICATION SHOP",
			"location_name": null,
			"date_received": "2019-06-07",
			"received_by": "Will Stone",
			"total_weight": "456",
			"packing_slip_number": "54654645",
			"links": [],
			"project_number": "WTS-2017-03",
			"project_name": "WTS-2017-03",
			"po_number": "PO-123",
			"po_name": "PO123",
			"date_need_by": "2019-06-11",
			"item_count": 15
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of deliveries. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/deliveries**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/deliveries`


**OPTIONAL URL PARAMETERS**

**project**: will limit results to a single project

  - {cinx_project_guid}

**vendor**: will limit results to a single vendor

  - {organization's vendor number}

**delivery**: will limit results to a specific delivery type location

  - Available options are: JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE

**ship_via**: will limit results to a specific ship via value

  - Available options are: SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE

**po_guid**: will limit results to a specified CINX purchase order

  - {CINX_PO_Id}

**submitter**: will limit results to a specified CINX user who received the order (received_by)

  - {CINX_User_Id}

**number**: will limit results to a specified transaction number

  - {transaction_number}
  
## Get Delivery
### API Endpoint - Get a Delivery

`GET`

This endpoint will be used to get the details of a specific delivery. Note: This response will include the delivery’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/delivery/{cinx_guid}**

The cinx_guid will be the delivery's CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/delivery/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

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
			"ship_via": null,
			"location_type": null,
			"location_name": null,
			"packing_slip_number": null,
			"tracking_id": null,
			"total_weight": null,
			"condition": null,
			"was_insured": false,
			"driver": null,
			"truck": null,
			"fob_type": null,
			"fob_point": null,
			"user_comment": null,
			"workflow_status": "INCOMPLETE",
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
`GET`

This endpoint will be used to get a CINX Template for a delivery.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/delivery**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/delivery`


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
`GET`

This endpoint will be used to get a value to be used in the number field of a new delivery.

**Notes**

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/delivery**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/delivery`
 

## Create Delivery
### API Endpoint - Create a New Delivery

`POST`

This endpoint will be used to create a new delivery.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-delivery-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-delivery-import?body=json`

<aside class="notice">
The POST payload will be processed asynchronously.
</aside>

## Modify Delivery
### API Endpoint - Modify a Delivery

`PUT`

This API endpoint will be used to modify an existing CINX delivery.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-delivery-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-delivery-import?body=json`

<aside class="notice">
The PUT payload will be processed asynchronously.
</aside>