Returns the audit trail log for the account.  
Can be filtered for specific actions, model types or models.

#### GET  
`/audit/`  
Returns the audit trail  

##### Parameters:  
`type`   
The type of log item. One of:  
* CREATE
* UPDATE
* DELETE
* PURGE
* LOGIN
* LOGOUT

`model_type`  
The type of model (Contact|Company|etc.)  

`model_id`  
The UUID for a specific model
