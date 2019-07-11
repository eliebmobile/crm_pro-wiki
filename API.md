All access is provided via an API. Access requires a token in the header of the request and data is provided back as JSON.  

Unless otherwise noted, POST data can be sent either as Form variables or as a JSON payload in the request body.  

* All API calls are prefixed with `/api/1`.*  
* All API calls should have a trailing forward slash `/`*
* Pagination is handled by `start` and `limit` query parameters. `limit` is optional and defaults to the account's setting or `settings.DEFAULT_PAGE_SIZE`.

 
 