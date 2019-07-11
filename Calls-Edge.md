Get and Update call records.

#### GET:
`/calls/`  
`/calls/{UUID}/`  
Return multiple or single call records

##### Parameters 
`filter` can be provided with search data following the [JSON filter spec](/crmasp/crmpro/wiki/Dynamic-Model-Filtering).

#### POST
`/calls/{UUID}/`  
`/calls/`

Create or update a call record.

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


## Get Call Documents

To return all the documents relating to a call, use this edge:  

`/calls/{CALL_UUID}/documents`

