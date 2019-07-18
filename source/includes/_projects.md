# Projects

## Get Project List
### API – GET Project List

This request will be used to get a list of the org’s Projects from CINX.

URL Pattern:

{api path}/sub/{B2B Id GUID}/boms?type=pml

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/boms?type=pml

## Get Project Details
### API – GET Project Details

URL Pattern:

{api path}/sub/{B2B Id GUID}/project/{Project GUID}/details

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/project/c8195210-dba8-b303-6292-8c7a60b8f539/details

## Create Project
### API – PUT New Project

This request will be used to create a new project in the org’s CINX account.

URL Pattern:

{api path}/sub/{B2B Id GUID}/project/create?values={JSON Structure}

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Project JSON Structures** section of this document for a listing of the available JSON structures.

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/project/create? values={"name":"Test-2016-06-09","description":"Test API create a project","number":"101"}

 
## Modify Project
### API – Modify a CINX Project

This request will be used to modify a project in the org’s CINX account.

URL Pattern:

{api path}/sub/{B2B Id GUID}/project/{Project GUID}/modify?values={JSON Structure}

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Project JSON Structures** section of this document for a listing of the available JSON structures.

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/project/c8195210-dba8-b303-6292-8c7a60b8f539/modify?values={"status":"Bid"}




