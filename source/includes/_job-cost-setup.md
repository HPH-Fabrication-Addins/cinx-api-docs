# Job Cost Setup	

## Introduction
### CINX Job Cost Introduction

To allow for the proper reporting of Project items and integration of transactions with contractor accounting systems, CINX has the ability for a company to define their job costing attributes. CINX supports the following Job Cost information types:

**PHASES**
A Phase is construction management concept that allows a company to break-down a project into a smaller group of tasks commonly used for scheduling, sequencing, and reporting purposes.  A Phase is also referred to as a Sub-Job, Area, or Extra by other software systems.  Examples Phases include, Site Work, Floor, and System.

**COST CODES**
A Cost Code is an accounting and construction management concept that allows a company to track material and labor for cost reporting purposes.  Other systems refer to Cost Codes as Item Groups.  Example Cost Codes are Sanitary Sewer, Domestic Water, and Gas.

**CATEGORIES**
A Category is an accounting that allows a company to classify project costs for expensing purposes.  Categories are also known as Cost Classes.  For example, Material, Labor, Sub-Contractor, and Rental.

**TAX GROUPS**
A Tax Group is a collection of tax fields defined in an accounting system that allows for the proper identification and processing of taxes.  

## Get Phases
### API – GET a List of the Job Cost Phases

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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "org_job_cost->getList",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-job-cost/get-list/phases",
        "format": "json",
        "start_time": 1564154910.323,
        "total_time": 0.45502400398254,
        "record_count": 6,
        "total_count": 6
    },
    "rows": [
        {
            "name": "1",
            "description": "Phase 1",
            "material_cost_code": {
                "guid": "df8f4e93-3d04-5379-948a-0b3f5319cbd2",
                "name": "CC1",
                "description": "Cost Code1"
            },
            "guid": "8e441211-45ca-5c84-b34b-a93cd4cdf853",
            "date_modified": "2017-10-20 19:10:27Z",
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
        },
        {
            "name": "First Floor",
            "description": "First Floor",
            "material_cost_code": {
                "guid": "df8f4e93-3d04-5379-948a-0b3f5319cbd2",
                "name": "CC1",
                "description": "Cost Code1"
            },
            "guid": "3b61f993-69b5-5db3-a367-2d204321c857",
            "date_modified": "2019-06-04 15:12:19Z",
            "status": "A",
            "reference_id": null,
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
        },
        {
            "name": "Phase 2.0",
            "description": "Modified 2.0",
            "status": "A",
            "guid": "8d4800f1-bbc3-5600-b627-350c89caba09",
            "date_modified": "2019-07-24 16:02:52Z",
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
        },
        {
            "name": "Phase2",
            "description": "UG pHase",
            "material_cost_code": {
                "guid": "5d9b83d0-a3de-5475-959d-04b92fd4de75",
                "name": "UG-123",
                "description": "Underground"
            },
            "guid": "ea6fba0f-0b8e-5e49-a110-6bcb36182146",
            "date_modified": "2017-10-20 19:10:36Z",
            "status": "A",
            "reference_id": null,
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
        },
        {
            "name": "T1",
            "description": "T1 D",
            "status": "A",
            "guid": "cce49d02-a6f5-5331-9fc4-7e1ea25d24c0",
            "date_modified": "2019-07-24 19:25:17Z",
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
        },
        {
            "name": "Test",
            "description": "Test Description",
            "status": "A",
            "guid": "78ae2003-98c1-5a9c-ae56-e14d4f2c7c14",
            "date_modified": "2019-07-24 18:48:01Z",
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

This URL will be used to get the list of Phases in the company’s CINX Job Costing library.  

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/get-list/phases

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/get-list/phases`

## Create Phase
### API – Create a Job Cost Phase 

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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "org_job_cost->modify",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-job-cost/modify/phases",
        "format": "json",
        "start_time": 1564155485.442,
        "total_time": 0.43365502357483,
        "record_count": 1,
        "total_count": 0
    },
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

The JSON **values** section of this URL will begin with **“phases”**: and then will be followed by an array structure comprised of the following components:

**Name**
“name”:”value”

**Description**
“description”:”value”

**Reference Id** (Can be used to store the accounting system’s internal Id for the Phase)
“reference_id”:”value”

**User Id**
“user_id”:”value”

**Date Modified**
“date_modified”:”date/time value”

**Status**
“status”:”value”
Available options are: **A, D** 
Option Definitions: **A=Active, D=Discontinued**

**Material Cost Code** (Can be used to define a default Cost Code for the Phase)
“material_cost_code”:”value”

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/modify/phases?values={%22phases%22:[{%22name%22:%2202-8157%22,%22description%22:%22Site%20Work%22,%22reference_id%22:%22%22,%22user_id%22:%22%22,%22date_modified%22:%22%22,%22status%22:%22A%22,%22material_cost_code%22:%225241%22}]}`

## Modify Phase
### API – Modify a Job Cost Phase 

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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "org_job_cost->modify",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-job-cost/modify/phases",
        "format": "json",
        "start_time": 1564155648.618,
        "total_time": 0.44458794593811,
        "record_count": 1,
        "total_count": 0
    },
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

NOTE: This URL pattern is the same as the Create Phase except that the GUID of the Phase to be modified must be included in the JSON array.

The JSON **values** section of this URL will begin with **“phases”:** and then will be followed by an array structure comprised of the following components:

**GUID**
“guid”:”value”

**Name**
“name”:”value”

**Description**
“description”:”value”

**Reference Id** (Can be used to store the accounting system’s internal Id for the Phase)
“reference_id”:”value”

**User Id**
“user_id”:”value”

**Date Modified**
“date_modified”:”date/time value”

**Status**
“status”:”value”
Available options are: **A, D** 
Option Definitions: **A=Active, D=Discontinued**

**Material Cost Code** (Can be used to define a default Cost Code for the Phase)
“material_cost_code”:”value”


Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/modify/phases?user=dc3aecca-f2ec-ee6e-eee9-6d96d45390fa&values={"phases":[{"guid":"6ebcc266-83b4-85cf-53f9-8db2d52f15cb","name":"02-8158","description":"Site Work","reference_id":"","user_id":"","date_modified":"","status":"A","material_cost_code":"5241"}]}`

## Get Cost Codes
### API – GET a List of the Job Cost Cost Codes

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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "org_job_cost->getList",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-job-cost/get-list/material-cost-codes",
        "format": "json",
        "start_time": 1564155707.648,
        "total_time": 0.45248103141785,
        "record_count": 5,
        "total_count": 5
    },
    "rows": [
        {
            "name": "101-1025",
            "description": "Domestic Water",
            "expense_category": {
                "guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
                "name": "MAT",
                "description": "Material"
            },
            "guid": "314f6a13-56b3-5c3f-b14e-10d159e4c5c0",
            "date_modified": "2019-06-04 15:12:59Z",
            "status": "A",
            "reference_id": null,
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
        },
        {
            "name": "22-235",
            "description": "Plumbing",
            "expense_category": {
                "guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
                "name": "MAT",
                "description": "Material"
            },
            "guid": "bece7ec3-16db-50c0-bdf9-36bb8de8cb88",
            "date_modified": "2019-06-05 21:28:13Z",
            "status": "A",
            "reference_id": null,
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
        },
        {
            "name": "CC1",
            "description": "Cost Code1",
            "expense_category": {
                "guid": "b7c8125e-6048-5085-a02c-8dd645012eda",
                "name": "Expense 13",
                "description": "Exp13"
            },
            "guid": "df8f4e93-3d04-5379-948a-0b3f5319cbd2",
            "date_modified": "2017-10-20 19:09:47Z",
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
                "type": "ORG-MATERIAL-COST-CODES",
                "domain": "org-0001-4030",
                "id": "71f73b3a-9e60-59bb-b498-bbfc34cb14dc"
            }
        },
        {
            "name": "New CC",
            "description": "Mod 2.0",
            "status": "A",
            "guid": "4038f906-cc66-5c11-8909-a59f2ab6267f",
            "date_modified": "2019-07-24 16:05:42Z",
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
        },
        {
            "name": "UG-123",
            "description": "Underground",
            "expense_category": {
                "guid": "a5f91c07-7c5b-5b0c-863b-16b2f6d960c6",
                "name": "Expense 12",
                "description": "expense cat12"
            },
            "guid": "5d9b83d0-a3de-5475-959d-04b92fd4de75",
            "date_modified": "2017-10-20 19:10:07Z",
            "status": "A",
            "reference_id": null,
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

This URL will be used to get the list of Cost Codes in the company’s CINX Job Costing library.   

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/get-list/material-cost-codes

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/get-list/material-cost-codes`

## Create Cost Code
### API – Create a Job Cost Cost Code

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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "org_job_cost->modify",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-job-cost/modify/material-cost-codes",
        "format": "json",
        "start_time": 1564155872.571,
        "total_time": 0.45745301246643,
        "record_count": 1,
        "total_count": 0
    },
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

NOTE: Please use underscores on material_cost_code when it is within the JSON structure.  This is different than the earlier part of the URL where hyphens are used.

The JSON values section of this URL will begin with “material_cost_codes”: and then will be followed by an array structure comprised of the following components:

Name
“name”:”value”

Description
“description”:”value”

Reference Id (Can be used to store the accounting system’s internal Id for the Phase)
“reference_id”:”value”

User Id
“user_id”:”value”

Date Modified
“date_modified”:”date/time value”

Status
“status”:”value”
Available options are: A, D 
Option Definitions: A=Active, D=Discontinued

Expense Category (Can be used to define a default Category for the Cost Code)
“expense_category”:”value”

## Modify Cost Code
### API – Modify a Job Cost Cost Code

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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "org_job_cost->modify",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org-job-cost/modify/material-cost-codes",
        "format": "json",
        "start_time": 1564156036.046,
        "total_time": 0.43114399909973,
        "record_count": 1,
        "total_count": 0
    },
    "rows": [
        {
            "name": "101-1025",
            "description": "W",
            "expense_category": {
                "guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
                "name": "MAT",
                "description": "Material"
            },
            "guid": "314f6a13-56b3-5c3f-b14e-10d159e4c5c0",
            "date_modified": "2019-07-26 15:47:16Z",
            "status": "A",
            "reference_id": null,
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

This URL will be used to modify an existing Cost Code in the company’s CINX Job Costing library.

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/material-cost-codes? values={“ material_cost_codes”:[{JSON Structure}]}

NOTE: This URL pattern is the same as the Create Cost Code except that the GUID of the Cost Code to be modified must be included in the JSON array.

NOTE: Please use underscores on material_cost_code when it is within the JSON structure.  This is different than the earlier part of the URL where hyphens are used.

The JSON values section of this URL will begin with “material_cost_codes”: and then will be followed by an array structure comprised of the following components:

GUID
“guid”:”value”

Name
“name”:”value”

Description
“description”:”value”

Reference Id (Can be used to store the accounting system’s internal Id for the Phase)
“reference_id”:”value”

User Id
“user_id”:”value”

Date Modified
“date_modified”:”date/time value”

Status
“status”:”value”
Available options are: A, D 
Option Definitions: A=Active, D=Discontinued

Expense Category (Can be used to define a default Category for the Cost Code)
“expense_category”:”value”

## Get Categories
### API – GET a List of the Job Cost Categories

This URL will be used to get the list of Categories in the company’s CINX Job Costing library.   

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/get-list/tax-expense-categories

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/get-list/tax-expense-categories`

## Create Category
### API – Create a Job Cost Category

This URL will be used to create a new Category in the company’s CINX Job Costing library.   

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/tax-expense-categories? values={“material_cost_code”:[{JSON Structure}]}

NOTE: Please use underscores on **material_cost_code** when it is within the JSON structure.  This is different than the earlier part of the URL where hyphens are used.

The JSON **values** section of this URL will begin with **“material_cost_code”:** and then will be followed by an array structure comprised of the following components:

**Name**
“name”:”value”

**Description**
“description”:”value”

**Reference Id** (Can be used to store the accounting system’s internal Id for the Phase)
“reference_id”:”value”

**User Id**
“user_id”:”value”

**Date Modified**
“date_modified”:”date/time value”

**Status**
“status”:”value”
Available options are: **A, D** 
Option Definitions: **A=Active, D=Discontinued**

## Modify Category
### API – Modify a Job Cost Category

This URL will be used to modify an existing Category in the company’s CINX Job Costing library.   

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/tax-expense-categories? values={“ tax_expense_categories”:[{JSON Structure}]}

NOTE: This URL pattern is the same as the Create Category except that the GUID of the Category to be modified must be included in the JSON array.

NOTE: Please use underscores on tax_expense_categories when it is within the JSON structure.  This is different than the earlier part of the URL where hyphens are used.

The JSON values section of this URL will begin with “tax_expense_categories”: and then will be followed by an array structure comprised of the following components:

GUID
“guid”:”value”

Name
“name”:”value”

Description
“description”:”value”

Reference Id (Can be used to store the accounting system’s internal Id for the Phase)
“reference_id”:”value”

User Id
“user_id”:”value”

Date Modified
“date_modified”:”date/time value”

Status
“status”:”value”
Available options are: A, D 
Option Definitions: A=Active, D=Discontinued



## Get Tax Groups
### API – GET a List of the Job Cost Tax Groups

This URL will be used to get the list of Tax Groups in the company’s CINX Job Costing library.  

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/get-list/tax-groups

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/get-list/tax-groups`

## Create Tax Group
### API – Create a Job Cost Tax Group

This URL will be used to create a new Tax Group in the company’s CINX Job Costing library. 

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/tax-groups? values={“ tax_groups”:[{JSON Structure}]}

NOTE: Please use underscores on tax_groups when it is within the JSON structure.  This is different than the earlier part of the URL where hyphens are used.

The JSON **values** section of this URL will begin with **“tax_groups”:** and then will be followed by an array structure comprised of the following components:

**Name**
“name”:”value”

**Tax Type**
“tax_type”:”value”
Available options are: SALES, USE, or {user defined}

**Description**
“description”:”value”

**Reference Id** (Can be used to store the accounting system’s internal Id for the Phase)
“reference_id”:”value”

**User Id**
“user_id”:”value”

**Date Modified**
“date_modified”:”date/time value”

**Status**
“status”:”value”
Available options are: **A, D** 
Option Definitions: **A=Active, D=Discontinued**

Rate
“rate”:”value”

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/modify/tax-groups?values={"tax_groups":[{"name":"MD1","tax_type":"Sales","description":"Maryland Sales Tax","reference_id":"T1254","user_id":"","date_modified":"","status":"A","rate":"5.65"}}}`


## Modify Tax Group
### API – Modify a Job Cost Tax Group

This URL will be used to modify an existing Tax Group in the company’s CINX Job Costing library.  

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/tax-groups? values={“ tax_groups”:[{JSON Structure}]}

NOTE: This URL pattern is the same as the Create Tax Group except that the GUID of the Tax Group to be modified must be included in the JSON array.

NOTE: Please use underscores on **tax_groups** when it is within the JSON structure.  This is different than the earlier part of the URL where hyphens are used.

The JSON **values** section of this URL will begin with **“tax_groups”:** and then will be followed by an array structure comprised of the following components:

**GUID**
“guid”:”value”

**Name**
“name”:”value”

**Tax Type**
“tax_type”:”value”
Available options are: SALES, USE, or {user defined}

**Description**
“description”:”value”

**Reference Id** (Can be used to store the accounting system’s internal Id for the Phase)
“reference_id”:”value”

**User Id**
“user_id”:”value”

**Date Modified**
“date_modified”:”date/time value”

**Status**
“status”:”value”
Available options are: **A, D** 
Option Definitions: **A=Active, D=Discontinued**

**Rate**
“rate”:”value”


Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/modify/tax-groups?values={"tax_groups":[{"guid":"dba9161a-4d78-9cff-fa37-6a7c344837b2","name":"MD1","tax_type":"Sales","description":"Maryland Sales Tax","reference_id":"T1254","user_id":"","date_modified":"","status":"A","rate":"5.65"}]}`

 
 
