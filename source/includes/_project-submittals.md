# Project Submittals

## Project Submittal Definition
### CINX Object Definition - Project Submittal



A project submittal is a document that is prepared and submitted to an engineer or other entity for approval. 

For larger projects, a project specification or manual is created and provided to all the project participants. The specification defines everything on a project from bidding requirements to product specifications and installation practices. Engineers normally define the sections of the specification relating to products used by contractors on the project.

Prior to the installation of products, contractors may have to submit documents relating to the products to the engineer or other responsible party for approval. Each document required by the specification and submitted for approval is called a submittal. Typically, the submittal will go through an approval process which may require several iterations.

The CINX web application has functionality to help a contractor create and manage submittals. User's can select product documentation to add as submittals and also upload new documents that needed to be provided to the approving entity.

Currently, the API supports working with documents defined as submittals within CINX.

**Supported API Services**

 - [Get a List of Project Submittals](#get-project-submittals)
 - [Get a Submittal](#get-submittal)

## Get Project Submittals
### API Endpoint – Get a Project's Submittals

<aside class="warning">
BETA: This call is in a beta state and therefore subject to potential change. It has been published to allow partners to provide input.  
</aside>

```json
{
 "response": {},
 "rows": [{
  "cinx_guid": "3dcecae7-c25e-5cc6-8bf9-609f2df56b61",
  "number": "SUB-4579",
  "description": "600WOG SDR BRS LOW LEAD 2PC BALL VLV",
  "type": "Specification Sheet",
  "workflow_status": "CREATED",
  "approval_status": "NOT APPROVED",
  "project_number": "PRJ-2019-13",
  "project_name": "PRJ-2019-13",
  "date_due": "2020-03-04",
  "date_approved": null,
  "date_created": "2020-03-02",
  "date_modified": "2020-03-02",
  "document": {
   "mime_type": "application/pdf",
   "url": "http://cdn.dev.cinx.biz/submittals/org-0001-4030/5bd8a7fbde7809766143984e.pdf"
  }
 }]
}
```

`GET`

This endpoint will be used to get a listing of a project's submittals.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/project/{project_guid}/submittals**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/7880c854-017f-5359-96de-fdef626c33cf/submittals`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
type | Limits results to a specific submittal document type. | SPECIFICATION SHEET, OPERATION MANUAL, SDS, WARRANTY, INSTALL INSTRUCTIONS, PARTS, MILL TEST REPORT, TECHNICAL BULLETIN, TECHNICAL DRAWING, WIRING DIAGRAM, SHOP DRAWING, AS-BUILT-PLAN, BROCHURE, OTHER
approval | Limits results to a specific approval status. | NOT APPROVED, APPROVED, APPROVED WITH CHANGES, REVISE AND RESUBMIT, REJECTED-NOT SPECIFIED DOCUMENT, REJECTED-INCOMPLETE, REJECTED-OTHER, INFORMATIONAL ONLY-FOR RECRORDS, NOT REQUIRED-NOT REVIEWED
workflow | Limits results to a specific workflow status. | CREATED, RECEIVED FROM VENDOR, APPLIED BY CINX, UPLOADED, APPROVED BY ORG, SUBMITTED, PENDING APPROVAL, APPROVED
number | Limits results to a specified submittal number. | {submittal_number}
format | Defines the response format type. If not specified, json will be used. | json, xml
offset | Defines the offset to use when returning the items. | Integer
limit | Defines the number of results to include in the response. If not specified, 10 will be used. | Integer

## Get Submittal
### API Endpoint – Get a Project Submittal 

<aside class="warning">
BETA: This call is in a beta state and therefore subject to potential change. It has been published to allow partners to provide input.  
</aside>

```json
{
  "response": {},
  "rows": [{
    "cinx_guid": "3dcecae7-c25e-5cc6-8bf9-609f2df56b61",
    "locked": "0",
    "number": "SUB-4579",
    "description": "125SWP/200WOG THD BZ CHECK VLV| MV",
    "type": "Specification Sheet",
    "source": "CINX",
    "workflow_status": "CREATED",
    "approval_status": "REJECTED-OTHER",
    "dates": {
      "created": "2020-03-02",
      "last_modified": "2020-03-02",
      "due": "2020-03-04",
      "approved": null
    },
    "project": {
      "guid": "eac76f6c-a988-5b53-a987-58e4bc01bd66",
      "name": "PRJ-2019-13",
      "number": "PRJ-2019-13"
    },
    "project_spec": {
      "page_number": "45",
      "page_paragraph": "5"
    },
    "reference_ids": {
      "architect": "ArchRef-1245",
      "drawing_symbol": null,
      "engineer": "ArchRef-1245",
      "general_contractor": "GCRef-4578",
      "serial_number": null,
      "mfr_part_number": null,
      "mfr_order_number": null
    },
    "master_format": {
      "division_number": "22",
      "division_name": "Plumbing",
      "section_number": "22-05-23",
      "section_name": "General Duty Valves for Plumbing Piping"
    },
    "documents": [{
        "revision": "2",
        "is_current": true,
        "description": "509/509T - Ver2",
        "url": "http://cdn.dev.cinx.biz/submittals/org-0001-4030/1583180007RLSProductCatalog.pdf",
        "mime_type": "application/pdf",
        "date_created": "2020-03-02",
        "creator": {
          "cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
          "name": "Will Stone",
          "email": "willstone@cinx.com"
        }
      },
      {
        "revision": "1",
        "is_current": false,
        "description": "Autogeneration File",
        "url": "http://cdn.dev.cinx.biz/submittals/org-0001-4030/5bd88151de780971827e7079.pdf",
        "mime_type": "application/pdf",
        "date_created": "2020-03-02",
        "creator": {
          "cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
          "name": "Will Stone",
          "email": "willstone@cinx.com"
        }
      }
    ],
    "participants": [{
      "cinx_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
      "name": "Will Stone",
      "email": "willstone@cinx.com",
      "phone": "",
      "org_name": "WTS Mechanical -DEV",
      "org_type": "CONTRACTOR"
    }],
    "attributes": []
  }]
}
```

`GET`

This endpoint will be used to get the details of a specific project submittal.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/submittal/{submittal_guid}/**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/submittal/cd204035-368e-5677-838b-17d7506c4523`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml
