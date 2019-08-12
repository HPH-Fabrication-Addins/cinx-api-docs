# Vendors

## Vendor Definition
### CINX Object Defintion - Vendor

Vendor is a generic term that refers to any organization that sells/distributes products or services that are consumed by a customer. Vendors refer to different organization types within the construction vertical market.

For contractors on the CINX platform, a Vendor is a Wholesale Distributor or other entities that provide products or services.  As a web-based platform CINX has the ability for contractors and distributors to connect with one another if they are both already members of the CINX site. Similar to LinkedIn and Facebook, a request is sent by the requesting party to create a relationship whereby CINX activities and transactions can be shared between the two companies.

When a relationship between the two parties is created, CINX creates a Commerce GUID that links the two parties. This GUID is the key that allows for the storage of important transaction parameters that are required to deliver and process transactions. It is therefore also used by the API as a URL parameter when fetching and updating relationship data.

CINX also has the ability for a contractor to create a **Private** vendor.  This is a vendor that is not a member of the CINX site.  A private vendor is unique to the contractor and will still be linked using a Commerce GUID.

**Dependencies and Business Rules**

  - Must be created by a CINX user linked to an active CINX company
  - The customer can assign an account number for the vendor
  - The vendor can assign an account number for the customer
  - Vendor users can be assigned to customers
  - Different branch locations can be loaded for selection by contractors

**Supported API Services**

  - [Get a List of Vendors](#get-vendor-list)
  - [Get a Vendor](#get-vendor)
  - [Get a Vendor Template](#get-vendor-template)
  - [Get a Vendor Number](#get-vendor-number)
  - [Create a Vendor](#create-vendor)
  - [Modify a Vendor](#modify-vendor)
  - [Get Vendor Transactions](#vendor-transactions)
  - Get Vendor Branches
  - Get Vendor Contacts

## Get Vendor List
### API Endpoint - Get List of Vendors

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

cinxApi.getVendors(cinx_api_token)
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
            "cinx_commerce_guid": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f",
            "name": "PVF Supply",
            "number": "P-45677",
            "status": "A",
            "type": "PVF",
            "address": {
                "type": "SHIPPING",
                "address1": "Address 001",
                "address2": "",
                "address3": "",
                "city": "City 001",
                "state": "AL",
                "postal_code": "00122",
                "country": "USA"
            }
        }
    ]
}
```
 `GET`

This endpoint will be used to get a list of the organization's vendors. 

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendors**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendors`

## Get Vendor
### API Endpoint - Get a Vendor

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

cinxApi.getVendorDetails(cinx_api_token, vendor_id)
    .then(function(response) {
        console.log(response);
    });
```

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [{
        "cinx_commerce_guid": "de0cf849-6f7b-5df6-9ae9-f924659f2d25",
        "number": "CXV101",
        "name": "ABS Supply Company",
        "short_name": null,
        "description": "Full Service PVF Distributor.",
        "type": null,
        "web_site": null,
        "logo": "http://cdn.dev.cinx.biz/assets/org-0000-5814/logo/org-0000-5814_logo_1.jpg",
        "status": "A",
        "location": {
            "number": null,
            "type": null,
            "emergency_info": "Call night watchman at 314.555.1452"
        },
        "terms": {
            "account_number": "CX101",
            "payment_days_type": "Number of Days",
            "payment_due_days": 15,
            "late_fee_percent": 1,
            "discount_days_type": null,
            "discount_days": 0,
            "discount_percent": 0
        },
        "accounting_defaults": {
            "cinx_material_cost_code_guid": null,
            "material_cost_code_name": null,
            "cinx_category_guid": null,
            "category_name": null,
            "cinx_tax_group_guid": null,
            "tax_group_name": null,
            "gl_account": null
        },
        "addresses": [{
            "type": "SHIPPING",
            "address1": "1533 Delmar Avenue",
            "address2": "",
            "address3": "",
            "country": "USA",
            "city": "St. Louis",
            "state": "AL",
            "postal_code": "63103",
            "description": "1533 Delmar Avenue"
        }],
        "phone_numbers": [{
            "type": "OFFICE",
            "number": "314.555.3200"
        }],
        "fax_numbers": [],
        "email_addresses": [{
            "type": "CORPORATE",
            "address": "sales@abssupply1.com"
        }],
        "id_numbers": []
    }]
}
```
 `GET`

This endpoint will be used to get the details of a specific vendor using the CINX Commerce Id.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/vendor/{cinx_commerce_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/512d5a2f-1d6c-21ca-9b97-9299ac9c802a`

## Get Vendor Template
### API Endpoint - Get a Vendor Template

```json
{
    "response": {},
    "rows": [
        {
           "doc_info": {},
           "template": {
                "cinx_guid": null,
                "number": null,
                "name": null,
                "short_name": null,
                "description": null,
                "type": null,
                "web_site": null,
                "status": "A",
                "location": {
                    "number": null,
                    "type": null,
                    "emergency_info": null
                },
                "terms": {
                    "account_number": null,
                    "payment_days_type": null,
                    "payment_due_days": null,
                    "late_fee_percent": null,
                    "discount_days_type": null,
                    "discount_days": null,
                    "discount_percent": null
                },
                "accounting_defaults": {
                    "cinx_material_cost_code_guid": null,
                    "material_cost_code_name": null,
                    "cinx_category_guid": null,
                    "category_name": null,
                    "cinx_tax_group_guid": null,
                    "tax_group_name": null,
                    "gl_account": null
                },
                "addresses": [
                    {
                        "type": null,
                        "address1": null,
                        "address2": null,
                        "address3": null,
                        "city": null,
                        "state": null,
                        "postal_code": null,
                        "country": "USA"
                    }
                ],
                "phone_numbers": [
                    {
                        "type": null,
                        "number": null
                    }
                ],
                "fax_numbers": [
                    {
                        "type": null,
                        "number": null
                    }
                ],
                "email_addresses": [
                    {
                        "type": null,
                        "address": null
                    }
                ],
                "id_numbers": [
                    {
                        "type": null,
                        "number": null
                    }
                ]
            },
            "field_options": {},
            "api_calls": {}
        }
    ]
}
```
`GET`

This endpoint will be used to get a CINX Template for a vendor.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/template/vendor**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/vendor`


The table below defines the input fields within the template.

**TEMPLATE FIELDS**

Name | Data Type | Required | Default | Note
----- | ----- | ----- | ----- | -----
cinx_guid | String (GUID Format) | POST = No; Put = Yes |  | CINX System Id.
number | String | No |  | Public number for the object.
name | String | Yes |  | Full name of the vendor.
short_name | String | No |  | Short or abbreviated name of the vendor.
description | String | No |  | Description of the vendor.
type | String | No |  | Organization-defined type assigned to the vendor.
web_site | String | No |  | Primary web site address of the vendor.
status | String | Yes | A | Status of the vendor.
location.number | String | No |  | Number identifying the vendor's location.
location.type | String | No |  | Type of location.  Template has a list of optional values.
location.emergency_info | String | No |  | Information for contacting the vendor in-case of an emergency.
terms.account_number | String | No |  | Vendor's system number for the customer.
terms.payment_days_type | String | No |  | Vendor's payment terms days type.
terms.payment_due_days | Real | No |  | Vendor's payment terms due days.
terms.late_fee_percent | Real | No |  | Vendor's payment terms late payment fee percentage.
terms.discount_days_type | String | No |  | Vendor's payment terms early pay discount days type.
terms.discount_days | Real | No |  | Vendor's payment terms early pay discount days.
terms.discount_percent | Real | No |  | Vendor's payment terms early pay discount percentage.
accounting_defaults.cinx_material_cost_code_guid | String (GUID Format) | No |  | Default CINX Id for the Material Cost Code assigned to the vendor.
accounting_defaults.material_cost_code_name | String | No |  | Default name for the Material Cost Code assigned to the vendor.
accounting_defaults.cinx_category_guid | String (GUID Format) | No |  | Default CINX Id for the Category assigned to the vendor.
accounting_defaults.category_name | String | No |  | Default name for the Category assigned to the vendor.
accounting_defaults.cinx_tax_group_guid | String (GUID Format) | No |  | Default CINX Id for the Tax Group assigned to the vendor
accounting_defaults.tax_group_name | String | No |  | Default name for the Tax Group assigned to the vendor.
accounting_defaults.gl_account | String | No |  | Default name for the General Ledger account assigned to the vendor.
addresses.type | String | No |  | Type of vendor location address. Template has a list of optional values.
addresses.address1 | String | No |  | Address 1 value for the vendor location.
addresses.address2 | String | No |  | Address 2 value for the vendor location.
addresses.address3 | String | No |  | Address 3 value for the vendor location.
addresses.city | String | No |  | City value for the vendor location.
addresses.state | String | No |  | State value for the vendor location. Two-character alpha abbreviation.
addresses.postal_code | String | No |  | Postal/Zip Code value for the vendor location.
addresses.country | String | No | USA | Country value for the vendor location. Three-character alpha abbreviation.
phone_numbers.type | String | No |  | Type of phone number. Template has a list of optional values.
phone_numbers.number | String | No |  | Value of the phone number.
fax_numbers.type | String | No |  | Type of fax number. Template has a list of optional values.
fax_numbers.number | String | No |  | Value of the fax number.
email_addresses.type | String | No |  | Type of email address. Template has a list of optional values.
email_addresses.address | String | No |  | Email address.
id_numbers.type | String | No |  | Type of Id number. Template has a list of optional values.
id_numbers.number | String | No |  | Id number value.

## Get Vendor Number
### API Endpoint - Get a New Vendor Number

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "vendor": "V-0001"
        }
    ]
}
```
 `GET`

This endpoint will be used to get a value to be used in the number field of a new vendor.

**Notes** 

- The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/auto-number/vendor**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/vendor`

## Create Vendor
### API Endpoint - Create a New Vendor

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"name_primary":"${vName}","vendor_id":"${vID}","vendor_status":"${vStatus}"}`;

cinxApi.postNewVendor(cinx_api_token, values)
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
                "type": "ORG",
                "domain": "orgs",
                "id": "org-0001-4246"
            }
        },
        {
            "cinx_id": {
                "type": "ORG-COMMERCE",
                "domain": "orgs",
                "id": "3dba458d-e000-5756-abde-fd81b2b52e54"
            }
        }
    ]
}
```
 `POST`

This endpoint will be used to insert a new private vendor for an organization.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-vendor-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-vendor-import?body=json`

## Modify Vendor
###API Endpoint - Modify a Vendor

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('http://api.dev.cinx.biz', '');

var values = `{"name_primary":"${vName}","vendor_id":"${vID}","vendor_status":"${vStatus}"}`;

cinxApi.modifyVendor(cinx_api_token, vendor_id, values)
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
                "type": "ORG",
                "domain": "orgs",
                "id": "org-0001-4245"
            }
        },
        {
            "cinx_id": {
                "type": "ORG-COMMERCE",
                "domain": "orgs",
                "id": "117556cd-c16b-5724-97fd-f9b644ee0b02"
            }
        }
    ]
}
```
`PUT`

This endpoint will be used to modify a vendor.

**Notes**

  - A CINX Template is available that documents the available fields that can be populated.
  - A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}/sub/{api_token}/partner/exec/cinx/json-vendor-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-vendor-import?body=json`
