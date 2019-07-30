# Requisitions

## Req Definition
### Requisition Object Definition

A CINX Material Requisition is a compilation of parts that need to be purchased.  The list might be for a whole project, phase, system, pre-fab work-order, spool, or a general list created by a project foreman in the field. Requisitions are created to request the materials.  The parts on a requisition might also contain items from multiple projects that are combined into one purchase to achieve volume pricing.

It is important to understand that the parts on a requisition may be divided onto different purchase orders which might be sent to different vendors.

Dependencies and Business Rules

* Must be created by a CINX user linked to an active CINX company.
* Must have a unique number
* Must have a procurement status
* Must be assigned to a valid CINX user

Supported API Services

* Get a list of requisitions
* Get a requisition
* Get a requisition’s related POs
* Get a requisition’s related RFQs
* Modify a requisition
* Get a requisition template
* Get a requisition number
* Create a requisition

## Get Req List
### Get a List of Requisitions

This request will be used to get a list of requisitions.

URL Pattern:
**{api path}/{api_version}sub/{api_token}/reqs**

URL Sample:
`https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/reqs`

HTTP Method:
`GET`

## Get Req
### Get a Requisition

This request will be used to get the details of a specific requisition.  Note: This response will include the requisition’s items.

URL Pattern:
**{api path}/{api_version}sub/{api_token}/req/{cinx_guid}**

The cinx_guid will be the Requisition’s CINX GUID.

URL Sample:
`https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/req/e73c118f-1ee9-57e0-9c79-1775c1a04b81`

HTTP Method:
`GET`

## Req Template
### Get a Requisition Template

This request will be used to get a CINX Template for a requisition.

URL Pattern:
**{api path}/{api_version}sub/{api_token}/template/req**

URL Sample:
`https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/req`

HTTP Method:
`GET`

## New Req Number
### Get a New Requisition Number

This request will be used to get a value to be used in the number field of a new requisition.

Note: The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern:
**{api path}/{api_version}sub/{api_token}/reqs/next-number**

URL Sample:
`https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/reqs/next-number`

HTTP Method:
`GET`

## Create Req
### Create a New Requisition

This API call will be used to create a new requisition.

Notes: 

* A CINX Template is available that documents the available fields that can be populated.
* A JSON formatted payload is used in the POST request

URL Pattern:
**{api path}/{api_version}sub/{api_token}/req/partner/exec/cinx/json-req-import?body=json**

URL Sample:
`https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-req-import?body=json`

HTTP Method:
`POST`

## Modify Req
### Modify a Requisition

This API call will be used to modify an existing CINX requisition.

Notes: 

* A CINX Template is available that documents the available fields that can be populated.
* A JSON formatted payload is used in the PUT request

URL Pattern:
**{api path}/{api_version}sub/{api_token}/req/partner/exec/cinx/json-req-import?body=json**

URL Sample:
`https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-req-import?body=json`

HTTP Method:
`PUT`
