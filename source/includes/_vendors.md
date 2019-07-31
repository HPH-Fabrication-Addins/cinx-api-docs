# Vendors

## Vendor Definition
### CINX Object Defintion - Vendor

Vendor is a generic term that refers to any organization that sells/distributes products or services that are consumed by a customer. Vendors refer to different organization types within the construction vertical market.

For contractors on the CINX platform, a Vendor is a Wholesale Distributor or other entities that provide products or services.  As a web-based platform CINX has the ability for contractors and distributors to connect with one another if they are both already members of the CINX site. Similar to LinkedIn and Facebook, a request is sent by the requesting party to create a relationship whereby CINX activities and transactions can be shared between the two companies.

When a relationship between the two parties is created, CINX creates a Commerce GUID that links the two parties. This GUID is the key that allows for the storage of important transaction parameters that are required to deliver and process transactions. It is therefore also used by the API as a URL parameter when fetching and updating relationship data.

CINX also has the ability for a contractor to create a **Private** vendor.  This is a vendor that is not a member of the CINX site.  A private vendor is unique to the contractor and will still be linked using a Commerce GUID.

**Dependencies and Business Rules**
* Must be created by a CINX user linked to an active CINX company.
* The customer can assign an account number for the vendor
* The vendor can assign an account number for the customer
* Vendor users can be assigned to customers
* Different branch locations can be loaded for selection by contractors

**Supported API Services**
* Get a List of Vendors
* Get a Vendor
* Get a Vendor Template
* Get a Vendor Number
* Create a Vendor
* Modify a Vendor
* Get Vendor Transactions
* Get Vendor Branches
* Get Vendor Contacts

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

This endpoint will be used to get a list of the organization's vendors. 

URL Pattern: **{api path}/{api_version}sub/{api_token}/vendors**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendors`

HTTP Method: `GET`

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
    "rows": [
        {  GET PICTURE
        }
    ]
}
```

This endpoint will be used to get the details of a specific vendor using the CINX Commerce Id.

URL Pattern: **{api path}/{api_version}sub/{api_token}/vendor/{cinx_commerce_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/512d5a2f-1d6c-21ca-9b97-9299ac9c802a`

HTTP Method: `GET`

## Get Vendor Template
### API Endpoint - Get a Vendor Template

This endpoint will be used to get a CINX Template for a vendor.

URL Pattern: **{api path}/{api_version}sub/{api_token}/template/vendor**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/vendor`

HTTP Method: `GET`

## Vendor Template Fields
### Definition of the Vendor Template's Fields

The table below defines the fields within the template.

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
This request will be used to get a value to be used in the number field of a new vendor.

**Notes** 
* The response will contain a new value ONLY if the company has turned on the auto-numbering feature in CINX.


URL Pattern: **{api path}/{api_version}sub/{api_token}/auto-number/vendor**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/auto-number/vendor`

HTTP Method: `GET`


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

This endpoint will be used to insert a new private vendor for an organization.

**Notes**

* A CINX Template is available that documents the available fields that can be populated.
* A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}sub/{api_token}/req/partner/exec/cinx/json-vendor-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-vendor-import?body=json`

HTTP Method: `POST`

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

This endpoint will be used to modify a vendor.

**Notes**

* A CINX Template is available that documents the available fields that can be populated.
* A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}sub/{api_token}/req/partner/exec/cinx/json-vendor-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-vendor-import?body=json`

HTTP Method: `PUT`

## Vendor JSON Structures
### CINX Vendor JSON Structures

The JSON structures shown below can be used in API calls to **Create** or **Modify** a Vendor.
