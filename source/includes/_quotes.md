# Quotes

## Quote Definition
### CINX Object Defintion - Quote

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
    "rows": [
        {
			"cinx_guid": "1eb08930-8744-5213-90f0-3ad63a216b20",
			"number": "",
			"name": "WTS Mechanical -DEV[ 2019 07 25 a ]",
			"description": "",
			"workflow_status": "RECEIVED",
			"vendor_number": "99999",
			"vendor_name": "Ferguson Testing July 2015",
			"submitted_by": "eb stone",
			"date_received": "2019-07-25",
			"date_expires": "2019-07-26",
			"date_requested": null,
			"links": [],
			"project_number": "WTS-2019-06",
			"project_name": "2019 01 30",
			"rfq_number": "2019 07 25 a",
			"rfq_name": "2019 07 25 a",
			"item_count": 11
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of quotes. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/quotes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/quotes`


**OPTIONAL URL PARAMETERS**

**delivery**: will limit results to a specific delivery type location

  - Available options are: JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR

**workflow**: will limit results to a specific workflow status

  - Available options are: IN-PROCESS, SUBMITTED, RECEIVED, ERP PENDING, ERP ACCEPTED, ERP FAILED

**project**: will limit results to a single project

  - {cinx_project_guid}

**vendor**: will limit results to a single vendor

  - {organization's vendor number}

**ship_via**: will limit results to a specific ship via value

  - Available options are: SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE

**deliver_date**: will limit results to a specific need-by or delivery-by date

  - Date Format: YYYY-MM-DD

**submitter**: will limit results to a specified CINX user

  - {CINX_User_Id}

**number**: will limit results to a specified transaction number

  - {transaction_number}

## Get Quote
### API Endpoint - Get a Quote

`GET`

This endpoint will be used to get the details of a specific quote.  Note: This response will include the quote’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/quote/{cinx_guid}**

The cinx_guid will be the quote’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/quote/e73c118f-1ee9-57e0-9c79-1775c1a04b81`
