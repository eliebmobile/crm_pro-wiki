# Account Migration into CRMPro

Accounts are migrated as requested from the old freecrm database. All imported accounts receive
the default `freecrm` template as their starting point, which mimics the legacy application but 
as soon as custom fields are available the template will be automatically modified to reflect this.
Most accounts migrated will then have their own custom model template available to them. 

## Migration Paths
There are two paths to perform a migration:

1. Via Freecrm, select to migrate your account. This is useful if the user did not yet register a 
new crmpro account. If the account's creator email already exists, this process will fail and 
prompt you to attempt the second path.
 
2. Via CRMpro, log in and select to migrate your account from freecrm. This will require you to 
provide the login for your freecrm account and will import to your already existing crmpro account.
 
## Data Migrated

We attempt to migrate all available data that is relevant in the new system with the following 
exceptions below. All users are moved over, including inactive and deleted ones. 

These items are not migrated: 

* Account Blocks
* Historic billing history
* Knowledge Base
* Data Confirmation requests
* Email campaign history
* Employee Unavailability
* Home Box Configuration
* Import Logs
* Import Mapping
* Tab/Menu Configuration
* Pending email campaign queue
* Company resources

These items might not be migrated:

* Alerts
* Custom Views
* Feedback Forms
* Flagged Records
* Record logs
* Print Campaigns


## Dropped fields

Certain fields in the legacy freecrm app might not be required. The default template 
omits the fields listed below, but if data exists for a migrated account they will be created
as custom fields:

#### Contacts
* suffix
* title
* birthday
