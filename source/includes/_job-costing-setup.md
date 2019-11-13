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
### API Endpoint - Get an Organization's List of Phases

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getPhases(cinx_api_token)
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
            "material_cost_code_name": "23-854",
            "reference_id": null,
            "modified_by": "Will Stone",
            "date_modified": "2019-06-04",
            "status": "A"
        }
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of project phases. In CINX, each company can define the list of standard phases that they use on projects. The company can define a name and description for each phase as well as a default material cost code. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org/job-costing/phases**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/job-costing/phases`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Phase Template
### API Endpoint - Get a Phase Template

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getPhaseTemplate(cinx_api_token)
    .then(function(response) {
        console.log(response);
    })
```

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [{
        "doc_info": {},
        "template": {
            "cinx_guid": null,
            "name": null,
            "description": null,
            "status": "A",
            "reference_id": null,
            "cinx_material_cost_code_guid": null,
            "material_cost_code_name": null
        },
        "field_options": {},
        "api_calls": []
    }]
}
```
`GET`

This endpoint will be used to get a CINX Template for a job costing phase.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/phase**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/phase`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

The table below defines the input fields within the template.

**TEMPLATE FIELDS**

Name | Data Type | Required | Default | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; PUT = Yes |  | CINX System Id.
name | String | Yes |  | Full name of the phase.
description | String | Yes |  | Description of the phase. Can be Null.
status | String | Yes | A | Status of the phase.
reference_id | String | Yes |  | Reference id field that can be used to store an ERP code for the phase. Can be Null.
cinx_material_cost_code_guid | String (GUID Format) | Yes |  | CINX Id for the default material cost code assigned to the phase. Can be Null.
material_cost_code_name | String | Yes |  | Name of the default material cost code assigned to the phase. Can be Null.

## Create Phase
### API Endpoint - Create a Phase 

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

var isSynchronous = true;
//phaseObject can be created based on the template retrieved from cinxApi.getPhaseTemplate(cinx_api_token) call
cinxApi.postPhase(cinx_api_token, phaseObject, isSynchronous)
            .then(function (response) {
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
`POST`

This URL will be used to create a new Phase in the company’s CINX job costing library.   

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-org-phase-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-org-phase-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json

## Modify Phase
### API Endpoint - Modify a Phase 

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

var isSynchronous = true;
//phaseObject can be created based on the template retrieved from cinxApi.getPhaseTemplate(cinx_api_token) call
cinxApi.putPhase(cinx_api_token, phaseObject, isSynchronous)
            .then(function (response) {
                console.log(response);
            }); 
```

> The above code returns JSON structured like this:

```json
{
    
}
```
`PUT`

This URL will be used to modify an existing Phase in the company’s CINX job costing library. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-org-phase-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-org-phase-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json

## Get Mat Cost Codes
### API Endpoint - Get an Organization's List of Material Cost Codes

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getMaterialCostCodes(cinx_api_token)
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
            "description": "W",
            "category_guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
            "category_name": "MAT",
            "reference_id": null,
            "modified_by": "Will Stone",
            "date_modified": "2019-07-26",
            "status": "A"
        }
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of material cost codes. In CINX, each company can define the list of cost codes that can be assigned to materials in a project. The company can define a name and description for each cost code as well as a default category. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org/job-costing/material-cost-codes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/job-costing/material-cost-codes`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Mat Cost Code Template
### API Endpoint - Get a Material Cost Code Template

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getMaterialCostCodeTemplate(cinx_api_token)
    .then(function(response) {
        console.log(response);
    })
```

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [{
        "doc_info": {},
        "template": {
            "cinx_guid": null,
            "name": null,
            "description": null,
            "status": "A",
            "reference_id": null,
            "cinx_category_guid": null,
            "category_name": null
        },
        "field_options": {},
        "api_calls": []
    }]
}
```
`GET`

This endpoint will be used to get a CINX Template for a job costing material cost code.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/material-cost-code**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/material-cost-code`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

The table below defines the input fields within the template.

**TEMPLATE FIELDS**

Name | Data Type | Required | Default | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; PUT = Yes |  | CINX System Id.
name | String | Yes |  | Full name of the material cost code.
description | String | Yes |  | Description of the material cost code. Can be Null.
status | String | Yes | A | Status of the material cost code.
reference_id | String | Yes |  | Reference id field that can be used to store an ERP code for the material cost code. Can be Null.
cinx_category_guid | String (GUID Format) | Yes |  | CINX Id for the default category assigned to the material cost code. Can be Null.
category_name | String | Yes |  | Name of the default category assigned to the material cost code. Can be Null.

## Create Mat Cost Code
### API Endpoint - Create a Material Cost Code

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

var isSynchronous = true;
//ccObject can be created based on the template retrieved from cinxApi.getMaterialCostCodeTemplate(cinx_api_token) call
cinxApi.postMaterialCostCode(cinx_api_token, ccObject, isSynchronous)
       .then(function(response) {
            console.log(response);
        });
```

> The above code returns JSON structured like this:

```json
{
   
}
```
`POST`

This URL will be used to create a new Cost Code in the company’s CINX job costing library.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-material-cost-code-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-material-cost-code-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json

## Modify Mat Cost Code
### API Endpoint - Modify a Material Cost Code

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

var isSynchronous = true;
//ccObject can be created based on the template retrieved from cinxApi.getMaterialCostCodeTemplate(cinx_api_token) call
cinxApi.putMaterialCostCode(cinx_api_token, ccObject, isSynchronous)
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
    
}
```
`PUT`

This URL will be used to modify an existing Cost Code in the company’s CINX job costing library.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-material-cost-code-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-material-cost-code-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json

## Get Labor Cost Codes
### API Endpoint - Get an Organization's List of Labor Cost Codes

```json
{
    "response": {},
    "rows": [
        {
            "cinx_guid": "314f6a13-56b3-5c3f-b14e-10d159e4c5c0",
            "name": "101-1025",
            "description": "W",
            "category_guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
            "category_name": "MAT",
            "reference_id": null,
            "modified_by": "Will Stone",
            "date_modified": "2019-07-26",
            "status": "A"
        }
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of labor cost codes. In CINX, each company can define the list of cost codes that can be assigned to labor activities associated with material products. The company can define a name and description for each cost code as well as a default category. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org/job-costing/labor-cost-codes**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/job-costing/labor-cost-codes`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Labor Cost Code Template
### API Endpoint - Get a Labor Cost Code Template

```json
{
    "response": {},
    "rows": [{
        "doc_info": {},
        "template": {
            "cinx_guid": null,
            "name": null,
            "description": null,
            "status": "A",
            "reference_id": null,
            "cinx_category_guid": null,
            "category_name": null
        },
        "required_post": [],
        "required_put": [],
        "field_options": {},
        "api_calls": []
    }]
}
```
`GET`

This endpoint will be used to get a CINX Template for a job costing labor cost code.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/labor-cost-code**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/labor-cost-code`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

The table below defines the input fields within the template.

**TEMPLATE FIELDS**

Name | Data Type | Required | Default | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; PUT = Yes |  | CINX System Id.
name | String | Yes |  | Full name of the labor cost code.
description | String | Yes |  | Description of the labor cost code. Can be Null.
status | String | Yes | A | Status of the labor cost code.
reference_id | String | Yes |  | Reference id field that can be used to store an ERP code for the labor cost code. Can be Null.
cinx_category_guid | String (GUID Format) | Yes |  | CINX Id for the default category assigned to the labor cost code. Can be Null.
category_name | String | Yes |  | Name of the default category assigned to the labor cost code. Can be Null.

## Create Labor Cost Code
### API Endpoint - Create a Labor Cost Code

```json
{
   
}
```
`POST`

This URL will be used to create a new Cost Code in the company’s CINX job costing library.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-labor-cost-code-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-labor-cost-code-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json


## Modify Labor Cost Code
### API Endpoint - Modify a Labor Cost Code

```json
{
    
}
```
`PUT`

This URL will be used to modify an existing Cost Code in the company’s CINX job costing library.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-labor-cost-code-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-labor-cost-code-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json

## Get Categories
### API Endpoint - Get an Organization's List of Categories

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getCategories(cinx_api_token)
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
            "cinx_guid": "31d57bb1-156e-5cf2-a1ce-05b57232e643",
            "name": "MAT",
            "description": "Material",
            "reference_id": null,
            "modified_by": "Will Stone",
            "date_modified": "2019-06-04",
            "status": "A"
        }
    ]
}
```
 `GET`

This endpoint will be used to get a company’s list of accounting categories. In CINX, each company can define the list of standard categories. The company can define a name and description for each category. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org/job-costing/categories**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/job-costing/categories`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Category Template
### API Endpoint - Get a Category Template

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getCategoryTemplate(cinx_api_token)
    .then(function(response) {
        console.log(response);
    })
```

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [{
        "doc_info": {},
        "template": {
            "cinx_guid": null,
            "name": null,
            "description": null,
            "status": "A",
            "reference_id": null,
            "cinx_category_guid": null,
            "category_name": null
        },
        "field_options": {},
        "api_calls": []
    }]
}
```
`GET`

This endpoint will be used to get a CINX Template for an accounting category.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/category**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/category`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

The table below defines the input fields within the template.

**TEMPLATE FIELDS**

Name | Data Type | Required | Default | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; PUT = Yes |  | CINX System Id.
name | String | Yes |  | Full name of the category.
description | String | Yes |  | Description of the category. Can be Null.
status | String | Yes | A | Status of the category.
reference_id | String | Yes |  | Reference id field that can be used to store an ERP code for the category. Can be Null.

## Create Category
### API Endpoint - Create a Category

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

var isSynchronous = true;
//cObject can be created based on the template retrieved from cinxApi.getCategoryTemplate(cinx_api_token) call
cinxApi.postCategory(cinx_api_token, cObject, isSynchronous)
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
           
        }
    ]
}
```
`POST`

This URL will be used to create a new Category in the company’s CINX job costing library.   

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-org-category-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-org-category-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json

## Modify Category
### API Endpoint - Modify a Job Cost Category
`PUT`

This URL will be used to modify an existing Category in the company’s CINX job costing library.   

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-org-category-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-org-category-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json

## Get Tax Groups
### API Endpoint - Get an Organization's List of Tax Groups

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getTaxGroups(cinx_api_token)
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
            "cinx_guid": "7c42f24f-766e-5220-bc7e-cce8048dbb57",
            "name": "TAX-12",
            "description": "state Tax",
            "rate": 8,
            "tax_type": "Sales",
            "reference_id": null,
            "modified_by": "Will Stone",
            "date_modified": "2017-10-20",
            "status": "A"
        }
    ]
}
```
`GET`

This endpoint will be used to get a company’s list of tax groups. In CINX, each company can define the list of standard tax groups. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/org/job-costing/tax-groups**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/job-costing/tax-groups`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

## Get Tax Group Template
### API Endpoint - Get a Tax Group Template

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getTaxGroupTemplate(cinx_api_token)
    .then(function(response) {
        console.log(response);
    })
```

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [{
        "doc_info": {},
        "template": {
            "cinx_guid": null,
            "name": null,
            "description": null,
            "rate": null,
            "tax_type": null,
            "status": "A",
            "reference_id": null
            
        },
        "field_options": {},
        "api_calls": []
    }]
}
```
`GET`

This endpoint will be used to get a CINX Template for a tax group.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/tax-group**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/tax-group`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml

The table below defines the input fields within the template.

**TEMPLATE FIELDS**

Name | Data Type | Required | Default | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; PUT = Yes |  | CINX System Id.
name | String | Yes |  | Full name of the tax group.
description | String | Yes |  | Description of the tax group. Can be Null.
rate | Real | Yes |  | Value of the tax group rate.
tax_type | String | Yes |  | Type of the tax. Template has a list of optional values. Can be Null.
status | String | Yes | A | Status of the tax group. Template has a list of optional values.
reference_id | String | Yes |  | Reference id field that can be used to store an ERP code for the tax group. Can be Null.

## Create Tax Group
### API Endpoint - Create a Job Cost Tax Group

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

var isSynchronous = true;
//tObject can be created based on the template retrieved from cinxApi.getTaxGroupTemplate(cinx_api_token) call
cinxApi.postTaxGroup(cinx_api_token, tObject, isSynchronous)
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
           
        }
    ]
}
```
`POST`

This URL will be used to create a new Tax Group in the company’s CINX job costing library. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-org-tax-group-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-org-tax-group-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json

## Modify Tax Group
### API Endpoint - Modify a Job Cost Tax Group
`PUT`

This URL will be used to modify an existing Tax Group in the company’s CINX job costing library.  

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-org-tax-group-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-org-tax-group-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json