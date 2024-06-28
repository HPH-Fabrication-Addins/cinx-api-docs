# Jobs

## Job Status
### CINX Object Definition - Job

A Job is a request submitted to the Partner Integration Gateway, affectionately known
as the PIG.  When you post an asynchronous job to the PIG, you get a simple JSON 
response that includes the job GUID. 

That GUID can then be used to make an authenticated call to the job status API 
here to see if the job has been completed, and if it was successful.

### Call response with processed PIG job


```json
{
  "response": {
    "status_code": 200,
    "message": "OK",
    "method": "App\\Controllers\\Auth->authenticate",
    "uri": "",
    "format": "json",
    "start_time": 1719584394.89486,
    "total_time": 3.177053928375244,
    "record_count": 1,
    "total_count": 0
  },
  "rows": [
    {
      "app": "json-rfq-import",
      "args": {
        "body": ["json"],
        "auto_submit": ["1"],
        "api_version": "2.0",
        "app_cdoc": ["couchdb://apps/2d4dde95cc7d1a3d8e830036ff126f60"],
        "org_cdoc": ["couchdb://orgs/org-unit-test"],
        "org_name": ["PSF Mechanical, Inc."],
        "user_cdoc": ["couchdb://users/CINX-SYSTEM"],
        "user_id": ["2260bc39-5871-4e13-87c6-afd3bfc7519e"],
        "user_name": ["USER TEST"],
        "archive": [1],
        "sub_id": ["93b09b7f-becd-4dd7-801d-80f0f45fa5ab"]
      },
      "command_started_at": "2024-01-17 16:38:55Z",
      "file_count": 1,
      "partner": "cinx",
      "status_code": 200,
      "status_message": "Processed",
      "cinx_id": {
        "id": "97b96860-ca73-4f8e-b6ba-37ce9f256871",
        "domain": "pig",
        "type": "PIG-UPLOAD"
      }
    }
  ]
}

```

> A successfully processed PIG job returns JSON structured like this:

When you submit a Partner Integration Gateway (PIG) job, you get a response like this. Critical is the job_id, which is used in the subsequent status call.

To get the status of a job, you call:

URL Pattern: **{api path}/{api version}/partner/exec/{job id}/status**

Sample Call: **{api path}/1.0/partner/exec/69151a1e-ac43-4355-ba14-ea9d148a6633/status**

* Note: This is a VERSION 1.0 API call.

```json
{
    "response": {
        "status_code": 500,
        "message": "Failed to find a job with the given id of [7ab6f316-39bb-4d02-92aa-c9cfd8eeeb11]",
        "method": "App\\Controllers\\Auth->authenticate",
        "uri": "sub/d4cdf53d-1e7d-7cf9-8cbe-94d194241980/partner/exec/7ab6f316-39bb-4d02-92aa-c9cfd8eeeb11/status",
        "format": "json",
        "start_time": 1719524513.524035,
        "total_time": 0.2764439582824707,
        "record_count": 0,
        "total_count": 0
    },
    "rows": []
}
```
> A call with an invalid Job Id

### Call with missing/invalid Job Id

The `rows` array will be empty. The `response.status_code` will not be 200. 


```json
{
  "response": {
    "status_code": 200,
    "message": "OK",
    "method": "App\\Controllers\\Auth->authenticate",
    "uri": "",
    "format": "json",
    "start_time": 1719584394.89486,
    "total_time": 3.177053928375244,
    "record_count": 1,
    "total_count": 0
  },
  "rows": [
    {
      "app": "json-rfq-import",
      "args": {
        "body": ["json"],
        "auto_submit": ["1"],
        "api_version": "2.0",
        "app_cdoc": ["couchdb://apps/2d4dde95cc7d1a3d8e830036ff126f60"],
        "org_cdoc": ["couchdb://orgs/org-unit-test"],
        "org_name": ["PSF Mechanical, Inc."],
        "user_cdoc": ["couchdb://users/CINX-SYSTEM"],
        "user_id": ["2260bc39-5871-4e13-87c6-afd3bfc7519e"],
        "user_name": ["USER TEST"],
        "archive": [1],
        "sub_id": ["93b09b7f-becd-4dd7-801d-80f0f45fa5ab"]
      },
      "command_started_at": "2024-01-17 16:38:55Z",
      "file_count": 1,
      "partner": "cinx",
      "status_code": 500,
      "status_message": "Internal Server Error",
      "cinx_id": {
        "id": "97b96860-ca73-4f8e-b6ba-37ce9f256871",
        "domain": "pig",
        "type": "PIG-UPLOAD"
      }
    }
  ]
}



```

> The above is a call with a valid pig job ID, but the job has failed. Note the
> `status_code` and `status_message`.

### Call with a failed PIG Job

The key fields to examine are the `status_code` and `status_message` in the first record in the rows array. If the `status_code` is 200 and the `status_message` is 'Processed', the job has completed successfully. If the `status_code` is 500, then the job was attempted and failed. The `status_message` in this case will be 'Internal Server Error'.


