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
			"cinx_guid": "e98e2fc5-f59b-5091-8b05-54edaa9284cc",
			UPDATE CONTENT
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of quotes. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/quotes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/quotes`


**OPTIONAL URL PARAMETERS**


## Get Quote
### API Endpoint - Get a Quote

`GET`

This request will be used to get the details of a specific quote.  Note: This response will include the quote’s items.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/quote/{cinx_guid}**

The cinx_guid will be the quote’s CINX Id.

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/quote/e73c118f-1ee9-57e0-9c79-1775c1a04b81`
