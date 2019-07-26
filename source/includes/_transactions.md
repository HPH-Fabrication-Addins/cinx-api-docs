# Transactions
## POST Project Items – csv
### API – POST Project Items – csv Format for Autodesk Fabrication

This URL will be used to POST a csv file containing Autodesk Fabrication items for a specified project. 

URL Pattern:

{api path}/sub/{B2B Id GUID}/partner/exec/cinx/import-excel-bom-items?bom_cdoc=couchdb://{CINX Org Id}/{CINX Project GUID}&user=CINX-SYSTEM&partner=autodesk-fab

 Sample:

`https://api.cinx.com/sub/e8478738-8c4b-a152-609d-f50e34be0090/partner/exec/cinx/import-excel-bom-items?bom_cdoc=couchdb://org-0000-6138/3dde31ee-694e-0e43-8af2-8382bb6dcc1f&user=CINX-SYSTEM&partner=autodesk-fab`

Parameter Information

**/partner/exec/cinx/import-excel-bom-items**   <literal>

**?bom_cdoc= couchdb://**  <literal> 

CINX Org ID = CINX Id of Org that the current user is associated with /default Org Id (ie, **org-0000-8761** for the Your company Development Account)
Project GUID = CINX Project GUID (ie, 3dde31ee-694e-0e43-8af2-8382bb6dcc1f)

**&user=CINX-SYSTEM** <literal> 

**&partner=autodesk-fab** <literal>

## Transaction/BOM Intro
### CINX BOM and BOM-ITEM Introduction

**BOM**

Like many construction software systems, CINX employs the BOM concept.  BOM is an acronym for Bill of Materials.  A BOM is a collection of materials/services that are grouped together for a particular job or transactional purpose.  A BOM will generally contain some descriptive information about its use and then have a listing of materials or services that are linked to it.   

CINX supports the following BOM types:

BOM-ASSEMBLY (Assembly)

BOM-REQ (Requisition)

BOM-RFQ (Request for Quotation)

BOM-QUOTE (Quotation)

BOM-PO (Purchase Order)

BOM-PO-MEMO (Purchase Order Change Order)

BOM-DELIVERY

BOM-RETURN

BOM-INVOICE

PROJECT

**BOM-ITEM**

Once a Catalog item is added to a BOM/Project it becomes a BOM-ITEM.  Items imported from another system (estimating, CAD) will also become BOM-ITEMs.

BOM-ITEM is a common CINX item data structure that is used of all BOM types.  It inherits from the Catalog Item structure and also provides additional fields for defining its use within a project (quantities, breakdown structure, spec requirements) and transactions (availability and delivery information).
	
The BOM-ITEM will be assigned a CINX GUID and also contain references (GUIDs) to the “BOM/Project” it was attached to and also its original catalog item.

## Get BOMs
### API – GET BOM List – General Response

This request will be used to get a list of the org’s BOMs from CINX.  The response will contain general information that is common to all BOMs in CINX.  Note:  Other API calls are available to provide additional information specific to each type of BOM

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms

URL Pattern using a BOM-Type filter:

{api path}/sub/{B2B Id GUID}/boms?type=pml

Available BOM-Type filters: **type=assembly, type=po, type=quote, type=rfq, type=req, type=po, type=po-memo, type=delivery, type=return, type=invoice**

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/boms?type=assembly`

## Get Project Reqs
### API – GET Requisitions for a Project

This request will be used to get a list of the org’s Requisitions for a given project.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/project/{Project GUID}?type=req

Supported Filters - The following filters are also supported for this call:

Delivery Location Type – will limit results to a specific delivery type location

URL Parameter: **&delivery={option from below}**
Available options are: **JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR**

Procurement Status – will limit results to a specific procurement status

URL Parameter: **&procurement={option from below}**
Available options are: **OPEN, SUBMITTED, IN-REVIEW, APPROVED, APPROVED W/MODS, REJECTED, PENDING ORDER, COMPLETE, CLOSED, CANCELLED, RESUBMITTED**

Vendor Reference – will limit results to a single vendor

URL parameter:  **&vendor={CINX vendor Id}**

Ship Via – will limit results to a specific ship via (transport type) value

URL Parameter: **&ship_via={option from below}**
Available options are: **SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE**

Deliver By Date – will limit results to a specific date

URL Parameter: **&deliver_date={date}**
Date Format: **YYYY-MM-DD**

Submitter – will limit results to a specified CINX User

URL parameter:  **&submitter={submitter CINX User Id}**

Current Owner– will limit results to a specified CINX User to whom the transaction is assigned

URL parameter:  **&owner={CINX User Id}**

Transaction Number– will limit results to a specified transaction number

URL parameter:  **&number={transaction number}**


Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/boms/project/e1e3cb54-b00a-55ae-a079-072732542bf4?type=req&delivery=JOB SITE`

## Get Project RFQs
### API – GET Request for Quotations for a Project

This request will be used to get a list of the org’s Request for Quotations for a given project.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/project/{Project GUID}?type=rfq

Supported Filters - The following filters are also supported for this call:

Delivery Location Type – will limit results to a specific delivery type location

URL Parameter: **&delivery={option from below}**
Available options are: **JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR**

Workflow Status – will limit results to a single workflow status

URL parameter:  **&workflow={workflow status value}**
Available options are:  **IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, QUOTED**

Vendor Reference – will limit results to a single vendor

URL parameter:  **&vendor={CINX vendor Id}**

Ship Via – will limit results to a specific ship via (transport type) value

URL Parameter: **&ship_via={option from below}**
Available options are: **SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE**

Deliver By Date – will limit results to a specific date

URL Parameter: **&deliver_date={date}**
Date Format: **YYYY-MM-DD**

Submitter – will limit results to a specified CINX User

URL parameter: **&submitter={submitter CINX User Id}**

Transaction Number– will limit results to a specified transaction number

URL parameter:  **&number={transaction number}**


Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/boms/project/bb613aff-4256-5359-b7cd-391505d19e01?type=rfq&vendor=org-0001-4221`

## Get Project Quotes
### API – GET Quotes for a Project

This request will be used to get a list of the org’s Quotes for a given project.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/project/{Project GUID}?type=quote

Supported Filters - The following filters are also supported for this call:

Vendor Reference – will limit results to a single vendor

URL parameter:  **&vendor={vendor CINX Id}**

Quote Workflow Status – will limit results to a single workflow status

URL parameter:  **&workflow={workflow status value}**
URL workflow status values:  **IN-PROCESS, SUBMITTED, RECEIVED, ERP PENDING, ERP ACCEPTED, ERP FAILED**

Delivery Location Type – will limit results to a specific delivery type location

URL Parameter: **&delivery={option from below}**
Available options are: **JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR**

Ship Via – will limit results to a specific ship via (transport type) value

URL Parameter: **&ship_via={option from below}**
Available options are: **SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE**

Deliver By Date – will limit results to a specific date

URL Parameter: **&deliver_date={date}**
Date Format: **YYYY-MM-DD**

Submitter – will limit results to a specified CINX User

URL parameter:  **&submitter={submitter CINX User Id}**

Transaction Number– will limit results to a specified transaction number

URL parameter:  **&number={transaction number}**

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/boms/project/f19fc7e7-5f79-aa03-5429-21b6367dd8e3?type=quote`

## Get Project POs
### API – GET Purchase Orders for a Project

This request will be used to get a list of the org’s Purchase Orders for a given project.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/project/{Project GUID}?type=po

Supported Filters - The following filters are also supported for this call:

Delivery Location Type – will limit results to a specific delivery type location

URL Parameter: **&delivery={option from below}**
Available options are: **JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR**

Procurement Status – will limit results to a specific procurement status

URL Parameter: **&procurement={option from below}**
Available options are: **NOT ORDERED, ORDER PENDING, ORDERED, BACK-ORDERED, DELIVERED, RETURNED, CANCELLED, CLOSED, ON-HOLD, INVOICE-APPROVED**

Workflow Status – will limit results to a single workflow status

URL parameter:  **&workflow={workflow status value}**
Available options are:  **IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, QUOTED**

ERP Status – will limit results to a specific ERP integration status

URL Parameter: **&erp_status={option from below}**
Available options are: **NOT SUBMITTED, PENDING, SUBMITTED, APPLIED**

Vendor Reference – will limit results to a single vendor

URL parameter:  **&vendor={CINX vendor Id}**

Ship Via – will limit results to a specific ship via (transport type) value

URL Parameter: **&ship_via={option from below}**
Available options are: **SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE**

Deliver By Date – will limit results to a specific date

URL Parameter: **&deliver_date={date}**
Date Format: **YYYY-MM-DD**

Submitter – will limit results to a specified CINX User

URL parameter:  **&submitter={submitter CINX User Id}**

Transaction Number– will limit results to a specified transaction number

URL parameter:  **&number={transaction number}**

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/boms/project/db0ca505-e2f5-573a-a580-30f51383b0e4?type=po&delivery=JOB%20SITE`

## Get Project PO COs
### API – GET Purchase Order Change Orders for a Project

This request will be used to get a list of the org’s Purchase Order Change Orders for a given project.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/project/{Project GUID}?type=poco

Supported Filters - The following filters are also supported for this call:

Delivery Location Type – will limit results to a specific delivery type location

URL Parameter: **&delivery={option from below}**
Available options are: **JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR**

Procurement Status – will limit results to a specific procurement status

URL Parameter: **&procurement={option from below}**
Available options are: **NOT ORDERED, ORDER PENDING, ORDERED, BACK-ORDERED, DELIVERED, RETURNED, CANCELLED, CLOSED, ON-HOLD, INVOICE-APPROVED**

Workflow Status – will limit results to a single workflow status

URL parameter:  **&workflow={workflow status value}**
Available options are:  **IN-PROCESS, SUBMITTED, RECEIVED, ACCEPTED, DECLINED, QUOTED**

ERP Status – will limit results to a specific ERP integration status

URL Parameter: **&erp_status={option from below}**
Available options are: **NOT SUBMITTED, PENDING, SUBMITTED, APPLIED**

Vendor Reference – will limit results to a single vendor

URL parameter:  **&vendor={CINX vendor Id}**

Ship Via – will limit results to a specific ship via (transport type) value

URL Parameter: **&ship_via={option from below}**
Available options are: **SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE**

Deliver By Date – will limit results to a specific date

URL Parameter: **&deliver_date={date}**
Date Format: **YYYY-MM-DD**

Submitter – will limit results to a specified CINX User

URL parameter:  **&submitter={submitter CINX User Id}**

Transaction Number– will limit results to a specified transaction number

URL parameter:  **&number={transaction number}**


Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/boms/project/bb613aff-4256-5359-b7cd-391505d19e01?type=poco&delivery=FABRICATION%20SHOP`

## Get Project Deliveries
### API – GET Vendor Deliveries for a Project

This request will be used to get a list of the org’s Vendor Deliveries for a given project.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/project/{Project GUID}?type=delivery

Supported Filters - The following filters are also supported for this call:

Vendor Reference – will limit results to a single vendor

URL parameter:  **&vendor={CINX vendor Id}**

Transaction Number– will limit results to a specified transaction number

URL parameter:  **&number={transaction number}**

Delivery Location Type – will limit results to a specific delivery type location

URL Parameter: **&delivery={option from below}**
Available options are: **JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR**

Ship Via – will limit results to a specific ship via (transport type) value

URL Parameter: **&ship_via={option from below}**
Available options are: **SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE**

Submitter – will limit results to a specified CINX User

URL parameter:  **&submitter={submitter CINX User Id}**

Purchase Order Reference – will limit results to a specified CINX Purchase Order

URL parameter:  **&po_guid={CINX Purchase Order Id}**


Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/boms/project/bb613aff-4256-5359-b7cd-391505d19e01?type=delivery&vendor=org-0001-4221`

## Get Project Returns
### API – GET Vendor Returns for a Project

This request will be used to get a list of the org’s Vendor Returns for a given project.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/project/{Project GUID}?type=return

Supported Filters - The following filters are also supported for this call:

Vendor Reference – will limit results to a single vendor

URL parameter:  **&vendor={CINX vendor Id}**

Transaction Number– will limit results to a specified transaction number

URL parameter:  **&number={transaction number}**

Delivery Location Type – will limit results to a specific delivery type location

URL Parameter: **&delivery={option from below}**

Available options are: **JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR**

Ship Via – will limit results to a specific ship via (transport type) value

URL Parameter: **&ship_via={option from below}**
Available options are: **SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE**

Current Owner– will limit results to a specified CINX User to whom the transaction is assigned

URL parameter:  **&owner={CINX User Id}**

Status – will limit results to a single status

URL parameter:  **&status={status value}**
Available options are:  **CREATED, RETURN REQUESTED, RMA REQUESTED, RMA RECEIVED, RMA REFUSED, IN-PROCESS, SHIPPED, RECEIVED, VENDOR INSPECTION, CLOSED**

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/boms/project/bb613aff-4256-5359-b7cd-391505d19e01?type=return&vendor=org-0001-4221`

## Get Project Invoices
### API – GET Invoices for a Project

This request will be used to get a list of the org’s Vendor Invoices for a given project.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/project/{Project GUID}?type=invoice

Supported Filters - The following filters are also supported for this call:

Status – will limit results to a single status

URL parameter:  **&status={status value}**
Available options are:  **PENDING E-INVOICE, ENTERED, REVIEWED, ACCEPTED, IN-DISPUTE, ON-HOLD, REJECTED, SUBMITTED**

ERP Status – will limit results to a specific ERP integration status

URL Parameter: **&erp_status={option from below}**
Available options are: **NOT SUBMITTED, PENDING, SUBMITTED, APPLIED**

Vendor Reference – will limit results to a single vendor

URL parameter:  **&vendor={CINX vendor Id}**

Transaction Number– will limit results to a specified transaction number

URL parameter:  **&number={transaction number}**

Current Owner– will limit results to a specified CINX User to whom the transaction is assigned

URL parameter:  **&owner={CINX User Id}**

Purchase Order Reference – will limit results to a specified CINX Purchase Order

URL parameter:  **&po_guid={CINX Purchase Order Id}**

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/boms/project/bb613aff-4256-5359-b7cd-391505d19e01?type=invoice&number=I456123`

## Get RFQ Quotes
### API – GET Quotes for a Request for Quotation

This request will be used to get a list of the org’s Quotes for a given Request for Quotation.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/source/{RFQ GUID}?type=quote

Supported Filters - The following filters are also supported for this call:

Vendor Reference – will limit results to a single vendor

URL parameter:  **&vendor={vendor Id}**

Quote Workflow Status – will limit results to a single workflow status

URL parameter:  **&workflow={workflow status value}**
Available options are:  **IN-PROCESS, SUBMITTED, RECEIVED, ERP PENDING, ERP ACCEPTED, ERP FAILED**

Delivery Location Type – will limit results to a specific delivery type location

URL Parameter: **&delivery={option from below}**
Available options are: **JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR**

Ship Via – will limit results to a specific ship via (transport type) value

URL Parameter: **&ship_via={option from below}**
Available options are: **SUPPLIER TRUCK, MOTOR COMMON CARRIER, CUSTOMER PICKUP, TRACKING GROUND, GROUND, AIR EXPRESS, AIR, PRIVATE PARCEL SERVICE**

Deliver By Date – will limit results to a specific date

URL Parameter: **&deliver_date={date}**
Date Format: **YYYY-MM-DD**

Submitter – will limit results to a specified CINX User

URL parameter:  **&submitter={submitter CINX User Id}**

Transaction Number– will limit results to a specified transaction number

URL parameter:  **&number={transaction number}**

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/boms/source/86469e52-8a53-667c-1a9e-cf621880535d?type=quote`

## Get PO Child Transactions
### API – GET Child Transactions for a Specific Purchase Order

This request will be used to get a list of transactions related to a specific Purchase Order.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms/source/{PO GUID}?type={transaction type reference}

Supported Transaction Type References:

Purchase Order Change Order:  **poco**
Delivery Reference:  **delivery**
Invoice Reference:  **invoice**
Return Reference:  **return**


Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/boms/source/80e6d9c8-d2e4-5aaa-9bd3-3957430741dd?type=delivery`

## Get Back-Orders
### API – GET Back-Ordered Items

This request will be used to get a list of items that have a procurement status of Back-Ordered.

URL Pattern:

{api path}/sub/{B2B Id GUID}/bom/back-ordered/items

{api path}/sub/{B2B Id GUID}/bom/back-ordered/items?{filter type name}={filter value}

Supported Filters - The following filters are also supported for this call:

Delivery Location Type – will limit results to a specific delivery type location

URL Parameter: **delivery={option from below}**
Available options are: **JOB SITE, FABRICATION SHOP, OFFICE, WAREHOUSE, FABRICATOR**

CINX Project GUID– will limit results to a specific project

URL Parameter: **project={CINX Project GUID}**

Vendor Reference – will limit results to a single vendor

URL parameter:  **vendor={CINX vendor Id}**

CINX Purchase Order GUID – will limit results to a specific purchase order

URL Parameter: **po={CINX Purchase Order GUID}**

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/bom/back-ordered/items?po=0435078e-fc66-53a8-b69e-7641e2247437`

## Mark PO as Applied
### API – Mark a PO as Applied in an ERP System

This request will be used to update the ERP status of a Purchase Order in CINX.  This call should be used after a PO from CINX is updated in an ERP/Accounting system. 

URL Pattern:

{api path}/sub/{B2B Id GUID}/po/{PO GUID}/applied

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/po/1091f700-3203-59c6-8da5-184609ab245a/applied`

## Create New Requisition
### API – Create a New Requisition

This request will be used to create a new requisition in the org’s CINX account.

URL Pattern:

{api path}/sub/{B2B Id GUID}/req/create?values={JSON Structure}

The values section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the CINX Requisition JSON Structures section of this document for a listing of the available JSON structures.

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/req/create?values={"name":"456321","number":"456321","description":"create req"}`

## JSON Structures
### CINX Requisition JSON Structures

The JSON structures shown below can be used in API calls to Create or Modify a Requisition.

If the structure is an array, all elements of the array must be submitted.  

Name (required)
“name”:”value”

Number (required)
“number”:”value”

Description
“description”:”value”

Procurement Status
“procurement_status”:”value”
Available options are: OPEN, SUBMITTED, IN-REVIEW, APPROVED, APPROVED W/MODS, REJECTED, PENDING ORDER, COMPLETE, CLOSED, CANCELLED, RESUBMITTED
Default value: OPEN

Project Defaults (object)
“project_defaults”:
“construction_level”:”value”,
“construction_space”:”value”,
“construction_sub_space”:”value”
“construction_system”:”value”,
“prefabrication_work_order_number”:”value”,
“prefabrication_spool_number”:”value”,
“allow_substitutes”:”{Boolean value}”

Sample: 

`"project_defaults":{ "construction_level":”3”,"construction_space":”lobby”,"construction_sub_space":”restrooms”,”construction_system”:”DWV”,”prefabrication_work_order_number”:”101”,”prefabrication_spool_number”:”456”,”allow_substitutes”:”0” }`

Transaction Information (object)
“tx”:
“cost_code_value”:”value”,
“phase”:”value”,
“category”:”value”
“is_tax_exempt”:”Boolean value}”
“tax_group”:”value”,
“manual_comment”:”value”,
“allow_substitutes”:”{Boolean value}”

Sample: 
`"tx":{ "cost_code_value":”22-250”,"phase":”Floor 2”,"category":”MAT”,”is_tax_exempt”:”0”,”tax_group”:”NH-13”,”manual_comment”:”comment text”,”allow_substitutes”:”1”}`

Delivery (object)
“delivery”:
“delivery_attention”:”value”,
“labeling_instructions”:”value”,
“packaging_instructions”:”value”,
 “delivery_location_type”:”value”,
“manual_instructions”:”value”,
“terms”:”value”

Sample: 
`"delivery":{ "delivery_attention":”Dan Thomas”,"labeling_instructions":”101”,"packaging_instructions":”Pallet”,”delivery_location_type”:”fabrication shop”,”manual_instructions”:”deliver before 9AM”,”terms”:”shipping term text”}`





















