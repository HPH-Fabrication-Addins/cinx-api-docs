# Deliveries

## Delivery Definition
### CINX Object Definition - Delivery

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

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getDeliveries(cinx_api_token)
    .then(function(response) {
        console.log(response);
    });
```

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

This endpoint will be used to get a list of deliveries. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/deliveries**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/deliveries`

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

## Get Delivery
### API Endpoint - Get a Delivery

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getDelivery(cinx_api_token, delivery_guid)
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "69e5c268-1c7b-54bf-acd9-601f4f59a52b",
		"locked": "1",
		"number": "D19-4512",
		"name": "D19-4512",
		"description": null,
		"date_received": "2019-06-27",
		"ship_via": "SUPPLIER TRUCK",
		"location_type": "JOB SITE",
		"location_name": null,
		"packing_slip_number": null,
		"tracking_id": null,
		"total_weight": null,
		"condition": null,
		"was_insured": "0",
		"driver": null,
		"truck": null,
		"fob_type": null,
		"fob_point": null,
		"user_comment": null,
		"workflow_status": "COMPLETE",
		"item_count": 3,
		"receiver": {
			"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
			"name": "Will Stone",
			"email": "willstone@cinx.com"
		},
		"purchase_order": {
			"cinx_guid": "5c88bd83-7675-54b0-8c11-61644cf470d6",
			"number": "P19-789412",
			"name": "P19-789412",
			"date_need_by": ""
		},
		"vendor": {
			"cinx_commerce_guid": "de0cf849-6f7b-5df6-9ae9-f924659f2d25",
			"number": "CXV101",
			"name": "National Sales Company"
		},
		"project": {
			"cinx_guid": "bb613aff-4256-5359-b7cd-391505d19e01",
			"number": "WTS-2017-03",
			"name": "WTS-2017-03"
		},
		"external_references": [],
		"items": [{
				"cinx_guid": "4361e462-7406-5989-84f6-9e2e7b2c5521",
				"sequence": 1,
				"quantity_ordered": 3,
				"quantity_accepted": 3,
				"quantity_refused": 0,
				"date_received": "2019-06-27",
				"allow_substitutes": true,
				"hph_code": "326ZU6541",
				"org_item_id": null,
				"org_system_id": null,
				"mfr_part_number": null,
				"upc": "67024006731",
				"size": "3",
				"description": null,
				"mfr_name": null,
				"workflow_status": "COMPLETE",
				"photo_url": null,
				"delivery": {
					"ship_via": "SUPPLIER TRUCK",
					"location_type": "JOB SITE",
					"location_name": null
				},
				"billable_weight": {
					"weight": 0,
					"uom": null
				},
				"hazmat": {
					"is_hazmat": false,
					"hazmat_code": null
				},
				"receiver": {
					"cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
					"name": "Will Stone",
					"email": "willstone@cinx.com"
				},
				"vendor": {
					"cinx_commerce_guid": "de0cf849-6f7b-5df6-9ae9-f924659f2d25",
					"number": "CXV101",
					"name": "National Sales Company",
					"item_id": null,
					"system_id": null
				},
				"work_breakdown": {
					"work_order_id": null,
					"work_order_name": null,
					"spool_id": null,
					"spool_name": null,
					"building_name": null,
					"level": "MAIN",
					"space": null,
					"sub_space": null,
					"system": "SAN W&V UG",
					"arch_symbol": null,
					"tag": null
				},
				"job_cost": {
					"cinx_phase_guid": null,
					"phase_name": "124",
					"cinx_material_cost_code_guid": null,
					"material_cost_code": null,
					"cinx_category_guid": null,
					"category_name": null
				},
				"design": {
					"model_item_guid": null,
					"model_name": null,
					"model_file": null,
					"drawing_number": "P1.0",
					"drawing_name": null
				},
				"attributes": []
			}
		]
	}]
}
```

`GET`

This endpoint will be used to get the details of a specific delivery. Note: This response will include the delivery’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/delivery/{cinx_guid}**

The cinx_guid will be the delivery's CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/delivery/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Delivery Template
### API Endpoint - Get a Delivery Template

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getDeliveryTemplate(cinx_api_token)
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

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
			"location_type": "JOB SITE",
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
				"quantity_accepted": 0,
				"quantity_refused": 0,
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
				},
				"attributes": [
					{
						"name": null,
						"value": null
					}]
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

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

The table below defines the input fields within the template.

**TEMPLATE FIELDS**

Name | Data Type | Required | Default | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; PUT = Yes |  | CINX System Id.
number | String | Yes |  | Public number for the object.
name | String | Yes |  | Public name for the object.
description | String | No |  | Public description for the object.
date_received | Date (YYYY-MM-DD) | No |  | Date the delivery was processed.
cinx_receiver_guid | String (GUID Format) | No |  | CINX Id for the user who processed the delivery.
ship_via | String | No |  | How the products were delivered or otherwise acquired. Template has a list of optional values.
delivery_location_type | String | Yes | JOB SITE | Type of location where the delivery was received. Template has a list of optional values.
delivery_location_name | String | No |  | Name of the location where the materials were delivered.
packing_slip_number | String | No |  | Id number from the shipment's packing slip.
tracking_id | String | No |  | Identification number of the package. For example, a tracking number issued by a delivery service.
total_weight | String | No |  | Total weight of the full shipment.
condition | String | No |  | User description of quality of the shipment packaging and handling.
was_insured | Boolean | Yes | FALSE | Indicator if the shipment was insured.
driver | String | No |  | Name of the driver who delivered the shipment.
truck | String | No |  | Id of the truck that delivered the shipment.
fob_type | String | No |  | F.O.B. Type. Template has a list of optional values.
fob_point | String | No |  | F.O.B. Point.
user_comment | String | No |  | General comment defined by a CINX user.
purchase_order.cinx_guid | String (GUID Format) | No |  | CINX Id of the Purchase Order against which the delivery was made. Field is not modifiable.
purchase_order.number | String | No |  | Public number for the Purchase Order. Field is not modifiable.
vendor.cinx_commerce_guid | String (GUID Format) | No |  | CINX Commerce Id for the vendor. Field is not modifiable.
vendor.number | String | No |  | The public number of the vendor from whom the products were sourced. Field is not modifiable.
project.cinx_guid | String (GUID Format) | No |  | CINX Project Id. Field is not modifiable.
project.number | String | No |  | The public number of the project from which the items are being requested. Field is not modifiable.
items.cinx_po_item_guid | String (GUID Format) | Yes |  | CINX System Id for the item on the purchase order.
items.quantity_accepted | Real | Yes | 0 | Quantity of the item that was accepted during the delivery receiving.
items.quantity_refused | Real | Yes | 0 | Quantity of the item that was refused during the delivery receiving.
items.date_received | Date (YYYY-MM-DD) | No |  | Date the delivery of the product was processed.
items.cinx_receiver_guid | String (GUID Format) | No |  | CINX Id for the user who received the product.
items.photo_url | String | No |  | Link to a photo of the item being received.
items.delivery.ship_via | String | No |  | How the product was delivered or otherwise acquired. Template has a list of optional values.
items.delivery.location_type | String | Yes | JOB SITE | Location type where the product was delivered. Template has a list of optional values.
items.delivery.location_name | String | No |  | Name of the location where the product was delivered.
items.billable_weight.weight | String | No |  | Weight of the product that could be subject to a delivery charge.
items.billable_weight.uom | String | No |  | Unit-of-measure of the product's billable weight.
items.hazmat.is_hazmat | Boolean | Yes | FALSE | Indicator if the delivered product is labeled as a Hazardous Material.
items.hazmat.hazmat_code | String | No |  | Hazardous Material code assigned to the product.
items.attributes.name | String | No |  | Name of the attribute.
items.attributes.value | String | No |  | Value of the attribute.

## Get Delivery Number
### API Endpoint - Get a New Delivery Number

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getDeliveryNumber(cinx_api_token)
    .then(function(response) {
        console.log(response);
    });
```

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

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Create Delivery
### API Endpoint - Create a New Delivery

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

var isSynchronous = true;
//dObject can be created based on the template retrieved from cinxApi.getDeliveryTemplate(cinx_api_token) call
cinxApi.postDelivery(cinx_api_token, dObject, isSynchronous)
            .then(function (response) {
            console.log(response);
            }); 
```

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
           
        }
    ]
}
```

`POST`

This endpoint will be used to create a new delivery.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-delivery-import?body=json**

URL Samples: 

  - Asynchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-delivery-import?body=json`
  - Synchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-delivery-import?body=json&synchronous=1`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json
synchronous | Switch to have the payload processed synchronously. | 1

<aside class="notice">
By default the POST payload will be processed asynchronously.  See the optional URL parameters table for a synchronous option.
</aside>

## Modify Delivery
### API Endpoint - Modify a Delivery

`PUT`

This API endpoint will be used to modify an existing CINX delivery.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-delivery-import?body=json**

URL Samples: 

  - Asynchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-delivery-import?body=json`
  - Synchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-delivery-import?body=json&synchronous=1`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json
synchronous | Switch to have the payload processed synchronously. | 1

<aside class="notice">
By default the PUT payload will be processed asynchronously.  See the optional URL parameters table for a synchronous option.
</aside>