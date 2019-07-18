# Mfr Price Sheets

## Introduction
### Manufacturer Price Sheet Introduction

A Price Sheet is a document that is issued by a product manufacturer or service provider that define the prices that will be charged to consumers for procuring the listed materials or services.  Manufacturers with large product offerings often have multiple price sheets with each containing only a segment of the manufacturer’s overall product listing.  For example, Charlotte has different price sheets for their Cast Iron No Hub, Service Weight, and Extra Heavy products.

Due to rising raw material, labor, transportation and many other factors, manufacturers frequently release new instances of price sheets with revised pricing levels.

Every item price in the Harrison Plumbing/Mechanical catalog on CINX is linked to Manufacturer Price Sheet from which it was obtained.  The CINX API provides several endpoints for working with Manufacturer Price Sheets.

To better understand the API, please review the following terms/concepts:

**Price Sheet Hierarchy:** In CINX there is a hierarchal structure that is used to manage the manufacturers’ price sheet instances.  The three levels of the hierarchy are: Manufacturer, Price Sheet Master, and Price Sheet Detail.

**Manufacturer:**  This is the organization that creates and releases the price sheets.  Each manufacturer will have a unique CINX identifier that will be used in API requests.
Example Manufacturer: Charlotte

**Price Sheet Master:** This defines a type of price sheet issued by the manufacturer.  Each Price Sheet Master will have a unique CINX identifier that will be used in API requests.
Example Price Sheet Master: Charlotte No Hub

**Price Sheet Detail:** This is a specific instance of a price sheet type.  Each Price Sheet Detail will have a unique CINX identifier that will be used in API requests.
Example Price Sheet Detail: Charlotte No Hub – January 1, 2018

**Effective Date:** This is the date that the prices on the Price Sheet are scheduled to be implemented.  This date is set by the manufacturer.  Each Price Sheet Detail will have an Effective Date value. 

## Get Sheet Types
### API – GET Manufacturer’s Price Sheet Masters

This request will be used to get a list of the manufacturer’s price sheet masters.

URL Pattern:

{api path}/sub/{B2B Id GUID}/pricesheet/masters/{org id}

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/pricesheet/masters/org-0000-1108

The results will be sorted alphabetically by **description field values.**

## Get Sheet Instances
### API – GET Manufacturer’s Price Sheet Master Details

This request will be used to get a list of the price sheet details for a given manufacturer price sheet master.

URL Pattern:

{api path}/sub/{B2B Id GUID}/pricesheet/master/{org id}/{price sheet master id}/details

Sample:

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/pricesheet/masters/org-0000-1108

The results will be sorted descending on the **date_effective** field values.

To make subsequent API calls using a price sheet detail, the **id** field within the **cinx_doc** object will be required.

