# Getting Started

## REST API
### ReST API

The CINX platform offers programmatic access to read and write data using ReST web services and standard HTTP verbs.

**Authentication & Headers**

HTTP Basic Authentication over HTTPS is used to control access to CINX platform resources.

With each API call, you’ll need to set request headers, including a CINX User’s User Name and Password.

**Account Authorization**

CINX accounts are subscription based and have expiration dates.  Accounts with expired subscriptions will not have access to CINX data.

**Production Endpoint**

The production endpoint for the CINX API is:

**https://api.cinx.com/**

**API Response Formatting – Standard/JSON**

All CINX API responses use a standardized format.  By default a JSON formatted response is provided.  Please see below if you prefer XML.

The **“response” object** will contain meta data about the server’s response to the request.

The **“rows” array** will contain the query results.

<code>
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
  "rows": [
    {
  ]
}
</code>

**API Response Formatting – XML**

To receive an XML response, please add the following parameter to the url:

**format=xml**

<code>
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
</code>

**Result Rows - Paging**

For many HTTP GET requests you can use URL parameters to define the number of rows returned in the response.  Valid input parameters are:

**start={number}**

**limit={number}**
