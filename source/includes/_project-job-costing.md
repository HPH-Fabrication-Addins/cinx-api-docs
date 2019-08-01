# Project Job Costing

## Job Cost Intro
### CINX Project Job Costing Introduction

To allow for the proper reporting of Project items and integration of transactions with contractor accounting systems, CINX has the ability for a company to define their job costing attributes or each Project. 

CINX supports the following Job Cost information at the project level:

**PHASES***
A Phase is construction management concept that allows a company to break-down a project into a smaller group of tasks commonly used for scheduling, sequencing, and reporting purposes.  A Phase is also referred to as a Sub-Job, Area, or Extra by other software systems.  Examples Phases include, Site Work, Floor, and System.

**MATERIAL COST CODES***
A Cost Code is an accounting and construction management concept that allows a company to track materials for cost reporting purposes.  Other systems refer to Cost Codes as Item Groups.  Example Cost Codes are Sanitary Sewer, Domestic Water, and Gas.

**CATEGORIES***
A Category is an accounting concept that allows a company to classify project costs for expensing purposes.  Categories are also known as Cost Classes.  For example, Material, Labor, Sub-Contractor, and Rental.

**ESTIMATED VALUES**
CINX supports the entry of estimated values for a project’s phase/cost code for the following data types:  Material Costs, Labor Units, and Labor Costs.

**BUDGET VALUES**
CINX supports the entry of budget values for a project’s phase/cost code for the following data types:  Material Costs, Labor Units, and Labor Costs.

**ACTUAL VALUES**
CINX supports the entry of actual values for a project’s phase/cost code for the following data types:  Material Costs, Labor Units, and Labor Costs.

**DATES**
CINX supports the entry of the following key date types related to the project’s phase/cost code:  Scheduled Start, Actual Start, Scheduled Completion, and Actual Completion.

**CONSTRUCTION STATUS**
The following statuses can be used to track a project’s phase/cost code: Not Installed, In-Process, Installed, Tested, Commissioned, and Operational.

**PERCENT COMPLETE**
Each CINX project phase/cost code has a field to track the percent complete.

* Phases, Cost Codes, and Categories must be established in the company’s CINX account before they can be attached to a project.  Please see these documentation sections for information about creating job cost information in CINX:

## Get Project Job Costing
### API Endpoint - Get a Project’s Job Costing List

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

cinxApi.getProjectCosts(cinx_api_token, project_id)
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
            "cinx_guid": "676a95fb-3903-5e01-9f0d-2a31a426a76e",
            "construction_status": "NOT INSTALLED",
            "percent_complete": null,
            "project": {
                "cinx_guid": "3b61f993-69b5-5db3-a367-2d204321c857",
                "name": "HQ  Oct 23",
                "description": "test",
                "number": "WTS-2017-01"
            },
            "phase": {
                "cinx_guid": "8e441211-45ca-5c84-b34b-a93cd4cdf853",
                "name": "1",
                "description": "A",
                "status": "A"
            },
            "material_cost_code": {
                "cinx_guid": "df8f4e93-3d04-5379-948a-0b3f5319cbd2",
                "name": "CC1",
                "description": "Cost Code1",
                "status": "A"
            },
            "category": {
                "cinx_guid": "b7c8125e-6048-5085-a02c-8dd645012eda",
                "name": "Expense 13",
                "description": "Exp13",
                "status": "A"
            },
            "material_cost": {
                "estimated": null,
                "budgeted": null,
                "actual": null
            },
            "labor_units": {
                "estimated": null,
                "budgeted": null,
                "actual": null
            },
            "labor_cost": {
                "estimated": null,
                "budgeted": null,
                "actual": null
            },
            "dates": {
                "start_scheduled": "2017-10-23 17:00:12Z",
                "start_actual": "2017-10-23 17:00:12Z",
                "completion_scheduled": "2017-10-23 17:00:12Z",
                "completion_actual": "2017-10-23 17:00:12Z"
            }
        }
    ]
}
```

This endpoint will be used to get a list of a project’s job costing information – phases and cost codes.  The response will contain full details for each phase/cost code.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}/job-costing**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/e1e3cb54-b00a-55ae-a079-072732542bf4/job-costing`

HTTP Method: `GET`

## Create Project Job Costing
### API Endpoint - Create a Project’s Phase and Cost Code List

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"material_cost_code":"${pName}","percent_complete":"${pDescription}","phase":"${pNumber}"}`;

cinxApi.putProjectCost(cinx_api_token, project_id, values)
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
           UPDATE PICTURE
        }
    ]
}
```

This endpoint will be used to create a project’s job costing attributes.

**Notes**

- A CINX Template is available that documents the available fields that can be populated.
- A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-xxxx-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-xxxx-import?body=json`

HTTP Method: `POST`

## Modify Project Job Costing
### API Endpoint - Modify a Project’s Phase and Cost Code

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"material_cost_code":"${pName}","percent_complete":"${pDescription}","phase":"${pNumber}"}`;

cinxApi.modifyProjectCost(cinx_api_token, project_cost_id, values)
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
           UPDATE PICTURE
        }
    ]
}
```

This endpoint will be used to modify a project’s phase and cost code attributes.

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-xxxx-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-xxxx-import?body=json`

HTTP Method: `PUT`
