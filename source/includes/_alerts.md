# Alerts

## Get Alerts
### API Endpoint – Get Received User Alerts

`GET`

This request will be used get a user’s CINX system alerts.

URL Pattern: **{api path}/{api_version}/sub/{api_token}/user/alerts**

URL Sample: `https://api.cinx.com/2.0/sub/dfed7d88-adf8-5356-8029-fe061c93d0fe/user/alerts`

**OPTIONAL URL PARAMETERS**

Parameter Name | Description | Value Type or Options
----- | ----- | ----- 
format | Defines the response format type. If not specified, json will be used. | json, xml
shown | Defines if the Alert has been viewed by the user. | 0, 1
closed | Defines if the Alert has been closed/removed by the user. | 0, 1



add time to date? 
add shown, closed?
add acknowledged (functional alert)?




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
  


