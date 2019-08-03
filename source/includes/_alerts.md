# Alerts

## Get Alerts
### API – GET Received User Alerts

`GET`

This request will be used get a User’s CINX system alerts.

URL Pattern:

{api path}/sub/{B2B Id GUID}/user/alerts/received?shown=0

Samples:

**“Shown” Parameter**

This optional URL parameter allows us to filter the alerts given their “User Shown” status.

**?shown=0**
**?shown=1**

An alert is marked **shown** when a user has view the alert.

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alerts/received?shown=0`

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alerts/received?shown=1`

**“Closed” Parameter**

This optional URL parameter allows us to filter the alerts given their “User Closed” status.

An alert is marked **closed** when a user has “deleted” the alert from a UI.

**?closed=0**
**?closed=1**

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alerts/received?closed=0`

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alerts/received?closed=1`
 
## Modify Alerts
### API – Mark User Alerts Shown or Closed

`PUT`

This request will be used update a user’s CINX system alert’s **Shown** or **Closed** status.

URL Pattern:

{api path}/sub/{B2B Id GUID}/user/alert/{alert GUID}/modify?values={**“shown or closed** attribute label”:{boolean indicator}

Samples:

**Mark Shown**

{api path}/sub/{B2B Id GUID}/user /alert/{alert GUID}modify?values={"shown":1 }

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alert/5dbf1bdf-732c-5c3b-d4cc-c837f5fc2fa2/modify?values={%22shown%22:1}`

{api path}/sub/{B2B Id GUID}/user/alert/{alert guid}/modify?values={"closed": 1 }

`https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alert/5dbf1bdf-732c-5c3b-d4cc-c837f5fc2fa2/modify?values={%22closed%22:1}`
  


