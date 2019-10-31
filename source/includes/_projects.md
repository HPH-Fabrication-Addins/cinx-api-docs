# Projects

## Project Definition
### CINX Object Defintion - Project

A CINX project is a job that is being performed for a customer/client on building, structure, or other asset.

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - A customer and its building can be associated with a project

**Supported API Services**

  - [Get a List of Projects](#get-project-list)
  - [Get a Project](#get-project)
  - [Get a Project Template](#get-project-template)
  - [Get a Project Number](#get-project-number)
  - [Create a Project](#create-project)
  - [Modify a Project](#modify-project)
  - [Get Project Job Costing](#project-job-costing)
  - [Get Project Transactions](#project-transactions)
  - Get Project Submittals

## Get Project List
### API Endpoint - Get List of Projects

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

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
                "building_name": null,
                "project_number": null
            },
            "external_references": [],
            "item_count": 7
        }
    ]
}
```
`GET`

This endpoint will be used to get a list of the organization's projects. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/projects**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/projects`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
number | Limits results to a specific project number. | {project number}
status | Limits results to a specific status. | CONCEPTUAL, BID, DESIGN, CONSTRUCTION, CLOSEOUT, COMPLETED, NOT SPECIFIED

## Get Project
### API Endpoint - Get a Project

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getProjectDetails(cinx_api_token, project_guid)
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [{
        "cinx_guid": "e1e3cb54-b00a-55ae-a079-072732542bf4",
        "locked": "0",
        "number": "WTS-2017-04",
        "name": "WTS-2017-04 - ATC Denver",
        "description": "17243",
        "project_manager": "Will Stone",
        "status": "DESIGN",
        "item_count": 241,
        "dates": {
            "contract_award": null,
            "scheduled_start": null,
            "actual_start": null,
            "scheduled_complete": null,
            "actual_complete": null
        },
        "customer": {
            "cinx_commerce_guid": "b65d1355-e1f7-55bc-b44a-5dc441989235",
            "customer_name": "Team O'Neil",
            "cinx_building_guid": "070eb515-65d7-5430-9e09-24eb9af9dcd1",
            "building_name": "motorsports",
            "project_number": null
        },
        "classifications": {
            "delivery_method": "INTEGRATED PROJECT DELIVERY",
            "is_leed": "1",
            "org_defined_type": "Industrial",
            "construction_type": "NEW",
            "industry_type": "COMMERCIAL",
            "cinx_type": "PROJECT",
            "sector_type": "PRIVATE - FOR PROFIT"
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
        },
        "external_references": []
    }]
}
```
`GET`

This endpoint will be used to get the details of a specific project.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/e8c5dc6b-e95a-5009-ad89-a11520f55493`

## Get Project Template
### API Endpoint - Get a Project Template

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getProjectTemplate(cinx_api_token)
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [{
        "doc_info": {},
        "template": {
            "cinx_guid": null,
            "number": null,
            "name": null,
            "description": null,
            "status": "NOT SPECIFIED",
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
                "delivery_method": null,
                "is_leed": false,
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
                "cinx_guid": null,
                "tax_group_name": null,
                "tax_exempt_id": null
            },
            "size_square": {
                "value": null,
                "uom": "FEET"
            },
            "external_references": [{
                "type": null,
                "description": null,
                "value": null
            }],
            "items": [{
                "cinx_guid": null,
                "quantity": 1,
                "currency": "USD",
                "order_lead_time": null,
                "allow_substitutes": true,
                "procurement_status": "NOT ORDERED",
                "construction_status": null,
                "hph_code": null,
                "org_item_id": null,
                "org_system_id": null,
                "mfr_part_number": null,
                "upc": null,
                "size": null,
                "description": null,
                "mfr_name": null,
                "item_type": null,
                "weight": {
                    "value": null,
                    "uom": null
                },
                "dates": {
                    "need_by": null,
                    "order_by": null,
                    "installed": null
                },
                "vendor": {
                    "cinx_commerce_guid": null,
                    "number": null,
                    "item_id": null,
                    "system_id": null,
                    "availability_type": null,
                    "availability_location": null
                },
                "delivery": {
                    "deliver_to": null,
                    "location_type": null,
                    "location_name": null,
                    "instructions": null,
                    "labeling_instructions": null,
                    "packaging_instructions": null
                },
                "work_breakdown": {
                    "trade": null,
                    "work_order_id": null,
                    "work_order_name": null,
                    "spool_id": null,
                    "spool_name": null,
                    "building_name": null,
                    "level": null,
                    "space": null,
                    "sub_space": null,
                    "system": null,
                    "arch_symbol": null,
                    "tag": null
                },
                "job_cost": {
                    "cinx_phase_guid": null,
                    "phase_name": null,
                    "cinx_material_cost_code_guid": null,
                    "material_cost_code_name": null,
                    "cinx_labor_cost_code_guid": null,
                    "labor_cost_code_name": null,
                    "cinx_category_guid": null,
                    "category_name": null
                },
                "taxes": {
                    "taxable": true,
                    "cinx_guid": null,
                    "tax_group_name": null,
                    "tax_type": null
                },
                "design": {
                    "model_item_guid": null,
                    "model_name": null,
                    "model_file": null,
                    "drawing_number": null,
                    "drawing_name": null
                },
                "buy_price": {
                    "base_price": null,
                    "multiplier_code": null,
                    "multiplier_value": null,
                    "unit_price": null,
                    "price_uom": null,
                    "price_source_type": null
                },
                "sell_price": {
                    "base_price": null,
                    "multiplier_code": null,
                    "multiplier_value": null,
                    "unit_price": null,
                    "price_uom": null,
                    "price_source_type": null
                },
                "labor_unit": {
                    "cinx_guid": null,
                    "source": null,
                    "base_unit": null,
                    "uom": null,
                    "multiplier_value": null,
                    "unit": null
                },
                "labor_cost": {
                    "labor_rate": null,
                    "sub_total": null,
                    "adjustment": null,
                    "total": null
                },
                "attributes": [{
                    "name": null,
                    "value": null
                }]
            }]
        },
        "field_options": {},
        "api_calls": []
    }]
}
```
`GET`

This endpoint will be used to get a CINX Template for a project.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/project**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/project`


The table below defines the input fields within the template.

**TEMPLATE FIELDS**

Name | Data Type | Required | Dflt | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; PUT = Yes |  | CINX System Id.
number | String | Yes |  | Public number for the object.
name | String | Yes |  | Public name for the object.
description | String | No |  | Public description for the object.
status | String | Yes | NOT SPECIFIED | Status used to track the project. Template has a list of optional values.
dates.contract_award | Date (YYYY-MM-DD) | No |  | Date the contract was awarded to the contractor.
dates.scheduled_start | Date (YYYY-MM-DD) | No |  | Date the project was scheduled to start.
dates.actual_start | Date (YYYY-MM-DD) | No |  | Date the project began construction.
dates.scheduled_complete | Date (YYYY-MM-DD) | No |  | Date the project was scheduled to finish.
dates.actual_complete | Date (YYYY-MM-DD) | No |  | Date the project was finished.
customer.cinx_commerce_guid | String (GUID Format) | No |  | CINX Commerce Id for the customer that commissioned the project.
customer.name | String | No |  | The name of the customer that commissioned the project.
customer.cinx_building_guid | String (GUID Format) | No |  | CINX Id for the building or structure.
customer.cinx_building_name | String | No |  | Name of the building or structure.
customer.project_number | String | No |  | The project number assigned by the customer for the project.
classifications.delivery_method | String | Yes | NOT SPECIFIED | Project delivery method being used on the project. Template has a list of optional values.
classifications.is_leed | Boolean | Yes | FALSE | Indicator if the project is a LEED project.
classifications.org_defined_type | String | No |  | Organization-defined type of project
classifications.construction_type | String | Yes | NOT SPECIFIED | The construction type for the project. Template has a list of optional values.
classifications.industry_type | String | Yes | NOT SPECIFIED | The construction type for the project. Template has a list of optional values.
classifications.cinx_type | String | Yes | PROJECT | The industry type for the project. Template has a list of optional values.
classifications.sector_type | String | Yes | NOT SPECIFIED | The sector type for the project. Template has a list of optional values.
contract.budget_amount | String | No |  | The budgeted amount for the project.
contract.budget_currency | String | Yes | USD | The currency in which the budget is defined.
taxes.taxable | Boolean | Yes | TRUE | Indicator defining if the project is taxable.
taxes.cinx_guid | String (GUID Format) | No |  | CINX Id for the Tax Group assigned to the items on the project.
taxes.tax_group_name | String | No |  | Name for the Tax Group assigned to the items on the project.
taxes.tax_exempt_id | String | No |  | Tax-Exempt Id.
size_square.value | String | No |  | Size of the project.
size_square.uom | String | Yes | FEET | Unit-of-measure that the size of the project is defined.
external_references.type | String | No |  | Non-CINX system reference type.
external_references.description | String | No |  | Non-CINX system reference description.
external_references.value | String | No |  | Non-CINX system reference value.
items.cinx_guid | String (GUID Format) | POST = No; Put = Yes |  | CINX System Id.
items.quantity | Real | Yes | 1 | Quantity of the item that is being ordered.
items.currency | String | Yes | USD | Currency in which the price is being defined.  Three-character alpha abbreviation.
items.order_lead_time | Real | No | | Number of days required for the material vendor to aquire the item.
items.allow_substitutes | Boolean | Yes | TRUE | Indicator if the product can be sourced from an alternate manufacturer.
items.procurement_status | String | Yes | NOT ORDERED | Status used to track the procurement activities of the item. Template has a list of optional values.
items.construction_status | String | Yes | NOT INSTALLED | Status used to track the installation of the item. Template has a list of optional values.
items.hph_code | String | No |  | HPH Item Code for the item that is being ordered.
items.org_item_id | String | No |  | The requesting company's Org Item Id for the product that is being ordered. User-friendly code.
items.org_system_id | String | No |  | The requesting company's Org System Item Id for the product that is being ordered. Unique Id code.
items.mfr_part_number | String | No |  | Manufacturer-defined Part/Catalog Number for the product that is being ordered.
items.upc | String | No |  | Manufacturer-defined UPC Number for the product that is being ordered.
items.size | String | No |  | Size of the item that is being ordered.
items.description | String | No |  | Description of the item that is being ordered.
items.mfr_name | String | No |  | Name of the manufacturer or fabricator that produces the item that is being ordered.
items.item_type | String | No |  | Classification name of the item that is being ordered.
items.weight.value | Real | No |  | Weight of the item.
items.weight.uom | String | No |  | Measurement type in which the weight value is expressed.
items.dates.need_by | Date (YYYY-MM-DD) | No |  | Date the product needs to be delivered to the specified delivery location.
items.dates_order_by | Date (YYYY-MM-DD) | No |  | Date the product needs to be ordered from the vendor.
items.dates_installed | Date (YYYY-MM-DD) | No |  | Date the product was installed.
items.vendor.cinx_commerce_guid | String (GUID Format) | No |  | CINX Commerce Id for the vendor.
items.vendor.number | String | No |  | The public number of the vendor from whom the product is being sourced.
items.vendor.item_id | String | No |  | The vendor's Org Item Id for the product that is being ordered. User-friendly code.
items.vendor.system_id | String | No |  | The vendor's Org System Item Id for the product that is being ordered. Unique Id code.
items.vendor.availability_type | String | No | | Vendor stocking type for the item. Template has a list of optional values.
items.vendor.availability_location | String | No | | Vendor stocking location for the item.
items.delivery.deliver_to | String | No |  | Deliver To text.
items.delivery.location_type | String | No |  | Where the requester would like the product to be delivered. Template has a list of optional values.
items.delivery_location_name | String | No |  | Name of the location where the item is to be delivered.
items.delivery.instructions | String | No |  | Delivery instructions to be submitted to the vendor responsible for delivering the item.
items.delivery.labeling_instructions | String | No |  | Labeling instructions to be submitted to the vendor responsible for delivering the item.
items.delivery.packaging_instructions | String | No |  | Packaging instructions to be submitted to the vendor responsible for delivering the item.
items.work_breakdown.trade | String | No |  | Contractor defined trade related to the installation of the item.
items.work_breakdown.work_order_id | String | No |  | Contractor defined Work Order Id that was assigned to the product.
items.work_breakdown.work_order_name | String | No |  | Contractor defined Work Order Name that was assigned to the product.
items.work_breakdown.spool_id | String | No |  | Contractor defined Spool Id that was assigned to the product.
items.work_breakdown.spool_name | String | No |  | Contractor defined Spool Name that was assigned to the product.
items.work_breakdown.building_name | String | No |  | Name of the building in which the product will be installed.
items.work_breakdown.level | String | No |  | Level of the building in which the product will be installed.
items.work_breakdown.space | String | No |  | Space of the building in which the product will be installed.
items.work_breakdown.sub_space | String | No |  | Sub-space of the building in which the product will be installed.
items.work_breakdown.system | String | No |  | Name of the system in which the product will be installed.
items.work_breakdown.arch_symbol | String | No |  | Architectural symbol of the product.
items.work_breakdown.tag | String | No |  | Text of what should appear on a tag for the item.
items.job_cost.cinx_phase_guid | String (GUID Format) | No |  | CINX Id for the Phase/Sub-Job assigned to the item.
items.job_cost.phase_name | String | No |  | Name for the Phase/Sub-Job assigned to the item.
items.job_cost.cinx_material_cost_code_guid | String (GUID Format) | No |  | CINX Id for the Material Cost Code assigned to the item.
items.job_cost.material_cost_code_name | String | No |  | Name for the Material Cost Code assigned to the item.
items.job_cost.cinx_labor_cost_code_guid | String (GUID Format) | No |  | CINX Id for the Labor Cost Code assigned to the labor reqruired to install the item.
items.job_cost.labor_cost_code_name | String | No |  | Name for the Labor Cost Code assigned to the labor reqruired to install the item.
items.job_cost.cinx_category_guid | String (GUID Format) | No |  | CINX Id for the Category assigned to the item.
items.job_cost.category_name | String | No |  | Name for the Category assigned to the item.
items.taxes.taxable | Boolean | Yes | TRUE | Indicator defining if the product is taxable.
items.taxes.cinx_guid | String (GUID Format) | No |  | CINX Id for the Tax Group assigned to the item.
items.taxes.tax_group_name | String | No |  | Name of the Tax Group assigned to the item.
items.taxes.tax_type | String | No |  | Name of the type of tax. Template has a list of optional values.
items.design.model_item_guid | String (GUID Format) | No |  | Id assigned by the authoring system that placed the item in the model.
items.design.model_name | String | No |  | Name of the model in which the item is located.
items.design.model_file | String | No |  | File name of the model in which the item is located.
items.design.drawing_number | String | No |  | Number of the drawing on which the item is located.
items.design.drawing_name | String | No |  | Name of the drawing on which the item is located.
items.buy_price.base_price | Real | No |  | Base price of the item.
items.buy_price.multiplier_code | String | No | | Code identifying the multiplier code/class.
items.buy_price.multiplier_value | Real | No |  | Multiplier to be applied to the base price of the item.
items.buy_price.unit_price | Real | No |  | Unit price of the item.
items.buy_price.price_uom | String | Yes | E | Price unit-of-measure. Template has a list of optional values.
items.buy_price.price_source_type | String | No |  | Source from which the price was obtained. Template has a list of optional values.
items.sell_price.base_price | Real | No |  | Base price of the item.
items.sell_price.multiplier_code | String | No | | Code identifying the multiplier code/class.
items.sell_price.multiplier_value | Real | No |  | Multiplier to be applied to the base price of the item.
items.sell_price.unit_price | Real | No |  | Unit price of the item.
items.sell_price.price_uom | String | Yes | E | Price unit-of-measure. Template has a list of optional values.
items.sell_price.price_source_type | String | No |  | Source from which the price was obtained. Template has a list of optional values.
items.labor_unit.cinx_guid | String (GUID Format) | No |  | CINX System Id for the labor unit from its source catalog.
items.labor_unit.source | String | No | | Name of the source that created the labor unit.
items.labor_unit.base_unit | Real | No |  | Base labor unit for the item.
items.labor_unit.uom | String | YES | HOUR | Unit-of-measure in which the labor unit is expressed.
items.labor_unit.multiplier_value | Real | No |  | Multiplier to be applied to the base labor unit for the item.
items.labor_unit.unit | Real | No |  | The labor unit value to be used for the item.
items.labor_cost.labor_rate | Real | No |  | Labor rate ($) to be used when billing for the installation of the item.
items.labor_cost.sub_total | Real | No |  | Labor sub-total to be used when billing for the installation of the item.
items.labor_cost.adjustment | Real | No |  | Adjustment amount ($) applied to the sub-total.
items.labor_cost.total | Real | No |  | Total amount ($) used when billing for the installation of the item.
items.attributes.name | String | No |  | Name of the attribute.
items.attributes.value | String | No |  | Value of the attribute.

## Get Project Number
### API Endpoint - Get a New Project Number

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '2.0');

cinxApi.getProjectNumber(cinx_api_token)
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
            "project": "PRJ-2019-01"
        }
    ]
}
```
`GET`

This endpoint will be used to get a value to be used in the number field of a new project.

**Notes**

  - The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.


URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/project**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/project`

## Create Project
### API Endpoint - Create a New Project

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

var isSynchronous = true;
//projectObject can be created based on the template retreived from cinxApi.getProjectTemplate(cinx_api_token) call
cinxApi.postProject(cinx_api_token, projectObject, isSynchronous)
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
 `POST`

This endpoint will be used to insert a new project.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-project-import?body=json**

URL Samples: 

  - Asynchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-project-import?body=json`
  - Synchronous processing: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-project-import?body=json&synchronous=1`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json
synchronous | Switch to have the payload processed synchronously. | 1

## Modify Project
### API Endpoint - Modify a CINX Project

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

var isSynchronous = true;
//projectObject can be created based on the template retreived from cinxApi.getProjectTemplate(cinx_api_token) call
cinxApi.putProject(cinx_api_token, projectObject, isSynchronous)
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

This endpoint will be used to modify a project.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-project-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-project-import?body=json`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
body | Defines the content type contained in the payload | json