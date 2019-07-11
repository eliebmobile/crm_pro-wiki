Campaigns allow sending out messages in bulk to contacts.  
A campaign is a generic collection of a group of templates and schedules sent to contact, and as such its transport agnostic. A user can set up campaigns based on implemented transport methods. Currently `EMAIL` and `SMS` are to be implemented.  
Once created, the transport method cannot be modified, but the actual transport account used can be changed. For example, you can switch SMTP accounts for an EMAIL campaign but not change it to an SMS campaign.

### Contacts 

A campaign as an explicit connection to all subscribed contacts. However, each such connection can be deactivated for a specific contact, for example, if the contact fails delivery for `n` number of times.

### Templates

A campaign uses template to format messages to the contact. The templates should correspond to the type of campaign they are used in. You cannot use an Email template in an SMS campaign.  
Template can contain $tags based on the contact dictionary and use any value from the contact model. The template is parsed before shipping it to each contact.

### Schedules

A campaign is a collection of schedules. A schedule determines which template is to be sent, and when.  
Each schedule record in a campaign has a template and an interval which determines how long after the last sent schedule should this one be sent.  The first schedule is set with a zero interval meaning that 
when a contact is added to a campaign and a send is initiated, the contact will receive the first schedule in the campaign.  

### Schedule Send Log

Each send attempt is logged in a schedule send log record. The log contains the schedule of course and the status and date of the send attempt. Status can be either `OK` or `FAIL`. A number of attempts is also present and determine that a contact should be deactivated from the campaign if a message fails sending 3 times.  
