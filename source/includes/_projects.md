# Projects

## Project Definition
### CINX Object Defintion - Project

A CINX project is a **job** that is being performed for a customer/client on building, structure, or other asset.

**Dependencies and Business Rules**
- Must be created by a CINX user linked to an active CINX company.
- A customer and its building can be associated with a project

**Supported API Services**
- Get a List of Projects
- Get a Project
- Get a Project Template
- Get a Project Number
- Create a Project
- Modify a Project
- Get Project Transactions
- Get Project Job Costing
- Get Project Submittals

## Get Project List
### API Endpoint - Get List of Projects

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

cinxApi.getProjects(cinx_api_token)
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
            "cinx_guid": "e8c5dc6b-e95a-5009-ad89-a11520f55493",
            "number": "A",
            "name": "A",
            "description": "A",
            "project_manager": "Will Stone",
            "status": "CONCEPTUAL",
            "customer": {
                "cinx_commerce_guid": null,
                "customer_name": null,
                "cinx_building_guid": null,
                "building_number": null,
                "building_name": null,
                "project_number": null
            },
            "item_count": 7
        }
    ]
}
```

This endpoint will be used to get a list of the organization's projects. 

URL Pattern: **{api path}/{api_version}sub/{api_token}/projects**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/projects`

HTTP Method: `GET`

## Get Project
### API Endpoint - Get a Project

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

cinxApi.getProjectDetails(cinx_api_token, project_id)
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
            "cinx_guid": "e8c5dc6b-e95a-5009-ad89-a11520f55493",
            "number": "A",
            "name": "A",
            "description": "A",
            "status": "CONCEPTUAL",
            "dates": {
                "contract_award": null,
                "scheduled_start": null,
                "actual_start": null,
                "scheduled_complete": null,
                "actual_complete": null
            },
            "customer": {
                "cinx_commerce_guid": null,
                "customer_name": null,
                "cinx_building_guid": null,
                "building_name": null,
                "project_number": null
            },
            "classifications": {
                "delivery_method": "NOT SPECIFIED",
                "is_leed": "0",
                "org_defined_type": null,
                "construction_type": "NOT SPECIFIED",
                "industry_type": "NOT SPECIFIED",
                "cinx_type": "PROJECT",
                "sector_type": "NOT SPECIFIED"
            },
            "contract": {
                "budget_amount": null,
                "budget_currency": "USD"
            },
            "taxes": {
                "taxable": true,
                "cinx_guid": "7c42f24f-766e-5220-bc7e-cce8048dbb57",
                "tax_group_name": "TAX-12",
                "tax_exempt_id": null
            },
            "size_square": {
                "value": null,
                "uom": "FEET"
            }
        }
    ]
}
```

This endpoint will be used to get the details of a specific project.

URL Pattern: **{api path}/{api_version}sub/{api_token}/project/{project_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/e8c5dc6b-e95a-5009-ad89-a11520f55493`

HTTP Method: `GET`

## Get Project Template
### API Endpoint - Get a Project Template

This endpoint will be used to get a CINX Template for a project.

URL Pattern: **{api path}/{api_version}sub/{api_token}/template/project**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/project`

HTTP Method: `GET`

## Project Template Fields
### Definition of the Project Template's Fields

The table below defines the fields within the template.

## Get Project Number
### API Endpoint - Get a New Project Number

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "project": "PRJ-2019-01"
        }
    ]
}
```
This request will be used to get a value to be used in the number field of a new project.

**Notes** 
- The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.


URL Pattern: **{api path}/{api_version}sub/{api_token}/auto-number/project**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/project`

HTTP Method: `GET`


## Create Project
### API Endpoint - Create a New Project

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"name":"${pName}","description":"${pDescription}","number":"${pNumber}","status":"${pStatus}","dates":[{"type":"SCHEDULED START","value": "2019-06-01"},{"type":"ACTUAL START","value":"2019-06-15"}]}`;

cinxApi.postNewProject(cinx_api_token, values)
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
            "cinx_id": {
                "type": "PROJECT",
                "domain": "org-0001-4030",
                "id": "4b4d08c7-7edf-57d2-b632-2371f8a18496"
            }
        }
    ]
}
```

This endpoint will be used to insert a new project.

**Notes**

- A CINX Template is available that documents the available fields that can be populated.
- A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-project-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-project-import?body=json`

HTTP Method: `POST`
 
## Modify Project
### API Endpoint - Modify a CINX Project

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"name":"${pName}","description":"${pDescription}","number":"${pNumber}","status":"${pStatus}"}`;

cinxApi.modifyProject(cinx_api_token, project_id, values)
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
            "cinx_id": {
                "type": "PROJECT",
                "domain": "org-0001-4030",
                "id": "4b4d08c7-7edf-57d2-b632-2371f8a18496"
            }
        }
    ]
}
```

This endpoint will be used to modify a project.

**Notes**

- A CINX Template is available that documents the available fields that can be populated.
- A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-project-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-project-import?body=json`

HTTP Method: `PUT`
