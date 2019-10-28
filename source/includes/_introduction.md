# Introduction

## Welcome
### Welcome to the CINX API Documentation site

CINX is a platform product from Harrison Publishing House (HPH) serving the construction industry in North America.  

The CINX API provides access to building material information, construction project information, and material transactions exchanged with product vendors.

The API requires a user to have a valid CINX account with an API subscription.  

HPH will be pleased to work with any developer seeking to utilize the API. Please email us at:  **support@cinx.com**

## REST API
### CINX REST API General Information

> JSON formatted response

```json
{
  "start_time": 1411574224.8083,
  "response": {
    "status_code": 200,
    "message": "OK",
    "record_count": 1,
    "server_response_time": 0,
    "total_elapsed_time": 0.02492094039917,
    "total_count": 0
  },
  "rows": []
}
```

> XML formatted response

```xml
<cinx_api>
  <start_time>1414436492.2267</start_time>
  <response>
    <status_code>200</status_code>
    <message>OK</message>
    <record_count>2</record_count>
    <server_response_time>0</server_response_time>
    <total_elapsed_time>0.013047933578491</total_elapsed_time>
    <total_count>0</total_count>
  </response>
  <rows>
    <row> 
    </row>
  </rows>
</cinx_api> 
```

The CINX platform offers programmatic access to read and write data using REST web services and standard HTTP methods/verbs.


**Authentication & Headers**

HTTP Basic Authentication over HTTPS is used to control access to CINX platform resources.

With each API call, you’ll need to set request headers, including a CINX user’s email and password.


**Account Authorization**

CINX accounts are subscription based and have expiration dates. Accounts with expired subscriptions will not have access to CINX data.  


**API Server Paths**

The production server is: **https://api.cinx.com**

The development server is: **https://api.dev.cinx.biz**


**API Version**

The CINX API is versioned. This documentation supports version 2.0 and higher. The API version will be added to the API server path and become part of the base URL.


**API Token**

The CINX API uses an API Token when submitting web service requests. The CINX API Token is retrieved from the subscription authorization API response. A company that has a CINX account must also be configured to permit API access before the API token will be returned in the authorization API response. The API token is valid for the duration of a company’s CINX subscription. The API token will be added to the base URL following the API Version number.

**API Base URL**

The CINX API Base URL is constructed from the components shown below:

  - **https://api.cinx.com/2.0/{api_token_value}/sub/**
  - **https://api.dev.cinx.biz/2.0/{api_token_value}/sub/**


**API Response Formatting – Standard/JSON**

All CINX API responses use a standardized format. By default, a JSON formatted response is provided.  Please see below if you prefer XML.

The **response** object will contain meta data about the server’s response to the request.

The **rows** array will contain the query results.


**API Response Formatting – XML**

To receive an XML response, please add the following parameter to the url: **format=xml**


**Result Rows - Paging**

For many HTTP GET requests you can use URL parameters to define the number of rows returned in the response.  Valid input parameters are:

  - **start={number}**

  - **limit={number}**

## Documentation Notes
### API Documentation Web Site Formating Notes

**API URL References**

The API calls documented on this site will contain two URL sections to assist in the construction of properly formatted URLs to be submitted to CINX.

  - **URL PATTERN**: This section defines the elements of the URL. Portions of the URL that will require variables to be inserted will be shown in curly braces. 

  - **URL SAMPLES**: Each API call definition page will also contain at least one sample. The sample will be fully formatted.  
THE SAMPLES WILL NOT DISPLAY A RESPONSE IF CLICKED.  The samples are provided only for formatting verification purposes.


## Developer Resources
### Additional API Resources for Developers

**Demo Site**

A simple demo site has been created to demonstrate the implementation of commonly used API calls. The URL for the demo site is: **https://www.dev.cinx.biz/cinxjs/**

**Javascript Library**
A Javascript library has been created to support the implementation of the API. The library is hosted on Github and can be accessed via this URL: **https://github.com/cinx-api/js-library**

## PING Server
### API Endpoint - PING CINX API Server

```javascript
//Using cinx-api.js
var cinxApi = new CinxApi();
cinxApi.setCredentials('CINX USERNAME', 'CINX PASSWORD');
cinxApi.setApiPathAndVersion('https://api.cinx.com', '2.0');

cinxApi.pingCinx()
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
      "status": 200,
      "message": "CINX: API Ping Response: Ok"
    }
  ]
}
```
`GET`

This endpoint can be used to test the availability of the CINX API.

URL Pattern: **{api path}/{api_version}/ping**

URL Samples: `https://api.cinx.com/2.0/ping`

## App/Sub Model
### CINX Application/Subscription Model Introduction

A CINX customer (organization) has the opportunity to subscribe to different applications available on the platform. An application can be a grouping of pages and functionality on the CINX web site or external applications that consume content from CINX. Each application on the CINX platform has a unique identifier and a range of fields that define its attributes. When an organization subscribes to an application, a new unique identifier is created to link the application to the subscribing organization. This application id will be used in API calls to identify and grant access to requested data operations.

<img src='images/subscription1.jpg'/>

## Data Sources
### CINX Data Source Introduction

CINX supports different “catalogs” (databases) of content. Companies subscribing to CINX can have access to multiple catalogs of content.  Here are some common catalogs in CINX:

  - HPH Plumbing/Mechanical
  - MCAA WebLEM
  - PHCC Labor Units 
  
Another catalog that each CINX company can use is a **Private** catalog.  This catalog of content is specific to the subscribing company and can contain material items. These items can be copied from another catalog on CINX or manually entered/uploaded by the company.

Estimating systems, CAD/BIM software systems, and other software partners that utilize CINX content will also have a separate CINX Catalogs. This allows each system to have a specific set of items that CINX maintains.

A good way to visualize this concept is to open the Catalog drop-down in the CINX Search app. Here is a screen shot that shows a company that has access to many catalogs. Note: each company’s private catalog will be listed using the company’s name as registered in CINX.
  
<img src='images/subscription2.jpg'/>
  
When working with the CINX API in conjunction with a company’s subscription a catalog is often named as Data Source in API responses.

## App - Data Sources
### CINX Application and Data Source Introduction

For software partner (external) applications that consume data from CINX there is an important attribute in the CINX subscription that defines which CINX catalog is used to acquire information for data outputs. This attribute is called a **data source**.
  
Importantly, a company can subscribe to an application multiple times provided that the data source is different. For example, a company using an industry estimating system may have CINX produce updates for different locations using different CINX Catalogs (data sources). One location may want standard list prices from the standard estimating database and another location may want update files to contain net buy prices based on their private catalog of content.

<img src='images/subscription3.jpg'/>
  
**Please note that when working with the CINX Subscription/Authorization API response each combination of an application and a data source will be listed in separate blocks.**
  
Below is a sample showing an App with two different data sources.


**Data Source Name: Quotesoft**

<img src='images/QSI-QSI.jpg'/>


**Data Source Name: My Private Catalog**

<img src='images/Qsi-MPC.jpg'/>

## Templates
### CINX Data Object Templates

To assist developers in creating and modifying data objects on the CINX Platform, the API includes templates that define the data structure and provide other information that can be used to present data options to the end-user.

The templates are accessed via the API and use a standardized response structure containing the following data structures:

**doc_info:** identification and version info for the template

<img src='images/subscription18.jpg'/>

**template:** data structure that should be used when submitting a POST or PUT payload. Note: fields not used do not have to be submitted.

<img src='images/subscription19.jpg'/>

**field_options:** defines available options for data fields

<img src='images/subscription20.jpg'/>

**api_calls:** lists related API calls.  The url in the response is fully formed with the proper API Token and other variables.  The API calls will include the web service to POST/PUT the data and any calls that can be used to access data that can be populated in the template. 

<img src='images/subscription21.jpg'/>

<aside class="notice">
Fields with a NULL value should be removed before creating or modifying an object. See the CINX demo site for sample code. Submitting a NULL value will over-write existing values.
</aside>

## Auto-Numbering
### CINX Object Auto-Numbering 

CINX provides a subscribing company with the option of automating the numbering of common objects when new instances are created. These numbers are the **public** values used by the company to define the objects. These are NOT system level ids.

Objects on the CINX Platform that can be auto-numbered for contractors are:

  - Vendors
  - Customers
  - Projects
  - Requisitions
  - RFQs (Request for Quotations)
  - POs (Purchase Orders)
  - Deliveries
  - Returns
  - Submittals
  - Transmittals

API calls for obtaining the next number for an object are provided and documented. Please note, that a number will only be provided if the company has activated the auto-numbering feature for the object. If the feature is not activated the API will return a 406 response.

 <img src='images/No-Auto-Number.jpg'/>


**Notes on other Transaction Numbering**

  - Purchase Order Change Orders are numbered by appending a numeric suffix the the original PO Number.
  - Invoices use the Vendor Invoice number

## PUT/POST Processing
### PUT and POST Processing Options

By default some PUT and POST operations will be processed asynchronously. This is due to the fact that some transactions could include a large volume of items which could require longer processing times. These calls will be noted on the API Documentation pages.

If you would like to override the asynchronous default an optioinal URL parameter is provided.  Using **synchronous=1** in the URL will switch the processing mode to be synchronous.

## CINX Ids
### CINX Platform Unique Ids
 
The CINX platform stores many Ids for different object types from different sources. For example, an item on a PO may have Ids defined by the customer, vendor, and product manufacturer. 

To clearly define CINX System Ids in API responses, the CINX Ids will be positioned at the top of response for the requested object. They will in most cases be named **cinx_guid**.

 <img src='images/cinx_guid_response.jpg'/>

If a response contains child JSON objects or arrays that list multiple CINX Ids, then the CINX Id will contain the name of the object being referenced.

## Commerce GUIDs
### CINX Commerce Relationship GUIDs

When a relationship between the two parties is created in CINX, a new document that links the two parties is created. Examples relationships include:

*	A contractor (customer) has a CINX relationship with a product wholesale distributor (vendor) that deliver products used in a project.
*	A building owner (customer) has a CINX relationship with a contractor (vendor) that completes a job.

The relationship document allows for the storage of important parameters that are required to deliver and process transactions, submittals, and other communications. This relationship is also assigned a new CINX GUID. This new Id is therefore used by the API as a URL parameter when fetching and updating relationship data. To clearly differentiate the Commerce GUID from a GUID assigned to an individual company (org), the API uses a different naming convention.

The Commerce GUIDs in API responses and requests will be named **cinx_commerce_guid**.

 <img src='images/cinx_commerce_guid.jpg'/>

## NULL Values
### Submitting NULL values

When a NULL value is submitted in a PUT or POST request, any existing value in the data field will be replaced with a NULL. Please see the CINX demo for code to strip fields with NULL values before they are submitted to the API. However, please use caution if you implement code to remove NULLs as this is the only method for deleting an existing value.

Please see the **External Refs** and **Attributes** sections below for information regarding removing values in those arrays.

## External Refs
### CINX External References

To assist in the exchange of data between systems, CINX supports external references for most object types.

A common use for an external reference is a system id from a non-CINX application. The API supports setting and modifying of these references using a three-field array structure:

 <img src='images/cinx-ext-refs.jpg'/>

<aside class="notice">
The TYPE, DESCRIPTION and VALUE fields are all required.
</aside>

Processing Notes

* To update the **value** of an existing external reference, submit the existing **type** with the revised **value**
* To remove an external reference submit the **type** with a NULL or empty string in the **value** field 
* If a new external reference is submitted without a **type** or **value** it will not be saved

## Attributes
### CINX Attributes

Attributes are also used to assist in the exchange of data between systems. Similar in concept to an external reference, attributes are intended to provide API users the ability to set and retreive values relevant to another system.  

In the API, attributes are used on objects that do not have external references. An important example is a BOM-ITEM.

The API supports setting and modifying of attributes using a two-field array structure:

 <img src='images/attribsStructure.jpg'/>

<aside class="notice">
The TYPE and VALUE fields are both required.
</aside>

Processing Notes

* To update the **value** of an existing attribute, submit the existing **type** with the revised **value**
* To remove an attribute submit the **type** with a NULL or empty string in the **value** field 
* If a new attribute is submitted without a **type** or **value** it will not be saved
