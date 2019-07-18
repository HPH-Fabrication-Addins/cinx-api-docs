# Org/Company

## Get Org Details
### API – GET Organization Details

This request will be used to get the company’s CINX organization details.

URL Pattern:

**{api path}/sub/{B2B GUID}/org/details**

Sample:

**https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/org/details**


## Modify Org
### API – Modify Organization Details

This request will be used to modify an organization’s details.

URL Pattern:

**{api path}/sub/{B2B Id GUID}/modify/org?values={JSON Structure}**

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Organization JSON Structures** section of this document for a listing of the available JSON structures.

Sample:

Dev sample using HPH Account:

**http://api.dev.cinx.biz/sub/83d8ba34-ecf1-59ab-1013-0ba2603adb36/modify/org?values={"types_customers":"Residential,Commercial,Industrial"}**


## JSON Structure
### CINX Organization JSON Structures

The JSON structures shown below can be used in API calls to **Modify** an existing CINX Organization.
If the structure is an array, all elements of the array must be submitted.  

**Name - Primary (required)**
“name_primary”:”value”

**Name - Short**
“name_short”:”value”

**Name - Alternate**
“name_alternate”:”value”

**Name - Previous**
“name_previous”:”value”

**Addresses (array)**
“add_address”:[{”address_type”:”type value”,”address1”: “value”,”address2”: “value”,”address3”: “value”,”city”: “value”,”state”: “value”,”postal_code”: “value”,”country”: “value”,”latitude”: “value” ,”longitude”: “value”}]
Available “address types” are: **SHIPPING, MAILING, BILLING**
Default Country: **USA**

**Marketing – Org Description**
“marketing_desc”:”value”

**Marketing – Org Tag Line**
“marketing_tag”:”value”

**Marketing – Org Year Founded**
“marketing_founded”:”value”

**Location Id**
“location_id”:”value”

**Location Type**
“location_type”:”value”
Available “location types” are: **HEADQUARTERS, BRANCH, WAREHOUSE, FABRICATION FACILITY, SHOP, SALES OFFICE, REGIONAL OFFICE, CENTRAL DISTRIBUTION CENTER, TRAINING CENTER, SHOWROOM**

**Customer Types**
“types_customers”:”value”
Values parameter can be a comma delimited list of types.  For example: **RESIDENTIAL,COMMERCIAL**

**Project Types**
“types_projects”:”value”
Values parameter can be a comma delimited list of types.  For example: **EDUCATION,SERVICE,CHEMICAL,BREWERY,INDUSTRIAL**

**Vendor Types**
“types_vendors”:”value”
Values parameter can be a comma delimited list of types.  For example: **PVF,HANGER,RENTAL,OFFICE SUPPLIES**


Additional content types are available; please contact HPH if your system requires additional project content. 

## Get Users 
### API – GET an Organization’s User List

This request will be used to get a company’s list of CINX users.  The results of this API will contain the User’s CINX system Id which can be used in other API calls.

URL Pattern:

{api path}/sub/{B2B GUID}/users

Sample:

https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/users

## Get Locations/Addresses
### API – GET an Organization’s Addresses

This request will be used to get a company’s list of addresses.

URL Pattern:

{api path}/sub/{B2B GUID}/addresses

Sample:

https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/addresses 
 
## Get Customer Types
### API – GET an Organization’s Customer Type List

This request will be used to get a company’s list of Customer Type Classifications. 

URL Pattern:

{api path}/sub/{B2B GUID}/customer/types

Sample:

https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/customer/types

## Get Vendor Types
### API – GET an Organization’s Vendor Type List

This request will be used to get a company’s list of Vendor Type Classifications.  

URL Pattern:

{api path}/sub/{B2B GUID}/vendor/types

Sample:

https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/types

## Get Project Types
### API – GET an Organization’s Project Type List

This request will be used to get a company’s list of Project Type Classifications.  

URL Pattern:

{api path}/sub/{B2B GUID}/project/types

Sample:

https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/types

## Get Dispute Reasons
### API – GET an Organization’s Invoice Dispute Reasons List

This request will be used to get a company’s list of Invoice Dispute types. 

URL Pattern:

{api path}/sub/{B2B GUID}/dispute/reasons

Sample:

https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/dispute/reasons

## Get Return Reasons
### API – GET an Organization’s Return Reasons List

This request will be used to get a company’s list of Return Reasons.

URL Pattern:

{api path}/sub/{B2B GUID}/return/reasons

Sample:

https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/return/reasons

## Get Return Actions
### API – GET an Organization’s Return Actions List

This request will be used to get a company’s list of Return Actions.

URL Pattern:

{api path}/sub/{B2B GUID}/return/actions

Sample:

https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/return/actions

