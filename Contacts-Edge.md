Get and Update contact records.

#### GET:
`/contacts/`  
`/contacts/{UUID}/`  
Return multiple or single contact records

##### Parameters 
`filter` can be provided with search data following the [JSON filter spec](/crmasp/crmpro/wiki/Dynamic-Model-Filtering).

#### POST
`/contacts/{UUID}/`  
`/contacts/`

Create or update a contact record.
The contact data sent can contain auxiliary data like communication channels and addresses.  
The data fields sent must correspond to the Contact's model template stored in the account.
Note that address blocks require valid address keys and must include at least one key to be valid.
Communication channels must include both the channel type and value fields. An optional default key
can set the channel to the default one.

Data sent to the server should be based on the following example below.

```
{
    "first_name": "John",
    "last_name": "Smith",
    "some": "field",
    "another": "field",
    "channels": [
        { "channel_type": "PHONE", "value":"077931111234", "default": true},
        { "channel_type": "EMAIL", "value":"harel@harelmalka.com"}
    ],
    "addresses": [
        {
            "address": "123 Side Street",
            "city": "Saint Fanta",
            "country": "US",
            "state": "CA",
            "zip": "123999"
        }
    ]
}
```

#### Response

The response contains the new contact data and a report detailing any problems or concerns during
the contact creation. If any non template fields were provided they will be omitted and reported
back in that data.

## Get Contact Documents

To return all the documents relating to a contact, use this edge:  

`/contacts/{CONTACT_UUID}/documents`

