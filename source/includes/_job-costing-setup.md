# Job Costing Setup	

## Job Costing Intro
### CINX Job Costing Introduction

To allow for the proper reporting of project items and integration of transactions with contractor accounting systems, CINX has the ability for a company to define its job costing attributes. CINX supports the following job cost information types:

**PHASES**

A Phase is construction management concept that allows a company to break-down a project into a smaller group of tasks commonly used for scheduling, sequencing, and reporting purposes. A Phase is also referred to as a Sub-Job, Area, or Extra by other software systems.  Example phases include, Site Work, First Floor, and System.

**COST CODES**

A Cost Code is an accounting and construction management concept that allows a company to track material and labor for cost reporting purposes.  Other systems refer to cost codes as Item Groups. Example cost codes are 200-Sanitary Sewer, 400-Domestic Water, and 600-Gas.

**CATEGORIES**

A Category is an accounting concept that allows a company to classify project costs for expensing purposes.  Categories are also known as Cost Classes.  For example, Material, Labor, Sub-Contractor, and Rental.

**TAX GROUPS**

A Tax Group is a collection of tax fields defined in an accounting system that allows for the proper identification and processing of taxes.  

## Get Phases
### API Endpoint - Get an Organizaiton's List of Phases

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

cinxApi.getJobCostPhases(cinx_api_token)
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
            "cinx_guid": "3b61f993-69b5-5db3-a367-2d204321c857",
            "name": "First Floor",
            "description": "First Floor",
            "material_cost_code_guid": "df8f4e93-3d04-5379-948a-0b3f5319cbd2",
            "modified_by": "Will Stone",
            "date_modified": "2019-06-04",
            "status": "A"
        }
    ]
}
```

This endpoint will be used to get a company’s list of project phases. In CINX, each company can define the list of standard phases that they use on projects. The company can define a name and description for each phase as well as a default material cost code. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org/job-costing/phases**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/job-costing/phases`

HTTP Method: `GET`

## Create Phase
### API Endpoint - Create a Job Cost Phase 

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"phases":[{"name":"${name}","description":"${description}","status":"${status}"}]}`;

cinxApi.putJobCostPhase(cinx_api_token, values)
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
            "name": "A",
            "description": "A",
            "status": "A",
            "guid": "ac004964-39f3-5487-8e4f-41d567e083ce",
            "date_modified": "2019-07-26 15:38:05Z",
            "reference_id": null,
            "material_cost_code": "",
            "is_default": 0,
            "modifier": {
                "name": "Will Stone",
                "cinx_id": {
                    "type": "USER",
                    "domain": "users",
                    "id": "185aabe1-3487-5f59-9ad5-c577a76bd392"
                }
            },
            "cinx_id": {
                "type": "ORG-PHASES",
                "domain": "org-0001-4030",
                "id": "d596b228-1b0a-5658-806c-0b5bd2f426ed"
            }
        }
    ]
}
```

This URL will be used to create a new Phase in the company’s CINX Job Costing library.   

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/phases?values={“phases”:[{JSON Structure}]}


## Modify Phase
### API Endpoint - Modify a Job Cost Phase 

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"phases":[{"name":"${name}","description":"${description}","status":"${status}"}]}`;

cinxApi.putJobCostPhase(cinx_api_token, values)
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
            "name": "1",
            "description": "A",
            "material_cost_code": {
                "guid": "df8f4e93-3d04-5379-948a-0b3f5319cbd2",
                "name": "CC1",
                "description": "Cost Code1"
            },
            "guid": "8e441211-45ca-5c84-b34b-a93cd4cdf853",
            "date_modified": "2019-07-26 15:40:49Z",
            "status": "A",
            "reference_id": null,
            "is_default": 1,
            "modifier": {
                "name": "Will Stone",
                "cinx_id": {
                    "type": "USER",
                    "domain": "users",
                    "id": "185aabe1-3487-5f59-9ad5-c577a76bd392"
                }
            },
            "cinx_id": {
                "type": "ORG-PHASES",
                "domain": "org-0001-4030",
                "id": "d596b228-1b0a-5658-806c-0b5bd2f426ed"
            }
        }
    ]
}
```

This URL will be used to modify an existing Phase in the company’s CINX Job Costing library. 

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/phases?values={“phases”:[{JSON Structure}]}


## Get Cost Codes
### API Endpoint - Get an Organization's List of Material Cost Codes

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

cinxApi.getJobCostCostCodes(cinx_api_token)
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
            "cinx_guid": "314f6a13-56b3-5c3f-b14e-10d159e4c5c0",
            "name": "101-1025",
            "description": "Pipe Hangers",
            "category_guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
            "modified_by": "Will Stone",
            "date_modified": "2019-07-26",
            "status": "A"
        }
    ]
}
```

This endpoint will be used to get a company’s list of material cost codes. In CINX, each company can define the list of cost codes that can be assigned to materials in a project. The company can define a name and description for each phase as well as a default category. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org/job-costing/material-cost-codes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/job-costing/material-cost-codes`

HTTP Method: `GET`

## Create Cost Code
### API Endpoint - Create a Job Cost Cost Code

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"material_cost_codes":[{"name":"${name}","description":"${description}","status":"${status}"}]}`;

cinxApi.putJobCostCostCode(cinx_api_token, values)
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
            "name": "A",
            "description": "A",
            "status": "A",
            "guid": "937ddba6-f62c-55a9-83fa-323b8daedfbe",
            "date_modified": "2019-07-26 15:44:33Z",
            "reference_id": null,
            "expense_category": "",
            "is_default": 0,
            "modifier": {
                "name": "Will Stone",
                "cinx_id": {
                    "type": "USER",
                    "domain": "users",
                    "id": "185aabe1-3487-5f59-9ad5-c577a76bd392"
                }
            },
            "cinx_id": {
                "type": "ORG-MATERIAL-COST-CODES",
                "domain": "org-0001-4030",
                "id": "71f73b3a-9e60-59bb-b498-bbfc34cb14dc"
            }
        }
    ]
}
```

This URL will be used to create a new Cost Code in the company’s CINX Job Costing library.

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/material-cost-codes? values={“ material_cost_codes”:[{JSON Structure}]}


## Modify Cost Code
### API Endpoint - Modify a Job Cost Cost Code

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"material_cost_codes":[{"name":"${name}","description":"${description}","status":"${status}"}]}`;

cinxApi.putJobCostCostCode(cinx_api_token, values)
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
    "response": { },
    "rows": [
        {
            "name": "101-1025",
            "description": "W",
            "expense_category": {
                "guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
                "name": "MAT",
                "description": "Material"
            }
        }
    ]
}
```

This URL will be used to modify an existing Cost Code in the company’s CINX Job Costing library.

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/material-cost-codes? values={“ material_cost_codes”:[{JSON Structure}]}


## Get Categories
### API Endpoint - Get an Organization's List of Categories

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "cinx_guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
            "name": "MAT",
            "description": "Material",
            "modified_by": "Will Stone",
            "date_modified": "2019-06-04",
            "status": "A"
        }
    ]
}
```

This endpoint will be used to get a company’s list of accounting categories. In CINX, each company can define the list of standard categories. The company can define a name and description. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org/job-costing/categories**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/job-costing/categories`

HTTP Method: `GET`

## Create Category
### API Endpoint - Create a Job Cost Category

This URL will be used to create a new Category in the company’s CINX Job Costing library.   

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/tax-expense-categories? values={“material_cost_code”:[{JSON Structure}]}

## Modify Category
### API Endpoint - Modify a Job Cost Category

This URL will be used to modify an existing Category in the company’s CINX Job Costing library.   

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/tax-expense-categories? values={“ tax_expense_categories”:[{JSON Structure}]}


## Get Tax Groups
### API Endpoint - Get an Organization's List of Tax Groups

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "cinx_guid": "7c42f24f-766e-5220-bc7e-cce8048dbb57",
            "name": "TAX-12",
            "description": "state Tax",
            "modified_by": "Will Stone",
            "date_modified": "2017-10-20",
            "status": "A"
        }
    ]
}
```

This endpoint will be used to get a company’s list of tax groups. In CINX, each company can define the list of standard tax groups. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org/job-costing/tax-groups**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/job-costing/tax-groups`

HTTP Method: `GET`

## Create Tax Group
### API Endpoint - Create a Job Cost Tax Group

This URL will be used to create a new Tax Group in the company’s CINX Job Costing library. 

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/tax-groups? values={“ tax_groups”:[{JSON Structure}]}



## Modify Tax Group
### API Endpoint - Modify a Job Cost Tax Group

This URL will be used to modify an existing Tax Group in the company’s CINX Job Costing library.  

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/tax-groups? values={“ tax_groups”:[{JSON Structure}]}
