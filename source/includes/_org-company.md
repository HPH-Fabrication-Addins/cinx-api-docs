# Org/Company


## Org Definition
### CINX Object Defintion - Organization

An Organization in CINX defines a company or grouping of individuals (residential customers) that participate or is referenced on the platform.

**Dependencies and Business Rules**

  - Must be created by a CINX user

**Supported API Services**

  - Get an Org's Details
  - Get an Org Template
  - Get an Org's List of Users
  - Get an Org's List of Locations/Addresses
  - Get an Org's List of Customer Types
  - Get an Org's List of Vendor Types
  - Get an Org's List of Project Types
  - Get an Org's List of Invoice Dispute Reasons
  - Get an Org's List of Return Reasons
  - Get an Org's List of Return Actions

The above list is intended to represent the API endpoints related to an Org and it core entities and references. There are many other org-related endpoint types documented on this site.  For example, an Org's Vendors, Projects, and Transactions.

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


This endpoint will be used to get company’s CINX organization details.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org`

HTTP Method: `GET`

## Get Org Template
### API Endpoint - Get an Organization Template

This endpoint will be used to get a CINX Template for an organization.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/org**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/org`

HTTP Method: `GET`

## Org Users
### API Enpoint – Get an Organization's List of Users

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

This endpoint will be used to get a company’s list of CINX users. The response of this API call will contain the user’s CINX System Id which can be used in other API calls.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/users**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/users`

HTTP Method: `GET`

## Org Locations/Addresses
### API Enpoint – Get an Organization's List of Locations/Addresses

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

This endpoint will be used to get a company’s list of location types and their addresses. This list will be used when creating material transactions that require delivery to a specific location.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/addresses**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/addresses`

HTTP Method: `GET`

## Modify Org
### API Enpoint – Modify an Organization's Details

This request will be used to modify an organization’s details.

URL Pattern:**{api path}/{api_version}/sub/{api_token}/modify/org**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/xxx`

HTTP Method: `PUT`

 
## Get Customer Types
### API Enpoint – Get an Organization’s List of Customer Types

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

This endpoint will be used to get a company’s list of thier Customer Types. In CINX, each company can define how it  would like to classify its customers. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/types/customers**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/types/customers`

HTTP Method: `GET`

## Get Vendor Types
### API Enpoint – Get an Organization’s List of Vendor Types

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

This endpoint will be used to get a company’s list of thier Vendor Types. In CINX, each company can define how it  would like to classify its vendors. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/types/vendors**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/types/vendors`

HTTP Method: `GET`

## Get Project Types
### API Enpoint – Get an Organization’s List of Project Types

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

This endpoint will be used to get a company’s list of thier Project Types. In CINX, each company can define how it  would like to classify its projects. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/types/projects**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/types/projects`

HTTP Method: `GET`

## Get Dispute Reasons
### API Enpoint – Get an Organization’s List of Invoice Dispute Reasons

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

This endpoint will be used to get a company’s list of thier Invoice Dispute Types. In CINX, each company can define the list of the reasons it can dispute an invoice. Dispute reasons can be at the transaction level and on individual items. The company can define a code and name for the dispute reasons. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/invoices/dispute-reasons**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/invoices/dispute-reasons`

HTTP Method: `GET`

## Get Return Reasons
### API Enpoint – Get an Organization’s List of Return Reasons

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

This endpoint will be used to get a company’s list of thier Return Reasons. In CINX, each company can define the list of the reasons it will return materials. The company can define a code and name for each reason. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/returns/reasons**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/returns/reasons`

HTTP Method: `GET`

## Get Return Actions
### API Enpoint – Get an Organization’s List of Return Actions

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

This endpoint will be used to get a company’s list of thier Return Actions. In CINX, each company can define the list of the actions it would like the vendor to use when processing the return. The company can define a code and name for each action. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org-refs/returns/actions**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-refs/returns/actions`

HTTP Method: `GET`
