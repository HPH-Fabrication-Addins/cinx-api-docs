# Job Costs

## CINX Job Cost Introduction

To allow for the proper reporting of Project items and integration of transactions with contractor accounting systems, CINX has the ability for a company to define their job costing attributes. CINX supports the following Job Cost information types:

**PHASES**
A Phase is construction management concept that allows a company to break-down a project into a smaller group of tasks commonly used for scheduling, sequencing, and reporting purposes.  A Phase is also referred to as a Sub-Job, Area, or Extra by other software systems.  Examples Phases include, Site Work, Floor, and System.

**COST CODES**
A Cost Code is an accounting and construction management concept that allows a company to track material and labor for cost reporting purposes.  Other systems refer to Cost Codes as Item Groups.  Example Cost Codes are Sanitary Sewer, Domestic Water, and Gas.

**CATEGORIES**
A Category is an accounting that allows a company to classify project costs for expensing purposes.  Categories are also known as Cost Classes.  For example, Material, Labor, Sub-Contractor, and Rental.

**TAX GROUPS**
A Tax Group is a collection of tax fields defined in an accounting system that allows for the proper identification and processing of taxes.  

# API – GET a List of the Job Cost Phases

This URL will be used to get the list of Phases in the company’s CINX Job Costing library.  

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/get-list/phases


Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/get-list/phases

## API – Create a Job Cost Phase 

This URL will be used to create a new Phase in the company’s CINX Job Costing library.   

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/phases? values={“phases”:[{JSON Structure}]}

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

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/modify/phases? values={%22phases%22:[{%22name%22:%2202-8157%22,%22description%22:%22Site%20Work%22,%22reference_id%22:%22%22,%22user_id%22:%22%22,%22date_modified%22:%22%22,%22status%22:%22A%22,%22material_cost_code%22:%225241%22}]}

## API – Modify a Job Cost Phase 

This URL will be used to modify an existing Phase in the company’s CINX Job Costing library. 

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/modify/phases? values={“phases”:[{JSON Structure}]}

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

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/modify/phases?user=dc3aecca-f2ec-ee6e-eee9-6d96d45390fa&values={"phases":[{"guid":"6ebcc266-83b4-85cf-53f9-8db2d52f15cb","name":"02-8158","description":"Site Work","reference_id":"","user_id":"","date_modified":"","status":"A","material_cost_code":"5241"}]}

## API – GET a List of the Job Cost Cost Codes

This URL will be used to get the list of Cost Codes in the company’s CINX Job Costing library.   

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/get-list/material-cost-codes

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/get-list/material-cost-codes

## API – Create a Job Cost Category

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

## API – GET a List of the Job Cost Tax Groups

This URL will be used to get the list of Tax Groups in the company’s CINX Job Costing library.  

URL Pattern:

{api path}/sub/{B2B Id GUID}/org-job-cost/get-list/tax-groups

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/get-list/tax-groups

## API – Create a Job Cost Tax Group

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

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/modify/tax-groups? values={"tax_groups":[{"name":"MD1","tax_type":"Sales","description":"Maryland Sales Tax","reference_id":"T1254","user_id":"","date_modified":"","status":"A","rate":"5.65"}}}


## API – Modify a Job Cost Tax Group

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

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org-job-cost/modify/tax-groups? values={"tax_groups":[{"guid":"dba9161a-4d78-9cff-fa37-6a7c344837b2","name":"MD1","tax_type":"Sales","description":"Maryland Sales Tax","reference_id":"T1254","user_id":"","date_modified":"","status":"A","rate":"5.65"}]}

 
 
