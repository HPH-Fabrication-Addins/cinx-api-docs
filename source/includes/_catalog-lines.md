# Catalog Lines
## Get Root Level
### API – GET Private Catalog Lines – Root Level

> The above code returns JSON structured like this:

```json
```

This request will be used to retrieve the Root level Private Catalog lines for an Org’s private catalog. 

URL Pattern:

{api path}/sub/{B2B Id GUID}/line/hierarchy/roots

Sample:

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/line/hierarchy/roots`

## Get Children
### API – GET a Private Catalog Line’s Children (sub-lines)

> The above code returns JSON structured like this:

```json
```

This request will be used to retrieve the children (sub-lines) of a parent line within an Org’s Private Catalog. 

URL Pattern:

{api path}/sub/{B2B Id GUID}/line/hierarchy/{parent hierarchy GUID}/children

Sample:   

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/line/hierarchy/7ec57062-0ad0-c331-fbe2-6023b015c6e8/children`




