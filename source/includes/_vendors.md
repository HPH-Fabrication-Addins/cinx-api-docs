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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getVendors",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendors",
        "format": "json",
        "start_time": 1564234550.414,
        "total_time": 0.45171499252319,
        "record_count": 5,
        "total_count": 5
    },
    "rows": [
        {
            "cinx_id": {
                "type": "ORG",
                "domain": "orgs",
                "id": "org-0000-7108"
            },
            "name": "Ferguson Testing July 2015",
            "address": {
                "address1": "Address 001",
                "address2": "",
                "address3": "",
                "city": "City 001",
                "state": "AL",
                "postal_code": "00122",
                "country": "USA",
                "desc": "new address 001",
                "type": "SHIPPING",
                "latitude": "",
                "longitude": "",
                "guid": "18568568-b8a2-5575-a525-354cf99abbe1"
            },
            "vendor_id": "99999",
            "vendor_status": "A",
            "vendor_type": "PVF",
            "customer_id": "ABCD1234",
            "availableUsers": [],
            "users": [
                {
                    "role": "User",
                    "is_primary": "0",
                    "names": {
                        "first": "David",
                        "middle": "",
                        "last": "Farnsworth",
                        "suffix": ""
                    },
                    "contact_points": {
                        "emails": [],
                        "faxes": [],
                        "phones": [],
                        "instant_messengers": [],
                        "urls": [],
                        "social_sites": []
                    },
                    "cinx_id": {
                        "type": "USER",
                        "domain": "users",
                        "id": "e9bf728d-021c-5644-b934-43c193751f2d"
                    }
                }
            ],
            "attributes": [
                {
                    "name": "discount_days_type",
                    "value": "Number of Days",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "discount_days",
                    "value": "10",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "discount_percent",
                    "value": "1.5",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "due_days",
                    "value": "30",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "late_fee_percent",
                    "value": "1.0",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "payment_days_type",
                    "value": "Number of Days",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "expense_account",
                    "value": "5412",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "cost_code",
                    "value": "23-8745",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "category",
                    "value": "MAT",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                }
            ],
            "commerce": {
                "cinx_id": {
                    "type": "ORG-COMMERCE",
                    "domain": "orgs",
                    "id": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f"
                }
            }
        },
        {
            "cinx_id": {
                "type": "ORG",
                "domain": "orgs",
                "id": "org-0001-4221"
            },
            "name": "Hilti-6",
            "address": null,
            "vendor_id": "V101",
            "vendor_status": "A",
            "vendor_type": "PVF",
            "customer_id": "C101",
            "availableUsers": [],
            "users": [],
            "attributes": [
                {
                    "name": "discount_days_type",
                    "value": "Number of Days",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "discount_days",
                    "value": "10",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "discount_percent",
                    "value": "1.5",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "due_days",
                    "value": "30",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "late_fee_percent",
                    "value": "1.5",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "payment_days_type",
                    "value": "Number of Days",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "expense_account",
                    "value": "4156",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "cost_code",
                    "value": "UG-123",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "category",
                    "value": "MAT",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                }
            ],
            "commerce": {
                "cinx_id": {
                    "type": "ORG-COMMERCE",
                    "domain": "orgs",
                    "id": "7880c854-017f-5359-96de-fdef626c33cf"
                }
            }
        },
        {
            "cinx_id": {
                "type": "ORG",
                "domain": "orgs",
                "id": "org-0000-5814"
            },
            "name": "National Sales Company",
            "address": {
                "type": "SHIPPING",
                "address1": "1533 Delmar Avenue",
                "address2": "",
                "address3": "",
                "city": "St. Louis",
                "state": "Missouri",
                "postal_code": "63103",
                "country": "USA",
                "latitude": "",
                "longitude": "",
                "guid": "2197a94b-2572-5930-86fa-b6e69f74c5d0",
                "desc": "1533 Delmar Avenue"
            },
            "vendor_id": "CXV101",
            "vendor_status": "A",
            "vendor_type": null,
            "customer_id": "CX101",
            "availableUsers": [],
            "users": [],
            "attributes": [
                {
                    "name": "discount_days_type",
                    "value": null,
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "discount_days",
                    "value": 0,
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "discount_percent",
                    "value": 0,
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "due_days",
                    "value": 30,
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "late_fee_percent",
                    "value": 21,
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "payment_days_type",
                    "value": "Number of Days",
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "expense_account",
                    "value": null,
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "cost_code",
                    "value": null,
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                },
                {
                    "name": "category",
                    "value": null,
                    "doc_type": "ORG-COMMERCE",
                    "ux_section": "VENDOR-TERMS"
                }
            ],
            "commerce": {
                "cinx_id": {
                    "type": "ORG-COMMERCE",
                    "domain": "orgs",
                    "id": "de0cf849-6f7b-5df6-9ae9-f924659f2d25"
                }
            }
        },
        {
            "cinx_id": {
                "type": "ORG",
                "domain": "orgs",
                "id": "org-0001-4239"
            },
            "name": "QWE",
            "address": null,
            "vendor_id": "QWE",
            "vendor_status": "A",
            "vendor_type": null,
            "customer_id": null,
            "availableUsers": [],
            "users": [],
            "attributes": [],
            "commerce": {
                "cinx_id": {
                    "type": "ORG-COMMERCE",
                    "domain": "orgs",
                    "id": "07815207-2061-5306-b6f2-24aaa8015da2"
                }
            }
        },
        {
            "cinx_id": {
                "type": "ORG",
                "domain": "orgs",
                "id": "org-0001-4228"
            },
            "name": "Vendor DEV",
            "address": null,
            "vendor_id": "V1",
            "vendor_status": "A",
            "vendor_type": null,
            "customer_id": null,
            "availableUsers": [],
            "users": [],
            "attributes": [],
            "commerce": {
                "cinx_id": {
                    "type": "ORG-COMMERCE",
                    "domain": "orgs",
                    "id": "3e008ab6-3c46-50da-b7cc-7d14023394b5"
                }
            }
        }
    ]
}
```

This request will be used to get a list of the company’s Vendors from CINX.

URL Pattern:

{api path}/sub/{B2B Id GUID}/vendors

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/vendors`

## Get Vendor Details
### API – GET Vendor Details – using CINX Commerce GUID

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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->getCommerceVendorDetails",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/vendor/9a13fcca-e6ae-524f-95dd-0f4d7d26930f/details",
        "format": "json",
        "start_time": 1564234952.761,
        "total_time": 0.42453718185425,
        "record_count": 1,
        "total_count": 0
    },
    "rows": [
        {
            "names": {
                "primary": "Ferguson Testing July 2015",
                "alternate": null,
                "short": null,
                "previous": null
            },
            "addresses": [
                {
                    "address1": "Address 001",
                    "address2": "",
                    "address3": "",
                    "city": "City 001",
                    "state": "AL",
                    "postal_code": "00122",
                    "country": "USA",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 7403",
                    "address2": "",
                    "address3": "",
                    "city": "City 7403",
                    "state": "AL",
                    "postal_code": "code 7403",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "test 001",
                    "address2": "",
                    "address3": "",
                    "city": "city",
                    "state": "AL",
                    "postal_code": "46564",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 3604",
                    "address2": "",
                    "address3": "",
                    "city": "City 3604",
                    "state": "AL",
                    "postal_code": "code 3604",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 8721",
                    "address2": "",
                    "address3": "",
                    "city": "City 8721",
                    "state": "AL",
                    "postal_code": "code 8721",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 9198",
                    "address2": "",
                    "address3": "",
                    "city": "City 9198",
                    "state": "AL",
                    "postal_code": "code 9198",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 2737",
                    "address2": "",
                    "address3": "",
                    "city": "City 2737",
                    "state": "AL",
                    "postal_code": "code 2737",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 4795",
                    "address2": "",
                    "address3": "",
                    "city": "City 4795",
                    "state": "AL",
                    "postal_code": "code 4795",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 8058",
                    "address2": "",
                    "address3": "",
                    "city": "City 8058",
                    "state": "AL",
                    "postal_code": "code 8058",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 2403",
                    "address2": "",
                    "address3": "",
                    "city": "City 2403",
                    "state": "AL",
                    "postal_code": "code 2403",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 6271",
                    "address2": "",
                    "address3": "",
                    "city": "City 6271",
                    "state": "AL",
                    "postal_code": "code 6271",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 2894",
                    "address2": "",
                    "address3": "",
                    "city": "City 2894",
                    "state": "AL",
                    "postal_code": "code 2894",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 7789",
                    "address2": "",
                    "address3": "",
                    "city": "City 7789",
                    "state": "AL",
                    "postal_code": "code 7789",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 6173",
                    "address2": "",
                    "address3": "",
                    "city": "City 6173",
                    "state": "AL",
                    "postal_code": "code 6173",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 2729",
                    "address2": "",
                    "address3": "",
                    "city": "City 2729",
                    "state": "AL",
                    "postal_code": "code 2729",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 43267",
                    "address2": "",
                    "address3": "",
                    "city": "City 43267",
                    "state": "AL",
                    "postal_code": "code 43267",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 11703",
                    "address2": "",
                    "address3": "",
                    "city": "City 11703",
                    "state": "AL",
                    "postal_code": "code 11703",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 92077",
                    "address2": "",
                    "address3": "",
                    "city": "City 92077",
                    "state": "AL",
                    "postal_code": "code 92077",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 28041",
                    "address2": "",
                    "address3": "",
                    "city": "City 28041",
                    "state": "AL",
                    "postal_code": "code 28041",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 14960",
                    "address2": "",
                    "address3": "",
                    "city": "City 14960",
                    "state": "AL",
                    "postal_code": "code 14960",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 72374",
                    "address2": "",
                    "address3": "",
                    "city": "City 72374",
                    "state": "AL",
                    "postal_code": "code 72374",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 2798",
                    "address2": "",
                    "address3": "",
                    "city": "City 2798",
                    "state": "AL",
                    "postal_code": "code 2798",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 62012",
                    "address2": "",
                    "address3": "",
                    "city": "City 62012",
                    "state": "AL",
                    "postal_code": "code 62012",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 61711",
                    "address2": "",
                    "address3": "",
                    "city": "City 61711",
                    "state": "AL",
                    "postal_code": "code 61711",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 60068",
                    "address2": "",
                    "address3": "",
                    "city": "City 60068",
                    "state": "AL",
                    "postal_code": "code 60068",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 86802",
                    "address2": "",
                    "address3": "",
                    "city": "City 86802",
                    "state": "AL",
                    "postal_code": "code 86802",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 70215",
                    "address2": "",
                    "address3": "",
                    "city": "City 70215",
                    "state": "AL",
                    "postal_code": "code 70215",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 30992",
                    "address2": "",
                    "address3": "",
                    "city": "City 30992",
                    "state": "AL",
                    "postal_code": "code 30992",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 47381",
                    "address2": "",
                    "address3": "",
                    "city": "City 47381",
                    "state": "AL",
                    "postal_code": "code 47381",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 72530",
                    "address2": "",
                    "address3": "",
                    "city": "City 72530",
                    "state": "AL",
                    "postal_code": "code 72530",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 12651",
                    "address2": "",
                    "address3": "",
                    "city": "City 12651",
                    "state": "AL",
                    "postal_code": "code 12651",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 12708",
                    "address2": "",
                    "address3": "",
                    "city": "City 12708",
                    "state": "AL",
                    "postal_code": "code 12708",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 83007",
                    "address2": "",
                    "address3": "",
                    "city": "City 83007",
                    "state": "AL",
                    "postal_code": "code 83007",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 41433",
                    "address2": "",
                    "address3": "",
                    "city": "City 41433",
                    "state": "AL",
                    "postal_code": "code 41433",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 89378",
                    "address2": "",
                    "address3": "",
                    "city": "City 89378",
                    "state": "AL",
                    "postal_code": "code 89378",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 84892",
                    "address2": "",
                    "address3": "",
                    "city": "City 84892",
                    "state": "AL",
                    "postal_code": "code 84892",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 34979",
                    "address2": "",
                    "address3": "",
                    "city": "City 34979",
                    "state": "AL",
                    "postal_code": "code 34979",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 83299",
                    "address2": "",
                    "address3": "",
                    "city": "City 83299",
                    "state": "AL",
                    "postal_code": "code 83299",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 35327",
                    "address2": "",
                    "address3": "",
                    "city": "City 35327",
                    "state": "AL",
                    "postal_code": "code 35327",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 53992",
                    "address2": "",
                    "address3": "",
                    "city": "City 53992",
                    "state": "AL",
                    "postal_code": "code 53992",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 40162",
                    "address2": "",
                    "address3": "",
                    "city": "City 40162",
                    "state": "AL",
                    "postal_code": "code 40162",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 3259",
                    "address2": "",
                    "address3": "",
                    "city": "City 3259",
                    "state": "AL",
                    "postal_code": "code 3259",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 26744",
                    "address2": "",
                    "address3": "",
                    "city": "City 26744",
                    "state": "AL",
                    "postal_code": "code 26744",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 84905",
                    "address2": "",
                    "address3": "",
                    "city": "City 84905",
                    "state": "AL",
                    "postal_code": "code 84905",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 38613",
                    "address2": "",
                    "address3": "",
                    "city": "City 38613",
                    "state": "AL",
                    "postal_code": "code 38613",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 53117",
                    "address2": "",
                    "address3": "",
                    "city": "City 53117",
                    "state": "AL",
                    "postal_code": "code 53117",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 69611",
                    "address2": "",
                    "address3": "",
                    "city": "City 69611",
                    "state": "AL",
                    "postal_code": "code 69611",
                    "type": "BILLING"
                },
                {
                    "country": "USA",
                    "address1": "Street 36659",
                    "address2": "",
                    "address3": "",
                    "city": "City 36659",
                    "state": "AL",
                    "postal_code": "code 36659",
                    "type": "SHIPPING"
                },
                {
                    "country": "USA",
                    "address1": "Street 40535",
                    "address2": "",
                    "address3": "",
                    "city": "City 40535",
                    "state": "AL",
                    "postal_code": "code 40535",
                    "type": "BILLING"
                }
            ],
            "marketing": {
                "desc": null,
                "year_founded": null,
                "logo": null
            },
            "emails": [],
            "faxes": [],
            "phones": [],
            "urls": [],
            "ids": [],
            "vendor_id": "99999",
            "vendor_status": "A",
            "vendor_type": "PVF",
            "location_id": null,
            "emergency_info": null,
            "org": {
                "cinx_id": {
                    "type": "ORG",
                    "domain": "orgs",
                    "id": "org-0000-7108"
                }
            },
            "commerce": {
                "cinx_id": {
                    "type": "ORG-COMMERCE",
                    "domain": "orgs",
                    "id": "9a13fcca-e6ae-524f-95dd-0f4d7d26930f"
                }
            }
        }
    ]
}
```

This request will be used to get the details of a vendor.

URL Pattern:

{api path}/sub/{B2B Id GUID}/vendor/{commerce guid}/details

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/vendor/512d5a2f-1d6c-21ca-9b97-9299ac9c802a/details`

## Create Vendor
### API – PUT New Vendor

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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->createPrivateVendor",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/private/vendor/create",
        "format": "json",
        "start_time": 1564235057.552,
        "total_time": 0.52051591873169,
        "record_count": 2,
        "total_count": 0
    },
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

This request will be used to insert a new private vendor for an organization.

URL Pattern:

{api path}/sub/{B2B Id GUID}/private/vendor/create?values={JSON Structure}

The **values** section of this URL must contain properly formatted JSON.  If the structure is an array, all elements of the array must be submitted.  Please see the **CINX Vendor JSON Structures** section of this document for a listing of the available JSON structures.

Sample:

`https://api.cinx.com/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/private/vendor/create?values={%22name_primary%22:%22Hilti%22,%22vendor_id%22:%22H123%22,%22vendor_type%22:%22Hardware%22,%22add_address%22:{%22type%22:%22Mailing%22,%22address1%22:%22Route%203%22,%22address2%22:%22Building%204%22,%22address3%22:%22Suite%20G%22,%22city%22:%22Woburn%22,%22state%22:%22MA%22,%22postal_code%22:%2201234%22,%22country%22:%22USA%22,%22latitude%22:%22%22,%22longitude%22:%22%22}}`

## Modify Vendor
### API – Modify a Vendor

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
    "response": {
        "status_code": 200,
        "message": "OK",
        "method": "Org->modifyPrivateVendor",
        "uri": "sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/private/vendor/117556cd-c16b-5724-97fd-f9b644ee0b02/modify",
        "format": "json",
        "start_time": 1564235188.569,
        "total_time": 0.50932908058167,
        "record_count": 2,
        "total_count": 0
    },
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





