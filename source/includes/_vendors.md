# Vendors

## Introduction
### CINX Vendor Introduction

For contractors on the CINX platform, a Vendor is a Wholesale Distributor or other entities that provide products or services.  As a web-based platform CINX has the ability for contractors and distributors to connect with one another if they are both already members of the CINX site.  Similar to LinkedIn and Facebook, a request is sent by the requesting party to create a relationship whereby CINX activities and transactions can be shared between the two companies.

As shown in the graphic, a simple click of the Add As Vendor button will send a request to the Vendor to accept the contractor’s request.

When a relationship between the two parties is created CINX creates a Commerce GUID that links the two parties.  This GUID is the key that allows for the storage of important transaction parameters that are required to deliver and process transactions.

It is therefore also used by the API as a URL parameter when fetching and updating relationship data.

CINX also has the ability for a contractor to create a **Private** vendor.  This is a vendor that is not a member of the CINX site.  A private vendor is unique to the contractor and will still be linked using a Commerce GUID.

## Get Vendor List
### API – GET Vendor List

This request will be used to get a list of the company’s Vendors from CINX.

URL Pattern:

{api path}/sub/{B2B Id GUID}/vendors

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/vendors`

## Get Vendor Details
### API – GET Vendor Details – using CINX Commerce GUID

This request will be used to get the details of a vendor.

URL Pattern:

{api path}/sub/{B2B Id GUID}/vendor/{commerce guid}/details

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/vendor/512d5a2f-1d6c-21ca-9b97-9299ac9c802a/details`

## Create Vendor
### API – PUT New Vendor

This request will be used to insert a new private vendor for an organization.

URL Pattern:

{api path}/sub/{B2B Id GUID}/private/vendor/create?values={JSON Structure}

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Vendor JSON Structures** section of this document for a listing of the available JSON structures.

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/private/vendor/create?values={%22name_primary%22:%22Hilti%22,%22vendor_id%22:%22H123%22,%22vendor_type%22:%22Hardware%22,%22add_address%22:{%22type%22:%22Mailing%22,%22address1%22:%22Route%203%22,%22address2%22:%22Building%204%22,%22address3%22:%22Suite%20G%22,%22city%22:%22Woburn%22,%22state%22:%22MA%22,%22postal_code%22:%2201234%22,%22country%22:%22USA%22,%22latitude%22:%22%22,%22longitude%22:%22%22}}`

## Modify Vendor
### API – Modify a Vendor

API – Modify a Vendor
This request will be used to modify a private vendor for an organization.

URL Pattern:

{api path}/sub/{B2B Id GUID}/private/vendor/{commerce guid}/modify?values={JSON Structure}

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Vendor JSON Structures** section of this document for a listing of the available JSON structures.

Sample:

`http://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/private/vendor/org-0001-4221/modify?values={"name_primary":"Hilti-5","vendor_id":"H125"}`

## Vendor JSON Structures
### CINX Vendor JSON Structures

The JSON structures shown below can be used in API calls to **Create** or **Modify** a Vendor.

If the structure is an array, all elements of the array must be submitted.

**Vendor Number/Id**
“vendor_id”:”value”

**Vendor Status**
“vendor_status”:”value”
Available options are: **A, I**
Option Definitions: **A=Active, I=Inactive**
Default value: **A**

**Vendor Type** (each org can define a set list of vendor types to be used to classify their vendors)
“vendor_type”:”value”

The options shown below are for creating or modifying **Private** Vendors

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

**Location Id**
“location_id”:”value”

**Location Type**
“location_type”:”value”
Available “location types” are: **HEADQUARTERS, BRANCH, WAREHOUSE, FABRICATION FACILITY, SHOP, SALES OFFICE, REGIONAL OFFICE, CENTRAL DISTRIBUTION CENTER, TRAINING CENTER, SHOWROOM**





