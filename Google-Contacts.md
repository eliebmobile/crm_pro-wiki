There are two ways to import Google contacts: 

* ***Contact import***  
imports just the user's contacts as defined in their contact section of their GMail account. This method allows for read and write access to get contacts as well as update them. More on that in the google dos [here](https://developers.google.com/google-apps/contacts/v3/?hl=en_US)

* ***People import***  
A combination of all data gathered about a user's connections, from various sources including contacts, Google+ profiles, domain data from Google Apps and whatever other Google related data source. This resource is read only. This is described in detail [here](https://developers.google.com/people/api/rest/)

When importing contacts/people from Google initially, the import process searches existing contacts for a person with the same email address. If found that record will be updated instead of creating a new contact. The `aux_id` will be set to that contact/person Google id. At this point the two records are bound.  

Since the People API will replace the Contacts API in the future, we will be using the People API to perform the sync. The API returns multiple values (potentially) for each field, but only one is marked as Primary and that is the one we'll use. We can allow the user to determine which *source of truth* they would like use for the import. 