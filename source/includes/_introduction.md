# Introduction

## App/Sub Model
### CINX Application/Subscription Model Introduction

A CINX customer (organization) has the opportunity to subscribe to different applications available on the platform. An application can be a grouping of pages and functionality on the CINX web site or external applications that consume content from CINX.  Each application on the CINX platform has a unique identifier and a range of fields that define its attributes.  When an organization subscribes to an application a new unique identifier is created to link the application to the subscribing organization.  This application id will be used in API calls to identify and grant access to requested data operations.

<img src='images/subscription1.jpg'/>

## Data Sources
### CINX Data Source Introduction

CINX supports different “catalogs” of content.  Companies subscribing to CINX can have access to multiple catalogs or databases of content.  Here are some common catalogs in CINX:

  - HPH Plumbing/Mechanical catalog
  - MCAA WebLEM
  - PHCC Labor Units 
  
Another catalog that each CINX company can use is a “Private” catalog.  This catalog of content is specific to the subscribing company and can contain material items.  These items can be copied from another catalog on CINX or manually entered/uploaded by the company.

Estimating systems, CAD/BIM software systems, and other software partners that utilize CINX content will also have a separate CINX Catalogs.  This allows each system to have a specific set of items that CINX maintains.

A good way to visualize this concept is to open the Catalog drop-down in the CINX Search app.  Here is a screen shot that shows a company that has access to many catalogs.  Note:  each company’s private catalog will be listed using the company’s name as registered in CINX.
  
<img src='images/subscription2.jpg'/>
  
When working with the CINX API in conjunction with a company’s subscription a catalog is often named Data Source.


## App - Data Sources
### CINX Application and Data Source Introduction

For software partner (external) applications that consume data from CINX there is an important attribute in the CINX subscription that defines which CINX catalog is used to acquire information for data outputs.  This attribute is called a **data source**.
  
Each application subscription in CINX has this attribute.
  
Importantly, a company can subscribe to an application multiple times provided that the data source is different.  For example, a company using an industry estimating system may have CINX produce updates for different locations using different CINX Catalogs (data sources).  One location may want standard list prices from the standard estimating database and another location may want update files to contain net buy prices based on their private catalog of content.

<img src='images/subscription3.jpg'/>
  
**Please note that when working with the CINX Subscription API response each combination of an application and a data source will be listed in separate blocks.**
  
Below is a sample showing an App with its data source

App Name: Viewpoint Estimation

Data Source Name: Viewpoint Estimation

<img src='images/subscription4.jpg'/>

App Name: Viewpoint Estimation

Data Source Name: My Private Catalog

<img src='images/subscription5.jpg'/>
