# Org/Company

## Get Org Details
### API – GET Organization Details

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getDetails",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/details",
        "format": "json",
        "start_time": 1564087376.595,
        "total_time": 0.44818305969238,
        "record_count": 1,
        "total_count": 0
    },
    "rows": [
        {
            "is_hidden": "0",
            "is_private": "0",
            "role_primary": "CONTRACTOR",
            "dispute_reasons": [
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "a9d3277e-6417-5458-98a6-08de16fa7c1b",
                    "code": "01-item",
                    "name": "Item Level Issue",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "75ebe888-4649-50f5-9ccb-08ee82f801c6",
                    "code": "02-badterm",
                    "name": "Incorrect Terms",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "bb469ff5-d51d-594a-841b-8b7e07f9dbd9",
                    "code": "03-NoPONum",
                    "name": "PO Number Not Listed",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "fd762a93-44a2-5e6e-9f6a-ddf729b640fa",
                    "code": "04-earlypa",
                    "name": "Early Pay Discount Issue",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "940b41c7-54bd-557e-adff-aa6f6ad9a204",
                    "code": "05-Dup",
                    "name": "Duplicate Invoice",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "edfa8926-272c-5bc3-9b5e-5e07c6d6e9f3",
                    "code": "06-BadBill",
                    "name": "Incorrect Bill To",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "aeffc0e6-22a3-556b-8011-f2ee099f1654",
                    "code": "07-partial",
                    "name": "Order Not Fully Received",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "6dc7b291-1151-5bb6-b774-e9ccde33e254",
                    "code": "08-DelvDat",
                    "name": "Delivery Date Exceeded",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "3edfa19c-9acc-56be-9e41-007d12820d23",
                    "code": "",
                    "name": "Incorrect Freight/Shipping Amount",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "a8ff3ca8-fcee-540b-a3f6-0ad4209a869e",
                    "code": "",
                    "name": "Tax Issue",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "c0fa3333-5548-5a55-bc6c-5fe4107db48d",
                    "code": "",
                    "name": "Late Delivery",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "6ff3c7ce-8eab-5691-855e-8e806761468c",
                    "code": "",
                    "name": "Pricing Agreement Not Applied",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "a7c500bb-873e-5db4-9011-8df4582b2c9e",
                    "code": "",
                    "name": "Project Number Not Listed",
                    "system": "1"
                },
                {
                    "type": "BOM",
                    "checked": "1",
                    "guid": "2180ffff-e9d6-5f2b-9f55-8f1a6c81636e",
                    "code": "",
                    "name": "MISC - No idea",
                    "system": "0"
                },
                {
                    "type": "BOM-ITEM",
                    "checked": "1",
                    "guid": "b568eb4d-a18e-5364-8895-361c51b701e8",
                    "code": "10-price",
                    "name": "Price Issue",
                    "system": "1"
                },
                {
                    "type": "BOM-ITEM",
                    "checked": "1",
                    "guid": "bc8d5c30-b0f4-5dfe-b47c-e5dade652d14",
                    "code": "11-qty",
                    "name": "Quantity Issue",
                    "system": "1"
                },
                {
                    "type": "BOM-ITEM",
                    "checked": "1",
                    "guid": "043479c9-27fa-5652-b914-4e72d5dc51df",
                    "code": "12-noshow",
                    "name": "Item was not received",
                    "system": "1"
                },
                {
                    "type": "BOM-ITEM",
                    "checked": "1",
                    "guid": "1d728ed7-55fd-5298-8397-9019b92deea9",
                    "code": "13-nopo",
                    "name": "Item was not on PO",
                    "system": "1"
                },
                {
                    "type": "BOM-ITEM",
                    "checked": "1",
                    "guid": "0064dd34-2bed-5042-a7c0-79c255c36a45",
                    "code": "14-wrong",
                    "name": "Item is not what was received",
                    "system": "1"
                },
                {
                    "type": "BOM-ITEM",
                    "checked": "1",
                    "guid": "f1f43215-2f00-5fc1-8b1c-a534065b1987",
                    "code": "15-",
                    "name": "Item is not what was ordered",
                    "system": "1"
                },
                {
                    "type": "BOM-ITEM",
                    "checked": "1",
                    "guid": "001399b1-820c-5bda-b7e0-379f4d7c9293",
                    "code": "16-ret",
                    "name": "Item was returned",
                    "system": "1"
                },
                {
                    "type": "BOM-ITEM",
                    "checked": "1",
                    "guid": "79c97b79-509f-5395-b665-f6fcae51722f",
                    "code": "17-damage",
                    "name": "Item was damaged",
                    "system": "1"
                }
            ],
            "return_reasons": [
                {
                    "checked": "1",
                    "guid": "36502c12-9e1b-56c8-a788-323c51b17a1f",
                    "code": "21-damage",
                    "name": "Damaged",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "57d44251-1b29-5882-bedb-ac59fdc6b90a",
                    "code": "22-item",
                    "name": "Wrong Product",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "08968fcd-c36b-5cd0-a057-10c4c9aef48b",
                    "code": "23-mfgwron",
                    "name": "Wrong Product Mfr",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "a4150583-769a-5c77-af41-05bbb5f1ee14",
                    "code": "24-pkg",
                    "name": "Wrong Package Type",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "ebcf01ea-81fc-594d-b9c7-58f9150538e1",
                    "code": "25-delv",
                    "name": "Wrong Delivery Location",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "548bda78-37c7-5657-9399-e2d16c232dd9",
                    "code": "26-nopo",
                    "name": "Not on Purchase Order",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "0defbda7-8084-5b3d-af74-500932b6ac4b",
                    "code": "27-InvPric",
                    "name": "Wrong Invoice Price",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "e8970344-6a5d-5a0f-b2f9-676b2a666505",
                    "code": "28-DelDate",
                    "name": "Delivery Date Exceeded",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "73a22288-eaee-588f-bcc1-020694bc1859",
                    "code": "29-NotReq",
                    "name": "No Longer Required",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "59b504c8-298c-579b-8b63-075593175b4f",
                    "code": "30-Pull",
                    "name": "Pulling Error",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "31e945d1-2bf0-5a36-9a7a-e5b9a1ae1408",
                    "code": "31-spec",
                    "name": "Does not Meet Speciification",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "fb406645-701d-5ce1-8ab0-13700c80eee0",
                    "code": "32-recall",
                    "name": "Mfr Recall",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "16adae8e-61e5-506b-a4d7-ad66e0f70290",
                    "code": "33-warr",
                    "name": "Out of Warranty",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "f3827754-7334-583f-8d40-ce29ace9cd86",
                    "code": "34-na",
                    "name": "Not Specified",
                    "system": "1"
                },
                {
                    "checked": "1",
                    "guid": "e4fd9ceb-16e2-5600-bd93-db3a57e9a62d",
                    "code": "35-misc",
                    "name": "Misc123",
                    "system": "0"
                }
            ],
            "return_actions": [
                {
                    "checked": "1",
                    "guid": "f51cc612-1f47-5f74-b47a-088e2f47d207",
                    "code": "41-replace",
                    "name": "Replace Item",
                    "system": "1",
                    "default": "1"
                },
                {
                    "checked": "1",
                    "guid": "31e27fdd-c231-5521-8536-1cb22493db74",
                    "code": "42-credit",
                    "name": "Credit Account",
                    "system": "1",
                    "default": "0"
                },
                {
                    "checked": "1",
                    "guid": "c15127ad-3a86-513c-9f3e-563f3188d6da",
                    "code": "43-refund",
                    "name": "Refund",
                    "system": "1",
                    "default": "0"
                },
                {
                    "checked": "1",
                    "guid": "47c49af0-fa6f-5b05-9046-6188792f89c7",
                    "code": "44-repair",
                    "name": "Repair Item",
                    "system": "1",
                    "default": "0"
                },
                {
                    "checked": "1",
                    "guid": "4b29f1bb-2b8c-581b-ab4f-3d83c93dc3d3",
                    "code": "45",
                    "name": "Misc",
                    "system": "0",
                    "default": "0"
                },
                {
                    "checked": "1",
                    "guid": "cfd091d8-8096-565d-8154-0c026116ace7",
                    "code": "46",
                    "name": "Miscq12",
                    "system": "0",
                    "default": "0"
                }
            ],
            "date_created": "2017-10-20",
            "date_modified": "2019-07-03",
            "creator": {
                "names": {
                    "first": "Will",
                    "middle": "",
                    "last": "Stone",
                    "suffix": ""
                },
                "cinx_id": {
                    "type": "USER",
                    "domain": "users",
                    "id": "185aabe1-3487-5f59-9ad5-c577a76bd392"
                }
            },
            "names": {
                "primary": "WTS Mechanical -DEV",
                "alternate": null,
                "short": null,
                "previous": null
            },
            "addresses": [
                {
                    "guid": "8c66255d-e173-532b-bb12-73943006bf80",
                    "type": "SHIPPING",
                    "desc": "HQ",
                    "address1": "995 Industrial Park Rd",
                    "address2": "",
                    "address3": "",
                    "country": "USA",
                    "city": "Littleton",
                    "state": "NH",
                    "postal_code": "03561",
                    "latitude": "",
                    "longitude": ""
                },
                {
                    "guid": "771bd90c-1e95-5538-b552-01621ac59a87",
                    "type": "BILLING",
                    "desc": "WTS Mech - Billing Address",
                    "address1": "PO Box 320",
                    "address2": "",
                    "address3": "",
                    "country": "USA",
                    "city": "Littleton",
                    "state": "NH",
                    "postal_code": "03561",
                    "latitude": "",
                    "longitude": ""
                },
                {
                    "type": "SHIPPING",
                    "desc": "Littleton Fab Shop",
                    "address1": "995 Industrial Park Road",
                    "address2": "Building 2",
                    "address3": "Suite 3",
                    "country": "USA",
                    "city": "Littleton",
                    "state": "NH",
                    "postal_code": "03561",
                    "latitude": "",
                    "longitude": "",
                    "guid": "4e1877b6-b485-5be6-9544-80bd2749d5e2"
                },
                {
                    "type": "SHIPPING",
                    "desc": "Boston Fab Shop",
                    "address1": "745 Atlantic Avenue",
                    "address2": "",
                    "address3": "",
                    "country": "USA",
                    "city": "Boston",
                    "state": "MA",
                    "postal_code": "02111",
                    "latitude": "",
                    "longitude": "",
                    "guid": "efef4e70-72b6-5ea1-bfac-15e1eb372142"
                }
            ],
            "contact_points": {
                "emails": [],
                "faxes": [],
                "phones": [
                    {
                        "type": "OFFICE",
                        "value": "6034440820"
                    }
                ],
                "instant_messengers": [],
                "urls": [
                    {
                        "type": "PRIMARY",
                        "value": "http://www.cinx.com",
                        "name": ""
                    }
                ],
                "social_sites": []
            },
            "location": {
                "location_id": null,
                "types": [],
                "hours": [],
                "holidays": [],
                "emergency_info": null
            },
            "marketing": {
                "desc": null,
                "tag_line": null,
                "year_founded": "2012",
                "logo_url": "http://api.dev.cinx.biz/entity/image/orgs/org-0001-4030?url=http://cdn.dev.cinx.biz/assets/org-0001-4030/logo/org-0001-4030_logo_1.PNG&type=ORG"
            },
            "logo_raw_url": "http://cdn.dev.cinx.biz/assets/org-0001-4030/logo/org-0001-4030_logo_1.PNG",
            "types": {
                "customers": "Industrial,Hospitality",
                "vendors": "PVF,Fixtures,Equipment",
                "projects": "Industrial,Healthcare"
            },
            "market_segments": [
                {
                    "name": "Contractors",
                    "segments": [
                        {
                            "id": "1",
                            "name": "Plumbing/Mechanical",
                            "desc": "Plumbing & Mechanical"
                        }
                    ],
                    "cinx_id": {
                        "type": "MARKET-SEGMENT",
                        "domain": "references",
                        "id": "mkt-seg-contractors"
                    }
                }
            ],
            "products": [],
            "ids": [],
            "parent": {
                "type": null,
                "domain": null,
                "id": null
            },
            "cinx_id": {
                "type": "ORG",
                "domain": "orgs",
                "id": "org-0001-4030"
            }
        }
    ]
}
```

This request will be used to get the company’s CINX organization details.

URL Pattern:

**{api path}/sub/{B2B GUID}/org/details**

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/details`


## Modify Org
### API – Modify Organization Details

This request will be used to modify an organization’s details.

URL Pattern:

**{api path}/sub/{B2B Id GUID}/modify/org?values={JSON Structure}**

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Organization JSON Structures** section of this document for a listing of the available JSON structures.

Sample:

Dev sample using HPH Account:

`http://api.dev.cinx.biz/sub/83d8ba34-ecf1-59ab-1013-0ba2603adb36/modify/org?values={"types_customers":"Residential,Commercial,Industrial"}`


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
“add_address”:[{”address_type”:”type value”,”address1”: “value”,”address2”: “value”,”address3”: “value”,”city”: “value”,”state”: “value”,”postal_code”: “value”,”country”: “value”,”latitude”: “value”, ”longitude”: “value”}]
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

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getUsers",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/users",
        "format": "json",
        "start_time": 1564087635.685,
        "total_time": 0.43664407730103,
        "record_count": 2,
        "total_count": 0
    },
    "rows": [
        {
            "id": "4a23ff84-9d61-5ab3-95c9-3870cb2727bd",
            "name": "Karl Stone",
            "last_first": "Stone, Karl",
            "email": "karlstone@cinx.com"
        },
        {
            "id": "185aabe1-3487-5f59-9ad5-c577a76bd392",
            "name": "Will Stone",
            "last_first": "Stone, Will",
            "email": "willstone@cinx.com"
        }
    ]
}
```

This request will be used to get a company’s list of CINX users.  The results of this API will contain the User’s CINX system Id which can be used in other API calls.

URL Pattern:

{api path}/sub/{B2B GUID}/users

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/users`

## Get Locations/Addresses
### API – GET an Organization’s Addresses

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getAddresses",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/addresses",
        "format": "json",
        "start_time": 1564087867.862,
        "total_time": 0.4335470199585,
        "record_count": 4,
        "total_count": 0
    },
    "rows": [
        {
            "guid": "8c66255d-e173-532b-bb12-73943006bf80",
            "type": "SHIPPING",
            "desc": "HQ",
            "address1": "995 Industrial Park Rd",
            "address2": "",
            "address3": "",
            "country": "USA",
            "city": "Littleton",
            "state": "NH",
            "postal_code": "03561",
            "latitude": "",
            "longitude": "",
            "default": true
        },
        {
            "guid": "771bd90c-1e95-5538-b552-01621ac59a87",
            "type": "BILLING",
            "desc": "WTS Mech - Billing Address",
            "address1": "PO Box 320",
            "address2": "",
            "address3": "",
            "country": "USA",
            "city": "Littleton",
            "state": "NH",
            "postal_code": "03561",
            "latitude": "",
            "longitude": "",
            "default": true
        },
        {
            "guid": "4e1877b6-b485-5be6-9544-80bd2749d5e2",
            "type": "SHIPPING",
            "desc": "Littleton Fab Shop",
            "address1": "995 Industrial Park Road",
            "address2": "Building 2",
            "address3": "Suite 3",
            "country": "USA",
            "city": "Littleton",
            "state": "NH",
            "postal_code": "03561",
            "latitude": "",
            "longitude": ""
        },
        {
            "guid": "efef4e70-72b6-5ea1-bfac-15e1eb372142",
            "type": "SHIPPING",
            "desc": "Boston Fab Shop",
            "address1": "745 Atlantic Avenue",
            "address2": "",
            "address3": "",
            "country": "USA",
            "city": "Boston",
            "state": "MA",
            "postal_code": "02111",
            "latitude": "",
            "longitude": ""
        }
    ]
}
```

This request will be used to get a company’s list of addresses.

URL Pattern:

{api path}/sub/{B2B GUID}/addresses

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/org/addresses`
 
## Get Customer Types
### API – GET an Organization’s Customer Type List

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getOrgCustomerTypes",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/customer/types",
        "format": "json",
        "start_time": 1564087975.636,
        "total_time": 0.46769309043884,
        "record_count": 2,
        "total_count": 0
    },
    "rows": [
        "Industrial",
        "Hospitality"
    ]
}
```

This request will be used to get a company’s list of Customer Type Classifications. 

URL Pattern:

{api path}/sub/{B2B GUID}/customer/types

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/customer/types`

## Get Vendor Types
### API – GET an Organization’s Vendor Type List

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getOrgCustomerTypes",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/types",
        "format": "json",
        "start_time": 1564088074.067,
        "total_time": 0.43536305427551,
        "record_count": 3,
        "total_count": 0
    },
    "rows": [
        "PVF",
        "Fixtures",
        "Equipment"
    ]
}
```

This request will be used to get a company’s list of Vendor Type Classifications.  

URL Pattern:

{api path}/sub/{B2B GUID}/vendor/types

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/types`

## Get Project Types
### API – GET an Organization’s Project Type List

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getOrgCustomerTypes",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/types",
        "format": "json",
        "start_time": 1564088160.065,
        "total_time": 0.43146705627441,
        "record_count": 2,
        "total_count": 0
    },
    "rows": [
        "Industrial",
        "Healthcare"
    ]
}
```

This request will be used to get a company’s list of Project Type Classifications.  

URL Pattern:

{api path}/sub/{B2B GUID}/project/types

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/project/types`

## Get Dispute Reasons
### API – GET an Organization’s Invoice Dispute Reasons List

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getOrgReasonActions",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/dispute/reasons",
        "format": "json",
        "start_time": 1564088249.983,
        "total_time": 0.44007587432861,
        "record_count": 22,
        "total_count": 0
    },
    "rows": [
        {
            "guid": "a9d3277e-6417-5458-98a6-08de16fa7c1b",
            "code": "01-item",
            "name": "Item Level Issue"
        },
        {
            "guid": "75ebe888-4649-50f5-9ccb-08ee82f801c6",
            "code": "02-badterm",
            "name": "Incorrect Terms"
        },
        {
            "guid": "bb469ff5-d51d-594a-841b-8b7e07f9dbd9",
            "code": "03-NoPONum",
            "name": "PO Number Not Listed"
        },
        {
            "guid": "fd762a93-44a2-5e6e-9f6a-ddf729b640fa",
            "code": "04-earlypa",
            "name": "Early Pay Discount Issue"
        },
        {
            "guid": "940b41c7-54bd-557e-adff-aa6f6ad9a204",
            "code": "05-Dup",
            "name": "Duplicate Invoice"
        },
        {
            "guid": "edfa8926-272c-5bc3-9b5e-5e07c6d6e9f3",
            "code": "06-BadBill",
            "name": "Incorrect Bill To"
        },
        {
            "guid": "aeffc0e6-22a3-556b-8011-f2ee099f1654",
            "code": "07-partial",
            "name": "Order Not Fully Received"
        },
        {
            "guid": "6dc7b291-1151-5bb6-b774-e9ccde33e254",
            "code": "08-DelvDat",
            "name": "Delivery Date Exceeded"
        },
        {
            "guid": "3edfa19c-9acc-56be-9e41-007d12820d23",
            "code": "",
            "name": "Incorrect Freight/Shipping Amount"
        },
        {
            "guid": "a8ff3ca8-fcee-540b-a3f6-0ad4209a869e",
            "code": "",
            "name": "Tax Issue"
        },
        {
            "guid": "c0fa3333-5548-5a55-bc6c-5fe4107db48d",
            "code": "",
            "name": "Late Delivery"
        },
        {
            "guid": "6ff3c7ce-8eab-5691-855e-8e806761468c",
            "code": "",
            "name": "Pricing Agreement Not Applied"
        },
        {
            "guid": "a7c500bb-873e-5db4-9011-8df4582b2c9e",
            "code": "",
            "name": "Project Number Not Listed"
        },
        {
            "guid": "2180ffff-e9d6-5f2b-9f55-8f1a6c81636e",
            "code": "",
            "name": "MISC - No idea"
        },
        {
            "guid": "b568eb4d-a18e-5364-8895-361c51b701e8",
            "code": "10-price",
            "name": "Price Issue"
        },
        {
            "guid": "bc8d5c30-b0f4-5dfe-b47c-e5dade652d14",
            "code": "11-qty",
            "name": "Quantity Issue"
        },
        {
            "guid": "043479c9-27fa-5652-b914-4e72d5dc51df",
            "code": "12-noshow",
            "name": "Item was not received"
        },
        {
            "guid": "1d728ed7-55fd-5298-8397-9019b92deea9",
            "code": "13-nopo",
            "name": "Item was not on PO"
        },
        {
            "guid": "0064dd34-2bed-5042-a7c0-79c255c36a45",
            "code": "14-wrong",
            "name": "Item is not what was received"
        },
        {
            "guid": "f1f43215-2f00-5fc1-8b1c-a534065b1987",
            "code": "15-",
            "name": "Item is not what was ordered"
        },
        {
            "guid": "001399b1-820c-5bda-b7e0-379f4d7c9293",
            "code": "16-ret",
            "name": "Item was returned"
        },
        {
            "guid": "79c97b79-509f-5395-b665-f6fcae51722f",
            "code": "17-damage",
            "name": "Item was damaged"
        }
    ]
}
```

This request will be used to get a company’s list of Invoice Dispute types. 

URL Pattern:

{api path}/sub/{B2B GUID}/dispute/reasons

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/dispute/reasons`

## Get Return Reasons
### API – GET an Organization’s Return Reasons List

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getOrgReasonActions",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/return/reasons",
        "format": "json",
        "start_time": 1564088351.98,
        "total_time": 0.42213296890259,
        "record_count": 15,
        "total_count": 0
    },
    "rows": [
        {
            "guid": "36502c12-9e1b-56c8-a788-323c51b17a1f",
            "code": "21-damage",
            "name": "Damaged"
        },
        {
            "guid": "57d44251-1b29-5882-bedb-ac59fdc6b90a",
            "code": "22-item",
            "name": "Wrong Product"
        },
        {
            "guid": "08968fcd-c36b-5cd0-a057-10c4c9aef48b",
            "code": "23-mfgwron",
            "name": "Wrong Product Mfr"
        },
        {
            "guid": "a4150583-769a-5c77-af41-05bbb5f1ee14",
            "code": "24-pkg",
            "name": "Wrong Package Type"
        },
        {
            "guid": "ebcf01ea-81fc-594d-b9c7-58f9150538e1",
            "code": "25-delv",
            "name": "Wrong Delivery Location"
        },
        {
            "guid": "548bda78-37c7-5657-9399-e2d16c232dd9",
            "code": "26-nopo",
            "name": "Not on Purchase Order"
        },
        {
            "guid": "0defbda7-8084-5b3d-af74-500932b6ac4b",
            "code": "27-InvPric",
            "name": "Wrong Invoice Price"
        },
        {
            "guid": "e8970344-6a5d-5a0f-b2f9-676b2a666505",
            "code": "28-DelDate",
            "name": "Delivery Date Exceeded"
        },
        {
            "guid": "73a22288-eaee-588f-bcc1-020694bc1859",
            "code": "29-NotReq",
            "name": "No Longer Required"
        },
        {
            "guid": "59b504c8-298c-579b-8b63-075593175b4f",
            "code": "30-Pull",
            "name": "Pulling Error"
        },
        {
            "guid": "31e945d1-2bf0-5a36-9a7a-e5b9a1ae1408",
            "code": "31-spec",
            "name": "Does not Meet Speciification"
        },
        {
            "guid": "fb406645-701d-5ce1-8ab0-13700c80eee0",
            "code": "32-recall",
            "name": "Mfr Recall"
        },
        {
            "guid": "16adae8e-61e5-506b-a4d7-ad66e0f70290",
            "code": "33-warr",
            "name": "Out of Warranty"
        },
        {
            "guid": "f3827754-7334-583f-8d40-ce29ace9cd86",
            "code": "34-na",
            "name": "Not Specified"
        },
        {
            "guid": "e4fd9ceb-16e2-5600-bd93-db3a57e9a62d",
            "code": "35-misc",
            "name": "Misc123"
        }
    ]
}
```

This request will be used to get a company’s list of Return Reasons.

URL Pattern:

{api path}/sub/{B2B GUID}/return/reasons

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/return/reasons`

## Get Return Actions
### API – GET an Organization’s Return Actions List

> The above code returns JSON structured like this:

```json
{
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getOrgReasonActions",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/return/actions",
        "format": "json",
        "start_time": 1564088448.645,
        "total_time": 0.43082904815674,
        "record_count": 6,
        "total_count": 0
    },
    "rows": [
        {
            "guid": "f51cc612-1f47-5f74-b47a-088e2f47d207",
            "code": "41-replace",
            "name": "Replace Item"
        },
        {
            "guid": "31e27fdd-c231-5521-8536-1cb22493db74",
            "code": "42-credit",
            "name": "Credit Account"
        },
        {
            "guid": "c15127ad-3a86-513c-9f3e-563f3188d6da",
            "code": "43-refund",
            "name": "Refund"
        },
        {
            "guid": "47c49af0-fa6f-5b05-9046-6188792f89c7",
            "code": "44-repair",
            "name": "Repair Item"
        },
        {
            "guid": "4b29f1bb-2b8c-581b-ab4f-3d83c93dc3d3",
            "code": "45",
            "name": "Misc"
        },
        {
            "guid": "cfd091d8-8096-565d-8154-0c026116ace7",
            "code": "46",
            "name": "Miscq12"
        }
    ]
}
```

This request will be used to get a company’s list of Return Actions.

URL Pattern:

{api path}/sub/{B2B GUID}/return/actions

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/return/actions`

