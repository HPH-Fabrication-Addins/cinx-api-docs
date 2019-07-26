# Projects

## Get Project List
### API – GET Project List

This request will be used to get a list of the org’s Projects from CINX.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms?type=pml

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/boms?type=pml`

## Get Project Details
### API – GET Project Details

URL Pattern:

{api path}/sub/{B2B Id GUID}/project/{Project GUID}/details

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/project/c8195210-dba8-b303-6292-8c7a60b8f539/details`

## Create Project
### API – PUT New Project

This request will be used to create a new project in the org’s CINX account.

URL Pattern:

{api path}/sub/{B2B Id GUID}/project/create?values={JSON Structure}

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Project JSON Structures** section of this document for a listing of the available JSON structures.

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/project/create?values={"name":"Test-2016-06-09","description":"Test API create a project","number":"101"}`

 
## Modify Project
### API – Modify a CINX Project

This request will be used to modify a project in the org’s CINX account.

URL Pattern:

{api path}/sub/{B2B Id GUID}/project/{Project GUID}/modify?values={JSON Structure}

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Project JSON Structures** section of this document for a listing of the available JSON structures.

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/project/c8195210-dba8-b303-6292-8c7a60b8f539/modify?values={"status":"Bid"}`

## JSON Structures
### CINX Project JSON Structures

The JSON structures shown below can be used in API calls to Create or Modify a Project.

If the structure is an array, all elements of the array must be submitted. 

Project Name (required)
“name”:”value”

Project Number
“number”:”value”

Project Description
“description”:”value”

Project Status
“status”:”value”
Available options are: CONCEPTUAL, DESIGN, BID, CONSTRUCTION, CLOSEOUT, COMPLETED, NOT SPECIFIED
Default value: NOT SPECIFIED

Is Tax Exempt
“is_tax_exempt”:” {Boolean value}”

Project Type - Construction
“type_construction”:”value”
Available options are: NEW, REMODEL, REPAIR, NOT SPECIFIED
Default value: NOT SPECIFIED

Project Type - Industry
“type_industry”:”value”
Available options are: RESIDENTIAL, LIGHT COMMERCIAL, COMMERCIAL, INDUSTRIAL, UTILITY, HOSPITAL & HEALTHCARE, BIO/PHARM, PULP & PAPER, BREWERY, HEAVY/CIVIL, NOT SPECIFIED 
Default value: NOT SPECIFIED

Project Type – Org Defined (each org can define a set list of project types to be used to classify their projects)
“type_org_defined”:”value”

Project Delivery Method
“delivery_method”:”value”
Available options are: DESIGN-BUILD, DESIGN-BID-BUILD, INTEGRATED PROJECT DELIVERY, CM-AGENCY, CM-AT RISK, CM-GC, GUARANTEED MAXIMUM PRICE, DESIGN-BID-BUILD-OPERATE-MAINTAIN, BUILD-OPERATE-TRANSFER, NOT SPECIFIED 
Default value: NOT SPECIFIED

Contract Budget Amount
“contract_budget_amount”:”value”

Contract Budget Amount Currency
“contract_budget_amount”:”value”
Default value: USD

Project Size - Square
“size_square_value”:”value”

Project Size – Square Unit-of-Measure
“size_square_uom”:”value”
Available options are: FEET, METERS
Default value: FEET

Is a LEED Project
“is_leed”:” {Boolean value}”

Customer Project Number
“customer_project_number”:”value”

Dates (array)
“dates”:[{”type”:”type name”,”value”: “value”}]
Available “date types” are: SCHEDULED START, ACTUAL START, SCHEDULED COMPLETE, ACTUAL COMPLETE, BID DUE, CONTRACT AWARD, {user defined}


Additional content types are available; please contact HPH if your system requires additional project content.

## Delete Project
### API – Delete a CINX Project

This request will be used to delete a project in the org’s CINX account.

URL Pattern:

{api path}/sub/{B2B Id GUID}/project/{Project GUID}/delete 

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/project/c8195210-dba8-b303-6292-8c7a60b8f539/delete`

## Job Cost Intro
### CINX Project Job Cost Introduction

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

**API – Create a Job Cost Phase**

**API – Create a Job Cost Cost Code**

**API – Create a Job Cost Category**

## Get Phases & Cost Codes
### API – GET a Project’s Phases and Cost Codes List

This request will be used to get a list of a project’s job cost information – phases and cost codes.  The response will contain full details for each phase/cost code.

URL Pattern:

{api path}/sub/{B2B Id GUID}/project/{Project GUID}/cost-codes

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/db0ca505-e2f5-573a-a580-30f51383b0e4/cost-codes`

## Create Phases & Cost Codes
### API – Create a Project’s Phase and Cost Code

This request will be used to create a project’s phase and cost code.

URL Pattern:

{api path}/sub/{B2B Id GUID}/project/{Project GUID}/cost-code/create?values={JSON Structure}

The values section of this URL must contain properly formatted JSON.  Please see the CINX Project Phase/Cost Code JSON Structures section of this document for a listing of the available JSON structures.
Please note that Phases, Cost Codes, and Categories must be established in the company’s CINX account before they can be attached to a specific project.  

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/db0ca505-e2f5-573a-a580-30f51383b0e4/cost-code/create?values={"material_cost_code":"101-1025","phase":"First Floor","category":"MAT","construction_status":"IN-PROCESS","percent_complete":"45","material_cost":{ "estimated":"4523.00","budgeted":"4600.00","actual":"4502.47"},"labor_cost":{ "estimated":"1001.12","budgeted":"1050.00","actual":"1093.00"},"labor_units":{"estimated":"100","budgeted":"150","actual":"93"},"dates":{ "start_scheduled":"2019-06-01","start_actual":"2019-06-10","completion_scheduled":"2020-01-14","completion_actual":"2019-02-01"}}`

## Modify Phases & Cost Codes
### API – Modify a Project’s Phase and Cost Code

This request will be used to modify a project’s phase and cost code.

URL Pattern:

{api path}/sub/{B2B Id GUID}/project-cost-code/{Project Cost Code GUID}/modify?values={JSON Structure}

The values section of this URL must contain properly formatted JSON.  Please see the CINX Project Phase/Cost Code JSON Structures section of this document for a listing of the available JSON structures.

Note:  Only modified values need to be submitted.

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project-cost-code/b356381f-081d-5e5f-b878-94863a90d90d/modify?values={"percent_complete":"100","construction_status":"INSTALLED"}`

## JSON Structures
### CINX Project Phase/Cost Code JSON Structures

The JSON structures shown below can be used in API calls to Create or Modify a Project.

Material Cost Code (required)
“material_cost_code”:”value”
Potential values are: The name/number of the cost code or the CINX GUID for the cost code.

Phase (name or CINX GUID)
“phase”:”value”
Potential values are: The name/number of the phase or the CINX GUID for the phase.

Category (name or CINX GUID)
“category”:”value”
Potential values are: The name/number of the category or the CINX GUID for the category.

Construction Status
“construction_status”:”value”
Available options are: NOT INSTALLED, IN-PROCESS, INSTALLED, TESTED, COMMISSIONED, OPERATIONAL
Default value: NOT INSTALLED

Percent Complete
“percent_complete”:”value”

Material Cost (object)
“material_cost”:
“estimated”:”value”,
“budgeted”:”value”,
“actual”:”value”
Sample: "material_cost":{ "estimated":”4523.00”,"budgeted":”4600.00”,"actual":”4502.47” }


Labor Cost (object)
“labor_cost”:
“estimated”:”value”,
“budgeted”:”value”,
“actual”:”value”
Sample: "labor_cost":{ "estimated":”1001.12”,"budgeted":”1050.00”,"actual":”1093.00” }


Labor Units (object)
“labor_units”:
“estimated”:”value”,
“budgeted”:”value”,
“actual”:”value”
Sample: "labor_units":{ "estimated":”100”,"budgeted":”150”,"actual":”93” }


Dates (object)
“dates”:
“start_scheduled”:”value”,
“start_actual”:”value”,
“completion_scheduled”:”value”,
“completion_actual”:”value”
Date Format: YYYY-MM-DD
Sample: "dates":{ "start_scheduled”:”2019-06-01”,”start_actual”:”2019-06-10”,”completion_scheduled”:”2020-01-14”,”completion_actual”:”2019-02-01” }













