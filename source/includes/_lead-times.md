# Lead-Times

## Lead-Time Definition
### CINX Object Defintion - Lead-Time

CINX supports the definition of a lead-time for an item that has been added to a project or purchasing transaction.  A lead time defines the amount of time, expressed in days, that it will take for the vendor to deliver the finished product after it is ordered. CINX also supports the definition of two date fields (need by and order by) that will help manage the timely ordering of materials.  

**Dependencies and Business Rules**

  - The item must be linked to a CINX project or purchasing transaction
  - CINX Lead-Times are expressed in days

**Supported API Services**

  - [Get a List of Lead-Times]()
  - [Get a Lead Time]()


## Get Lead-Times List
### API Endpoint - Get a List of Lead-Times

> The above code returns JSON structured like this:

```json
{
	"response": {},
	"rows": [{
		
		Update Content
	}]
}
```
`GET`

This endpoint will be used to get a list of items with a lead-time. See the Optional URL Parameters list for additional query parameters that can be used in the URL.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/lead-times**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/lead-times`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
delivery | Limits results to a specific delivery type location. | JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR
project | Limits results to a single project. | {cinx_project_id}
vendor | Limits results to a single vendor. | {organization's vendor number}

## Get Lead-Time
### API Endpoint - Get a Lead-Time

`GET`

This endpoint will be used to get the details of an item with a lead-time.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/lead-time/{lead_time_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/lead_time/076bd4bb-d6d9-5096-96f2-ec105d0562b1`

```json
{
	"response": {},
	"rows": [{
		
		Update Content
	}]
}
```
