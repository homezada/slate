# Errors

The HomeZada Partner API uses the following error codes at the HTTP request level:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is incorrect or not recognized.
403 | Forbidden -- The request is hidden for administrators only.
404 | Not Found -- The specified data could not be found.
405 | Method Not Allowed -- You tried to access data with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json api compliant.
410 | Gone -- The data requested has been removed from our servers.
429 | Too Many Requests -- The API is being throttled, and will require longer delays between calls.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

The JSON data supplied returned in any error response will provide additional info as shown in the example on the right.

> An JSON API error example, for HTTP/1.1 404 Not Found

```json
{
  errors:
  [
    {
      title: "Record not found",
      detail: "The record identified by 123 could not be found.",
      code: "RECORD_NOT_FOUND",
      status:"404"
    }
  ]
}
````

The JSON API returns the following error codes.

Error Code Text | Internal Code 
-----------|---------
VALIDATION_ERROR | '100' 
INVALID_RESOURCE | '101' 
FILTER_NOT_ALLOWED | '102'
INVALID_FIELD_VALUE | '103'
INVALID_FIELD | '104'
PARAM_NOT_ALLOWED | '105'
PARAM_MISSING | '106'
INVALID_FILTER_VALUE | '107'
KEY_ORDER_MISMATCH | '109'
KEY_NOT_INCLUDED_IN_URL | '110'
INVALID_INCLUDE | '112'
RELATION_EXISTS | '113'
INVALID_SORT_CRITERIA | '114'
INVALID_LINKS_OBJECT | '115'
TYPE_MISMATCH | '116'
INVALID_PAGE_OBJECT | '117'
INVALID_PAGE_VALUE | '118'
INVALID_FIELD_FORMAT | '119'
INVALID_FILTERS_SYNTAX | '120'
SAVE_FAILED | '121'
INVALID_DATA_FORMAT | '122'
INVALID_RELATIONSHIP | '123'
BAD_REQUEST | '400'
FORBIDDEN | '403'
RECORD_NOT_FOUND | '404'
NOT_ACCEPTABLE | '406'
UNSUPPORTED_MEDIA_TYPE | '415'
LOCKED | '423'
INTERNAL_SERVER_ERROR | '500'


