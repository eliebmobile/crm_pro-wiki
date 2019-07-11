Events appear on the calendar. They contain a start and end date, can span multiple days, or be designated full day events (time-less). 

Events can be recurring events. To the user a recurring event appears at the same day and time based on the recurrence criteria. In the back end recurring events are fetched and 'stretched' as ghost events into the fetched date range. For example, when getting a month's worth of events, and having a recurring event every Monday morning, that event will be duplicated into the API results.  
If a user updates a recurring event *instance*, only then its created as its own event record.

Events are connected to contacts and users. Each can designate confirmation of his/hers attendance.  

Events are also connected to a (single) job, case or task.

Integration with Google Calendar is a must

## Recurrence

Events can be set to reoccur - i.e., they will happen from that day onwards, at the same time at various intervals. Recurrence is saved as a JSON data in the event model.  
The JSON contains the following fields (or sensible combinations of):

* `weekdays`: Python day numberes where Monday is 0, and Sunday is 6. Designating days of the week the event happens at. [0,2] = "Every Monday and Wednesday".
* `interval_unit`: WEEK|MONTH|YEAR - the scale of the interval field
* `interval`: Number of `interval_unit` between events. E.g., 2/WEEK = Every 2 weeks, 1/WEEK = Every week, 1/MONTH = Every Month.
* `end_date`: End date for the recurrence
* `end_count`: End after *n* number of recurrences (note end_date/count cannot be set together).
* `

### Recurrence Examples

Repeat every working weekday, until Septermber 2015  
```
{
  "weekdays": [0,1,2,3,4],
  "interval_unit": "WEEK",
  "interval": 1, 
  "end_date": '2015-09-01'
}
```

Repeat every year weekday on the event date. (Birthday?)  
```
{ 
  "interval_unit": "YEAR",
  "interval": 1
}
```

Repeat every month on a Monday  
```
{
  "weekdays": [0],
  "interval_unit": "MONTH",
  "interval": 1
}
```

### Events as Time Markers
Many records in the system have a relationship with time. Deals might have a close date, tasks a deadline, calls a call date etc.  In order for such time markers to appear in the calendar, an event record is created automatically if the user chooses to mark that event in the calendar.  
If an original record is deleted, so will its events.  
This ensures a consistency in the calendar where only events are allowed to represent calendar events. 
