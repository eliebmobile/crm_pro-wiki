All access to the API is done by supplying an auth token in the header or as a request parameter. Each request is authenticated against that token. The UI itself is a client of the API and as such, also has to supply the token for each request. 

## Users

Upon registration, a Super User is created. That user is able to create additional users and assign roles to them. The roles define which resources users can access. 

## Roles

CRMpro uses a Role based security scheme, where different roles are defined and assigned various permissions.  
The roles are as follows:  
* `SuperUser`: All permissions are set and allowed. 
* `ContactManagerRole`: Can create, edit and delete contacts
* `ContactReaderRole`: Can read contact data 
* `CompanyManager`: Can create, edit and delete companies
* `CompanyReaderRole`: Can read company data 
* `DealManagerRole`: Can create, edit and delete deals
* `DealReaderRole`: Can read deal data 
* `TaskManagerRole`: Can create, edit and delete tasks.
* `TaskReaderRole`: Can read task data
* `CaseManagerRole`: Can create, edit and delete cases
* `CaseReaderRole`: Can read case data
* `CallManagerRole`: Can create, edit and delete calls
* `CallReaderRole`: Can read call data
* `DocumentManagerRole`: Can create, upload, edit and delete documents
* `DocumentReaderRole`: Can read and download documents 
* `EventManagerRole`: Can create, edit and delete events
* `EventReaderRole`: Can read events
* `EmailCampaignManager`: Can execute, create, edit and delete email campaings
* `EmailCampaignReaderRole`: Can read email campaign data
* `EmailCampaignExecuterRole`: Can execute email campaigns
* `MetaDataEditorRole`: Can modify the model data templates
* `ReportManagerRole`: Can generate reports
* `ReportReaderRole`: Can execute and get reports 
* `AccessAllDataRole`: Can access all records


## Data Access Restrictions

Besides defining access to resources using the roles, they can also be used to restrict access to data. Any record can be marked *private*, in which case only its owner, assignees or an Admin class role can modify or read it. 