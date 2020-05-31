# Org/Company

## Org Definition
### CINX Object Definition - Organization

An Organization in CINX defines a company or grouping of individuals (residential customers) that participate or is referenced on the platform.

**Dependencies and Business Rules**

  - Must be created by a CINX user

**Supported API Services**

  - [Get an Org's Details](#get-org-details)
  - [Get an Org's List of Users](#org-users)
  - [Get an Org's List of Locations/Addresses](#org-locations-addresses)
  - [Get an Org's List of Customer Types](#get-customer-types)
  - [Get an Org's List of Vendor Types](#get-vendor-types)
  - [Get an Org's List of Project Types](#get-project-types)
  - [Get an Org's List of Invoice Dispute Reasons](#get-dispute-reasons)
  - [Get an Org's List of Return Reasons](#get-return-reasons)
  - [Get an Org's List of Return Actions](#get-return-actions)

The above list is intended to represent the API endpoints related to an Org and it core entities and references. There are many other org-related endpoint types documented on this site.  For example, an [Org's Vendors](#vendors), [Projects](#projects), and Transactions.

## Get Org Details
### API Endpoint - Get an Organization's Details

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "is_hidden": "0",
            "is_private": "0",
            "role_primary": "CONTRACTOR",
        }  
    ]
}
```
`GET`

This endpoint will be used to get company’s CINX organization details.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml 

## Org Users
### API Enpoint – Get an Organization's List of Users

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getOrgUsers(cinx_api_token)
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
            "id": "4a23ff84-9d61-5ab3-95c9-3870cb2727bd",
            "name": "Karl Stone",
            "last_first": "Stone, Karl",
            "email": "karlstone@cinx.com"
        },
        {
            "id": "185aabe1-3487-5f59-9ad5-c577a76bd392",
            "name": "Will Stone",
            "last_first": "Stone, Will",
            "email": "willstone@cinx.com"
        }
    ]
}
```
 `GET`

This endpoint will be used to get a company’s list of CINX users. The response of this API call will contain the CINX Id for each user.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/users**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/users`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Org Locations/Addresses
### API Endpoint – Get an Organization's List of Locations/Addresses

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getOrgAddresses(cinx_api_token)
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
            "guid": "4e1877b6-b485-5be6-9544-80bd2749d5e2",
            "type": "SHIPPING",
            "desc": "Littleton Fab Shop",
            "address1": "995 Industrial Park Road",
            "address2": "Building 2",
            "address3": "Suite 3",
            "country": "USA",
            "city": "Littleton",
            "state": "NH",
            "postal_code": "03561",
            "latitude": "",
            "longitude": ""
        }
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of location types and their addresses. This list will be used when creating material transactions that require delivery to a specific location.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/addresses**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/addresses`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml
 
## Get Customer Types
### API Endpoint – Get an Organization’s List of Customer Types

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        "Industrial",
        "Commercial",
        "Medical",
        "Residential",
        "Hospitality"
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of their Customer Types. In CINX, each company can define how it  would like to classify its customers.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/types/customers**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/types/customers`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Vendor Types
### API Endpoint – Get an Organization’s List of Vendor Types

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        "PVF",
        "Fixtures",
        "Hardware",
        "Office Supplies",
        "Equipment"
    ]
}
```
 `GET`

This endpoint will be used to get a company’s list of their Vendor Types. In CINX, each company can define how it  would like to classify its vendors. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/types/vendors**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/types/vendors`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Project Types
### API Endpoint – Get an Organization’s List of Project Types

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        "New Construction",
        "Tenant Fit-Up",
        "Service"
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of their Project Types. In CINX, each company can define how it  would like to classify its projects. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/types/projects**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/types/projects`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Dispute Reasons
### API Endpoint – Get an Organization’s List of Invoice Dispute Reasons

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "guid": "a9d3277e-6417-5458-98a6-08de16fa7c1b",
            "code": "01-item",
            "name": "Item Level Issue"
        },
        {
            "guid": "75ebe888-4649-50f5-9ccb-08ee82f801c6",
            "code": "02-badterm",
            "name": "Incorrect Terms"
        }
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of their Invoice Dispute Types. In CINX, each company can define the list of reasons it can use to identify a dispute on an invoice. Dispute reasons can be at the transaction level and also on individual items. The company can define a code and name for the dispute reasons. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/invoices/dispute-reasons**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/invoices/dispute-reasons`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Return Reasons
### API Endpoint – Get an Organization’s List of Return Reasons

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "guid": "36502c12-9e1b-56c8-a788-323c51b17a1f",
            "code": "21-damage",
            "name": "Damaged"
        },
        {
            "guid": "57d44251-1b29-5882-bedb-ac59fdc6b90a",
            "code": "22-item",
            "name": "Wrong Product"
        }
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of their Return Reasons. In CINX, each company can define the list of the reasons it will return materials. The company can define a code and name for each reason. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/returns/reasons**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/returns/reasons`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Return Actions
### API Endpoint – Get an Organization’s List of Return Actions

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "guid": "f51cc612-1f47-5f74-b47a-088e2f47d207",
            "code": "41-replace",
            "name": "Replace Item"
        },
        {
            "guid": "31e27fdd-c231-5521-8536-1cb22493db74",
            "code": "42-credit",
            "name": "Credit Account"
        }
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of their Return Actions. In CINX, each company can define the list of the actions it would like the vendor to use when processing the return. The company can define a code and name for each action. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/returns/actions**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/returns/actions`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml
