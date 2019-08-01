# Catalog Item

## Item Definition
### CINX Object Defintion - Catalog

A CINX Catalog Item is a building material product or construction related service that is stored within a CINX catalog.

A CINX Catalog is a collection of items grouped together in a CINX database structure. Catalogs may contain construction materials, sub-contract services, rental equipment, and other content necessary for the execution of a construction project or maintenance of a building.

A CINX orgranization will have a private catalog where items can be stored. An organization's private CINX catalog can be built from the items from CINX public catalogs including the HPH Plumbing/Mechanical list. Private items not associated with a CINX public catalog can also be inserted into an organization's private catalog. Thus, the responsibility for maintaining that item will be the organization.

**Dependencies and Business Rules**
- A catalog item must be associated with a CINX catalog
- A catalog item must have a description
- A catalog item must have a manufacturer

**Supported API Services**
- Get an Item using the HPH Code
- Get an Item using an Organization Id
- Get an Item using a CINX Id
- Get a Purchase Order Number
- Create a Catalog Item from an HPH Code
- Get a Catalog Item Template
- Create a Catalog Item
- Modify a Catalog Item
- Delete a Catalog Item

## Create Item - HPH Code
### API Endpoint – Add a New Catalog Item using an HPH Code

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "cinx_id": {
             UPDATE CONTENTS
            }
        }
    ]
}
```

This endpoint will be used to submit an HPH Item Code for an item and have it added to an organization's private catalog. 

URL Pattern: **{api path}/{api_version}sub/{api_token}/catalog-item/add?hph-code={hph-code}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/catalog-item/add?hph-code=001BS0200F`

HTTP Method: `POST`

## Get Item Template
### API Endpoint - Get a Catalog Item Template

This request will be used to get a CINX Template for a catalog item.

URL Pattern: **{api path}/{api_version}sub/{api_token}/template/item**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/template/item

HTTP Method: `GET`

## Catalog Item Template Fields
### Definition of the Catalog Item Template's Fields

The table below defines the fields within the template.

## Create Item
### API Endpoint – Create a non-HPH Private Catalog Item

> The above code returns JSON structured like this:

```json
{
    "response": {},
    "rows": [
        {
            "cinx_id": {
                
                UPDATE CONTENTS
        }
    ]
}
```

This endpoint will be used to create a private catalog item that is not linked to an HPH Item.  

**Notes**

- A CINX Template is available that documents the available fields that can be populated.
- A JSON formatted payload is used in the POST request

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-item-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-item-import?body=json`

HTTP Method: `POST`

## Modify Item
### API Endpoint – Modify a CINX Private Catalog Item using a CINX Id


This endpoint will be used to modify a private catalog item that is not linked to an HPH Item.  

**Notes**

- A CINX Template is available that documents the available fields that can be populated.
- A JSON formatted payload is used in the PUT request

URL Pattern: **{api path}/{api_version}sub/{api_token}/partner/exec/cinx/json-item-import?body=json**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/exec/cinx/json-item-import?body=json`

HTTP Method: `PUT`


## Delete Item
### API Endpoint – Delete a Catalog Item using a CINX Id

> The above code returns JSON structured like this:

```json
```

This endpoint will be used to remove an item from an organization's private CINX catalog.  Please note that this API call requires the item’s CINX Item Id.

URL Pattern: **{api path}/{api_version}sub/{api_token}/item/{cinx_guid}**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/partner/item/d9863525-d926-5441-9f9c-aa47a285a19b`

HTTP Method: `DELETE`
