# Token Auth

## Token Auth
### API Endpoint - User Subscription/Authorization Token

```json
{
    "token": "b9bff245-e1f2-410a-8244-7beabeda6a99",
    "token_exp_date": "2024-08-07",
    "account_exp_date": "2025-11-13",
    "authorized": {
        "tokens": [
            "API"
        ],
        "apps": [
            {
                "name": "CINX B2B",
                "id": "a4cdf53d-1e7d-7ef9-8cbe-922194241980",
                "type": "INTEGRATION",
                "sub_type": "B2B",
                "access": "RESTRICTED",
                "app_cdoc": "couchdb://apps/2d4dde95cc7d1a3d8e830036ff126f60",
                "attributes": [],
                "cost": 50,
                "is_paid": "1",
                "users": [],
                "notify": [],
                "labor_app": false,
                "logo": "https://cdn.cinx.com/assets/apps/cinx-integration-b2b.png",
                "description": "CINX B2B Partner API Integration Services",
                "data_source": "couchdb://apps/a6502d78d800a4cd3cc052562500033a",
                "data_source_name": "My Private Catalog",
                "catalog_source": "couchdb://apps/a6502d78d800a4cd3cc052562500033a"
            }
        ]
    }
}
```

`GET`

There are times where you may wish to use an API token instead of HTTP Basic Auth username and password to access the API in an authenticated manner. 
In that case, you will need to generate a bearer token for the user's credentials.

URL Pattern: **{api path}/{api version}/auth/token/generate**

URL Sample: `https://api.cinx.com/2.0/auth/token/generate`

HTTP basic authentication required.

Required additional header:

    * `Partner-Id` with a value of `oauth-api`


### How to Use ###
In the returned data, if the user is valid and has an active subscription to CINX, there are two key guids returned that you need to access 
other resources permitted to this account:

* `token` - This is the Bearer Token that you will you on subsequent calls, *instead of* HTTP basic authentication. 
** Using the sample JSON return here as an example, you'd set the `Bearer` header to a value of `b9bff245-e1f2-410a-8244-7beabeda6a99`
* `authorized.apps.id` - This is the API token, here called the CINX api token

Also note the expiration date; you may wish to save the Expiration Date so you can remind your users that they need to refresh their token
to continue to access protected resources and features of CINX.

#### Update 2024-06-26 ####
We are working on a ticket to create version 2.1, where the output of this call matches that of [User Authentication](#user-auth).
