# Notifications

## API Call – POST External file with User Notifications 

This request will be used to POST an uploaded external file (Excel, PDF, txt) to the CINX CDN.  In addition, this POST operation allows for user notifications to be delivered by the API.  The notification types are **Email** and **CINX System Alert.**

URL Pattern:

{api path}/sub/{B2B Id GUID}/partner/exec/cinx/lib-doc? type=MATERIAL+REQUISITION &name={requisition id}&parent=couchdb://{CINX Org Id}/{CINX Project GUID}&email_subject={text}&notify_email={User Email address}&notify_alert={CINX User GUID}

Sample:

https://api.cinx.com/sub/e8478738-8c4b-a152-609d-f50e34be0090/partner/exec/cinx/lib-doc? type=MATERIAL+REQUISITION&name=Req123&parent=couchdb://org-0000-6138/3dde31ee-694e-0e43-8af2-8382bb6dcc1f&email_subject=NewShopMaterialRequestionReq123&notify_email=bakigervalla@gmail.com&notify_email=dmcphaul@hphguide.com&notify_alert=c61a47a8-3a4a-025a-0db1-2b9e609da089&notify_alert=54e0afa4-c359-f55b-ad3c-cc63df698900

URL Parameter Information

**/partner/exec/cinx/lib-doc**  <literal>

**?type="MATERIAL REQUISITION"**  <literal>

**&name=** {document name} populate with the Requisition Id

**&parent=couchdb://**  <literal> 

CINX Org ID = CINX Id of Org that the current user is associated with /default Org Id (ie, **org-0000-7833** for Your company Dev account)

Project GUID = CINX Project GUID

**&email_subject=** {subject line for email notification} **“New CINX Material Requisition Received** – {req id}”

**&notify_email=**{email address} – Send to User email address - REPEAT as needed using full parameter label and value

**&notify_alert=**{user id/cdoc} - Send to CINX User GUID - REPEAT as needed using full parameter label and value 

## API – GET Received User Alerts

This request will be used get a User’s CINX system alerts.

URL Pattern:

{api path}/sub/{B2B Id GUID}/user/alerts/received?shown=0

Samples:

**“Shown” Parameter**

This optional URL parameter allows us to filter the alerts given their “User Shown” status.

**?shown=0**
**?shown=1**

An alert is marked **shown** when a user has view the alert.

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alerts/received?shown=0

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alerts/received?shown=1

**“Closed” Parameter**

This optional URL parameter allows us to filter the alerts given their “User Closed” status.

An alert is marked **closed** when a user has “deleted” the alert from a UI.

**?closed=0**
**?closed=1**

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alerts/received?closed=0

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alerts/received?closed=1
 
## API – Mark User Alerts Shown or Closed

This request will be used update a user’s CINX system alert’s **Shown** or **Closed** status.

URL Pattern:

{api path}/sub/{B2B Id GUID}/user/alert/{alert GUID}/modify?values={**“shown or closed** attribute label”:{boolean indicator}

Samples:

**Mark Shown**

{api path}/sub/{B2B Id GUID}/user /alert/{alert GUID}modify?values={"shown":1 }

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alert/5dbf1bdf-732c-5c3b-d4cc-c837f5fc2fa2/modify?values={%22shown%22:1}

{api path}/sub/{B2B Id GUID}/user/alert/{alert guid}/modify?values={"closed": 1 }

https://api.cinx.com/sub/050ba80b-832b-89cc-8197-b2a1261a408c/user/alert/5dbf1bdf-732c-5c3b-d4cc-c837f5fc2fa2/modify?values={%22closed%22:1}
  


