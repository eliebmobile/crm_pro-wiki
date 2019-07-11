Get and update event records

#### GET
`/events/`  
`/events/{EVENT_UUID}`   

Return a single event record  

##### Parameters:
`filter` can be provided with search data following the [JSON filter spec](/crmasp/crmpro/wiki/Dynamic-Model-Filtering).


#### POST
`/events/`  
`/events/{EVENT_UUID}`  
Create or Update an event record.  

Event data can contain information on assigned users and contacts,
recurrence rules, and any additional template based fields for this model.  

Assignment to users is done via the `assigned_to` key, which is a list of maps containing the user id.  
Contacts can be added using the `participants` key list, where each item is a map containing 
the contact UUID  

##### Recurrence  
Recurrence can be set via the recurrence map.   
The event start_date represents the beginning and time of the recurrence.  

```
{
    "weekdays": [0,1,2,3,4,5,6],
    "interval": 1,
    "interval_unit": "DAILY|WEEKLY|MONTHLY|YEARLY",
    "end_count": 3,
    "end_date": "2015-12-01"
}
```

###### Parameters  
`weekdays` represents which days of the week this event recurs at, with Monday=0, Tuesday=1 etc.
`interval` represents how many times recurrences are in the `interval_unit`, while `end_date` 
and `end_count` control how many or until when this event recurs.   
Note that `end_count` and `end_date` are mutually exclusive with end_date taking precedence.  

###### Examples
This recurrence happens weekly every Monday and Wednesday, until Christmas.
```
{
    "weekdays": [0,2],
    "interval": 1,
    "interval_unit": "WEEKLY",
    "end_date": "2015-12-25"
}
```

And this recurrence represents a birthday happening every year on the 24th of April 
(which is the start_date of the event):   
```
{
    "interval": 1,
    "interval_unit": "YEARLY",
}
```


##### Create an event without recurrence

```
    {
        "title": "My Event",
        "description": "This is my event. there are many like it but this one is mine.",
        "start_date": "2015-06-11T13:00Z",
        "end_date": "2015-06-11T14:30Z",
        "assigned_to": [
            { "id": 1}
        ],
        "participants": [
            {"id": "14c65a56-4599-4bca-859f-ae7ea447ff25"  }
        ]
    }
```

##### Create an event with recurrence

```
    {
        "title": "My Event",
        "description": "This is my event. there are many like it but this one is mine.",
        "start_date": "2015-06-11T13:00Z",
        "end_date": "2015-06-11T14:30Z",
        "assigned_to": [
            { "id": 1}
        ],
        "participants": [
            {"id": "14c65a56-4599-4bca-859f-ae7ea447ff25"  }
        ],
        "recurrence": {
            "weekdays": [0,2],
            "interval": 1,
            "interval_unit": "WEEKLY",
            "end_date": "2015-12-25"
        }
    }
```

### Add and Remove Participants

Event participants can be system users and/or contacts. The can be added and removed from an event by using this edge:   

`/events/{EVENT_UUID}/add/`  
`/events/{EVENT_UUID}/remove/`  

##### Parameters  
`contact_id`:  A comma separated list of contact UUIDs  
`user_id`: A comma separated list of user ids  


## Get Event Documents

To return all the documents relating to an event, use this edge:  

`/events/{EVENT_UUID}/documents`

