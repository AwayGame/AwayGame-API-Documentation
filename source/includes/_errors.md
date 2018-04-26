# Errors

The AwayGame API uses the following error codes:

Error Code | Meaning
---------- | -------
422 | Unprocessable Entity -- Your request is missing data
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The endpoint requested is hidden for administrators only.
404 | Not Found -- The specified endpoint could not be found.
429 | Too Many Requests
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
