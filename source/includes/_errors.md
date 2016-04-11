# Errors

The SWCE API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid
401 | Unauthorized -- Your API key is not valid
403 | Forbidden -- The endpoint requested is hidden for administrators only
404 | Not Found -- The specified item could not be found
405 | Method Not Allowed -- You tried to access a item with an invalid method
406 | Not Acceptable -- You requested a format that isn't json or xml
429 | Too Many Requests -- You have been rate limited.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
