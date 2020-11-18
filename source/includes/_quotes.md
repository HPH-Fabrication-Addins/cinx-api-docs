# Quotes

## Quote Definition
### CINX Object Definition - Quote

A CINX Quote is a document a vendor prepares in response to a customer’s Request for Quotation.  Quotes will contain the net prices a customer will pay if they place an order.

**Supported API Services**

  - [Get a List of Quotes](#get-quote-list)
  - [Get a Quote](#get-quote)


## Get Quote List
### API Endpoint - Get a List of Quotes

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

This endpoint will be used to get a list of quotes. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/quotes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/quotes`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
workflow | Limits results to a specific workflow status. | IN-PROCESS, SUBMITTED, RECEIVED, ERP PENDING, ERP ACCEPTED, ERP FAILED
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}
ship-via | Limits results to a specific ship via value. | SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE
need-by | Limits results to a specific need-by or delivery-by date. | Date Format: YYYY-MM-DD
submitter | Limits results to a specified CINX user. | {cinx_user_id}
number | Limits results to a specified transaction number. | {transaction_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 50 will be used. | Integer

## Get Quote
### API Endpoint - Get a Quote

`GET`

This endpoint will be used to get the details of a specific quote.  Note: This response will include the quote’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/quote/{cinx_guid}**

The cinx_guid will be the quote’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/quote/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

```json
{
	"response": {},
	"rows": [{
		"cinx_guid": "1eb08930-8744-5213-90f0-3ad63a216b20",
		"locked": "0",
		"number": "Q101254",
		"name": "Q101254",
		"description": "",
		"terms": "1.5/15",
		"user_comment": "",
		"workflow_status": "RECEIVED",
		"vendor": {
			"cinx_commerce_guid": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f",
			"number": "99999",
			"name": "Keegan Supply"
		},
		"customer": {
			"cinx_commerce_guid": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f",
			"number": "ABCD1234",
			"name": "WTS Mechanical",
			"rfq_number": "RFQ-8745",
			"rfq_name": "RFQ-8745",
			"requested_by_name": "Will Stone",
			"project_number": "WTS-2019-06",
			"project_name": "Martha's Restaurant Upgrade",
			"phase_name": null,
			"material_cost_code_name": null,
			"category_name": null,
			"taxable": true,
			"tax_group_name": null
		},
		"counts": {
			"credits": 0,
			"charges": 0,
			"items": 11
		},
		"submitter": {
			"cinx_guid": "0317a60e-2a5a-50a2-8674-39e8f54ad49b",
			"name": "eb stone",
			"email": "estone@cinx.com"
		},
		"dates": {
			"created": "2019-07-25",
			"last_modified": "2019-07-25",
			"expiration": "2019-07-26",
			"rfq_respond_by": null,
			"submitted": null,
			"need_by": null
		},
		"delivery": {
			"address1": "995 Industrial Park Rd",
			"address2": "",
			"address3": "",
			"city": "Littleton",
			"state": "NH",
			"postal_code": "03561",
			"country": "USA",
			"ship_via": null,
			"fob_type": null,
			"ship_from": null,
			"attention": null,
			"location_type": "JOB SITE",
			"location_name": null,
			"instructions": null
		},
		"external_references": [],
		"charges": [],
		"credits": [],
		"items": [{
				"cinx_guid": "61e3150a-ec0e-50dc-a358-89af1819c601",
				"sequence": 1,
				"quantity": 1,
				"base_price": 6.667,
				"multiplier_value": 1,
				"unit_price": 6.667,
				"price_uom": "E",
				"currency": "USD",
				"multiplier_code": null,
				"availability_type": null,
				"availability_location": null,
				"order_lead_time": null,
				"date_need_by": null,
				"allow_substitutes": false,
				"substituted": false,
				"hph_code": null,
				"org_item_id": null,
				"org_system_id": null,
				"mfr_part_number": null,
				"upc": null,
				"size": "4\"",
				"description": "4\" DC CI LVL-TROL ABS PLUG ADJ FLOOR CO",
				"mfr_name": "Zurn Industries/Drains",
				"item_type": "MATERIAL",
				"customer": {
					"item_id": null,
					"item_system_id": null,
					"project_number": "WTS-2019-06",
					"phase_name": null,
					"material_cost_code_name": null,
					"category_name": null,
					"taxable": true,
					"tax_group_name": null,
					"ship_via": null,
					"location_type": null,
					"instructions": null,
					"labeling_instructions": "wo-101",
					"packaging_instructions": "crate",
					"work_order_name": null,
					"spool_name": null,
					"building": null,
					"level": null,
					"space": null,
					"sub_space": null,
					"system": null,
					"arch_symbol": null,
					"tag": null,
				"attributes": []
				}
			}
		]
	}]
}
```

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml