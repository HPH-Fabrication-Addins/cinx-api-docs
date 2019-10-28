# Additional Info
## Get Countries
### API Endpoint - Get a List of Countries

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"name": "United States",
			"abv_alpha2": "US",
			"abv_alpha3": "USA",
			"country_code": "840"
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of countries. This can be used when setting addresses within the API. Please use the **abv_alpha3** field.

URL Pattern: **{api path}/{api_version}sub/countries**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/countries`

## Get States
### API Endpoint - Get a List of States for a Country

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"abv": "AL",
			"name": "Alabama"
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of states for a given country. This can be used when setting addresses within the API.  Please use the **abv** field.

URL Pattern: **{api path}/{api_version}sub/country/{country_abv_alpha3}/states**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/country/usa/states`

## Get Currencies
### API Endpoint - Get a List of Currencies

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
			"country": "United States",
			"currency_name": "US Dollar (Next day)",
			"currency_abv": "USN"
		}
    ]
}
```
`GET`

This endpoint will be used to get a list of currencies. Please use the **currency_abv** field when setting a currency in CINX.

URL Pattern: **{api path}/{api_version}sub/currencies**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/currencies`

## CINX Concepts
### List of CINX Terms and Concepts

**Application:** is a grouping of pages, functionality, or an external software partner system that interacts
with the CINX platform and is managed via a CINX subscription plan.

**Base Price:** is the initial price for a product or service. It is also commonly referred to as a List Price or
MSRP.

**BOM Item:** a grouping of fields that defines an item once it has been added to a BOM. This structure
inherits from the Item structure and also provides additional fields for defining its use within a project
(quantities, breakdown structure, spec requirements).

**Buy Price:** is the price paid to a vendor for the purchase of a product or service. The Buy Price is often a
discounted price from a previously established base price - which is commonly referred to as a List Price
or a MSRP.

**Catalog:** a collection of items grouped together in a CINX database structure. Catalogs may contain
construction materials, sub-contract services, rental equipment, and other content necessary for the
execution of a construction project or maintenance of a building.

**Catalog Item:** a building material product or construction related service that is stored within a CINX
catalog. Its data structure includes core information about the product including, part identifiers,
descriptions, attributes, dimensional data, and URLs.

**CINX Id:** uniquely identifies an entity within the CINX system. The Id is comprised of three elements
(Entity Type, Domain, and Id) which together will provide the location and Id of the entity.

**Item Labor:** an Item level structure for storing labor unit (installation time) and cost information.

**Item Quantity:** a component of the BOM Item that is used to detail all information about a quantity's
instance including its type, value, uom, and availability information.

**Item Relationship:** a method by which Items can be associated with one another in the CINX system.
The data structure defines the type and identification of an item relationship. Relationship types include
alternates, required, and complimentary items.

**Labor Unit:** a component of an Item's Labor structure which stores installation time elements.

**Manufacturer:** an organization that produces building material products.

**Multiplier:** (also referred to as a discount) is a decimal value that is applied to a price to determine a buy or
sell price.

**Organization:** CINX entity that defines a company or a grouping of individuals (residential customers)
that participates or is referenced within the CINX platform.

**Price Sheet:** a collection of fields that identify an instance of a building product manufacturer's or
service provider's price list stored within the CINX system.


**Project:** a job that is being performed for a customer/client on a building, structure, or other asset (Built
Entity).

**Sell Price:** is the price charged to a customer for a product or service. A Sell Price is normally related to a Buy Price or an established base price.

**User:** a person who has created a personal CINX account.

## Transaction/BOM Intro
### CINX BOM and BOM-ITEM Introduction

**BOM**

Like many construction software systems, CINX employs the BOM concept. BOM is an acronym for Bill of Materials. A BOM is a collection of materials/services that are grouped together for a particular job or transactional purpose. A BOM will generally contain some descriptive information about its use and then have a listing of materials or services that are linked to it.   

CINX supports the following BOM types:

BOM-ASSEMBLY (Assembly)

BOM-REQ (Requisition)

BOM-RFQ (Request for Quotation)

BOM-QUOTE (Quotation)

BOM-PO (Purchase Order)

BOM-PO-MEMO (Purchase Order Change Order)

BOM-DELIVERY

BOM-RETURN

BOM-INVOICE

PROJECT

**BOM-ITEM**

Once a Catalog item is added to a BOM/Project it becomes a BOM-ITEM. Items imported from another system (estimating, CAD) will also become BOM-ITEMs.

BOM-ITEM is a CINX data structure that is used with all BOM types. It inherits from the Catalog Item structure and also provides additional fields for defining its use within a project (quantities, breakdown structure, spec requirements) and transactions (availability and delivery information).

## CINX Links
### Useful CINX Links


**Login**: **https://secure.cinx.com/login**

**Forgot CINX Password**: **https://secure.cinx.com/login/reset**

**To set up a CINX account click here**: **https://secure.cinx.com/join**

**Terms**: **http://support.cinx.com/terms-of-use-agreement**

 