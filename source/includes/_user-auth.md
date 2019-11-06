# User Auth

## User Auth
### API Endpoint - User Subscription/Authorization

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.getSubscriptions()
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
            "cinx_api_token": "dfed7d88-adf8-5356-8029-fe061c93d0fe",
            "user": {
                "cinx_user_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
                "first_name": "Will",
                "middle_name": "",
                "last_name": "Stone",
                "suffix": ""
            },
            "org": {
                "cinx_org_id": "org-0001-4030",
                "name": "WTS Mechanical -DEV"
            },
            "subscription": {
                "status_code": 200,
                "status_message": "OK",
                "status_message_reason": null,
                "start_date": "2017-10-20",
                "end_date": "2025-11-19",
                "apps": [
                    {
                        "cinx_app_guid": "3780a6b903937022c5649f5cd391744e",
                        "cinx_app_id": "d217f7b7-ef49-5ae1-adf3-3765160725a4",
                        "name": "Integrated Price Updates",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "My Private Catalog"
                    }
                ]
            }
        },
        {
            "cinx_api_token": "fde79d15-0a1b-5d51-a665-7b87ed341711",
            "user": {
                "cinx_user_guid": "185aabe1-3487-5f59-9ad5-c577a76bd392",
                "first_name": "Will",
                "middle_name": "",
                "last_name": "Stone",
                "suffix": ""
            },
            "org": {
                "cinx_org_id": "org-0001-4032",
                "name": "Alpine Mechanical"
            },
            "subscription": {
                "status_code": 401,
                "status_message": "Unauthorized",
                "status_message_reason": "Subscription expired on [2017-11-22]",
                "start_date": "2017-10-23",
                "end_date": "2017-11-22",
                "apps": [
                    {
                        "cinx_app_guid": "308-599736-f129d818-ca871bfb90-350af7",
                        "cinx_app_id": "f5e9f665-1239-5a1e-8c01-7afda01d6e3d",
                        "name": "Autodesk Fabrication Add-In",
                        "type": "INTEGRATION : IMPORT-EXPORT",
                        "data_source": "My Private Catalog"
                    }
                ]
            }
        }
    ]
}
```
`GET`

This endpoint will be used to get the applications/subscriptions that the user is authorized to access.  The response will also contain account status and CINX Ids required to make additional API calls.

**Notes**

  - A User can be associated with multiple companies (orgs).  In this case, their will be multiple **Rows** in the response.
  - If a User account is expired, the **status_code** in the subscription object will be **401**.
  - For additional information about working with this response see this page [Auth Response](#auth-response)

URL Pattern: **{api path}/{api version}/subs**

URL Sample: `https://api.cinx.com/2.0/subs`

**RESPONSE FIELDS**

<aside class="warning">
API TOKEN: The CINX API uses an API Token when submitting web service requests. The CINX API Token is retrieved from the response of this call in a field named cinx_api_token. A company that has a CINX account must also be configured to permit API access before the API token will be returned in the authorization API response. Please email support@cinx.com to request access to the API if your company does not have an API Token.   
</aside>

Field Name | Description
----- | ----- | ----- 
cinx_api_token | Company-specific API token value that will be used in the URL of other CINX API calls. Token is valid for the duration of a company’s CINX subscription. Tokens **will be** different on the two different CINX servers (Dev and Production).
user.cinx_user_guid | CINX unique Id for the user.
user.first_name | User's first name.
user.middle_name | User's middle name.
user.last_name | User's last name.
user.suffix | User's name suffix.
org.cinx_org_id | CINX unique Id for the company/organization.
org.name | Name of the company/organization.
subscription.status_code | Status code for the subscription. Potential values are **200** and **401**.
subscription.status_message | Message relating to the status code. Potential values are **OK** or **Unauthorized**.
subscription.status_message_reason | Reason for the status code. If the account is expired the account expiration date will be provided.
subscription.start_date | Start date of the company's subscription.
subscription.end_date | Expiration date of the company's subscription.
apps.cinx_app_guid | System constant value that is used to identify an application within the CINX platform. If you are a software company that requires data access to a specific catalog of content, a CINX app will be created and you will be provided the cinx_app_guid so that you can query the response for instances of your app.
apps.cinx_app_id | Unique value that links a subscribing CINX company/org to the application. This value will be required when making API calls to access content.
apps.name | Name of the application.
apps.type | CINX application type. Current CINX App types include Integration (interactions with other software systems) and Data-Source (catalog of content).
apps.data_source | Name of the source of the item content that will be used to create content update files (price updates).

## Auth Response
### Working with the GET User Subscription/Auth API Response

The Subscription/Authorization API response will provide the necessary information to make subsequent API requests.

Please keep the following CINX Platform attributes in mind as you begin to work with the Subscription response:

  - A User may be associated with more than one company (multiple Orgs in the CINX subscription result)
  - An Org can subscribe to multiple catalogs of content
  - An Org might have multiple subscriptions to a single App  (the data for the App coming from different sources)
  - A User may use a CINX Addin for multiple partner applications on the same computer
  - Objects in the CINX Platform are assigned Unique Ids that will be required API URL elements

The JSON response uses the following structure:

<img src='images/subscription6.jpg'/>

Each **Row** array of the response will correspond to an Org to which the user is a member and will contain the following components:

**CINX API Token:** Token that will be used in API calls to access and insert data.

**User:** provides basic information about the user and his/her CINX Unique Id.

**Org:** basic information that can be used to identify a registered CINX org.  

**Subscription:** defines the org’s subscription status which controls access to the API.

**Subscription [Apps]:** an array of applications that the org currently subscribes to and can access using the API. The structure of an app object is governed by its **Type**. Current CINX App types include **Data-Source** (catalog of content) and **Integration** (interactions with other software systems). The contents of this array will only be used if your app needs to access content of a specific CINX Data Source in a pre-defined data format. For example, price updates for an estimating system database.


The following sections contain important information about using the API and the CINX Unique Ids that will be required for making API calls. 

**Does the subscription response contain a CINX API Token?**
A CINX API Token is required to grant programmatic access to content on the CINX Platform. The API Token will appear at the top of the response object in a field named **cinx_api_token**. If there is not a value in this field, then access to content will be denied. A user can contact HPH, to have the necessary account modification made to allow for the generation of the token.

<img src='images/subscription10.jpg'/>

**Is the subscription active?**
API-based access to CINX will also be controlled by the org’s subscription status. You will need to verify that the subscription is active. This is done by checking the **subscription** object of the response.

If the subscription is active the response will have the following information:

<img src='images/subscription11.jpg'/>

**What is the user’s CINX Unique Id?**
The CINX User Unique Id (GUID) will be required by some API requests. These requests will generally be ones in which new information is created or existing content is updated.

<img src='images/subscription12.jpg'/>

**Will you need to access price updates or other item content stored in a CINX Catalog in a specific pre-defined format?**

The **Apps** array within the **Subscription** object in the response will provide a list of applications to which the org has subscribed.  

<img src='images/subscription13.jpg'/>

The **cinx_app_guid** is a constant value that is used to identify an application within the CINX platform. If you are a software company that requires data access to a specific catalog of content, a CINX app will be created and you will be provided the **cinx_app_guid** so that you can query the response for instances of your app.

The **cinx_app_id** is a unique value that links a subscribing CINX org to your application. This value will be required when you are making API calls to access content.

The **data_source** name value will define the source of the item content that will be used to create content update files (price updates). For more information about the relationship between and app and a data source, please review the CINX Applications and Data Source page.
