Once a user connects their email provider's account to the CRM, we'll proceed to periodically pull their emails and save any email to is relevant to an existing contact against their record. This will provide part of the electronic trail of this contact. 

Initially the user can choose to parse their entire email account to pull any historic messages and perform the same reference to contacts.


### Email Sync

Each user can turn on email sync. Sync runs multiple times a day and retrieves the last day's worth of emails. 
Email syncs are logged using the `EmailSyncHistory` model.  
The process below describes the Gmail sync flow but can be applied to any mail server with modifications:

* Query EmailSyncHistory to establish last sync date. If no records exist (first sync) fetch all.
* Establish a query filter to retrieve emails. In Gmail this is a string similar to `after:2016/5/6 before:2016/5/21`.
* Query the mail server via the API, Imap, POP3 etc. Retrieve partial messages (minimal set possible). Where possible get RAW RFC2822 email data and parse them through Python's `email.parser.Parser` object. From this point on the details should be same for every provider.
* For each message check if it already exists in our database using the Email.msg_id field. 
* If the Email does not exist, create it by fetching the full message first if required. 
* Ensures at least one contact exists for the email recipients. Emails that do not relate to existing
contacts are ignored. 
* Creates the local Email record while ensuring it is attached to all existing contacts in the database. 

