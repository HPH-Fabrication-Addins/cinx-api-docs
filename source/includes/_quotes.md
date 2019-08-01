# Quotes

## Quote Definition
### CINX Object Defintion - Quote

A CINX Quote is a document a vendor prepares in response to a customer’s Request for Quotation.  Quotes will contain the net prices a customer will pay if they place an order.

**Supported API Services**
- Get a List of Quotes
- Get a Quote


## Get Quote List
### API Endpoint - Get a List of Quotes

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"cinx_guid": "e98e2fc5-f59b-5091-8b05-54edaa9284cc",
			UPDATE CONTENT
		}
    ]
}
```
This endpoint will be used to get a list of quotes. See the Supported Filters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}sub/{api_token}/quotes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/quotes`

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


## Get Quote
### API Endpoint - Get a Quote

This request will be used to get the details of a specific quote.  Note: This response will include the quote’s items.

URL Pattern: **{api path}/{api_version}sub/{api_token}/quote/{cinx_guid}**

The cinx_guid will be the quote’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/quote/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

HTTP Method: `GET`