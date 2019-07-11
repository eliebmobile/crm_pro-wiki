Communication Channels define all the methods a contact can be contacted outside of a physical address. These include Email, Phone, Mobile, Social Network handles, Skype etc.  
A contact can have multiple channels of the same type but only one can be set to a default of each type.  

#### Email
All email addresses are validated before entry into the database. A user cannot set an invalid email on a contact. 

#### Phone
When determining a contact's phone number the country of the phone number is assumed to be the one set in the account settings as `default_phone_country`. Otherwise the specified country code is used.  
All phone numbers must be able to format as E.164 standard and are saved in that format to the database. 
The E.164 format includes the country code in the number prefixed by a `+` symbol.  
For example, a US number would look like `+14157618273` while a UK one `+447794736151`. Phones that cannot be converted to that format will be deemed invalid and not used. 