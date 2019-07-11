Data models contains the bare minimum built in fields. The rest is defined via templates. For example, a Contact model contains a First and Last name fields as built ins and everything else is constructed via the template associated with the model instance.  

Templates are defined as JSON data structures. Beside defining the fields of the model they also define the order and way they are to be presented in a UI as well as any other meta data relating to the model instance itself. Therefore its possible to have one set of Contact fields for a Contact model for one account, and a completely different set of fields on another.  

Its important to note that each model type has a certain number of *fixed* fields, though in *most* cases not all of them are required.  The order of the fields determines their order of display in forms and views.

When a field is created, a unique name is either provided or generated for it based on the given label. That name cannot be changed at a later time though it is only used for backend operations. The label can be changed at any time. As well, the field type cannot be altered. Fixed fields only allow changing the label and positional index of a field

## Template Spec

A template JSON contains the following structure:  
```
{
    "fields": [
         { field specs },
         { field specs },
         ...
    ]
}
```

## Field Specs

Field specs contain the following fields: 

* `fixed`: true|false if this field is a fixed field on the model, or template driven
* `name`: The name of the field. Only A-Za-z0-9 and underscores are allowed here. Normally this would be auto generated from the field's label.  
* `label`: The human friendly name of the field.
* `type`: The field's data type. One of:  
`text, numeric, range, date, time, datetime, options, lookup, money, user`
* `required`: true/false to determine if a field is required. 
* `hidden`: Optional true/false to hide a field from forms and views but retain it in the models  
* `colspan`: Optional true/false to determine if a field spans 2 columns in displays or just one.
* `sortable`: Optional true/false to determine if a field is sortable in the grid. Defaults to `true`

Certain data types allow for additional fields:

### text
* `max_length`: The maximum allowed length of this text. Omitting this key or setting it to 0 removes any length restrictions
* `large`: `true`|`false` if this is a long text entry. Represented as a textarea in forms.

### range
* `min`: The minimum allowed value in this range. 
* `max`: The maximum allowed value in this range.

### options
Options fields are drop down selections
* `options`: A list of options that can be used as a value. 
* `multiple`: When true, multiple values can be selected

### calendars
A specialised drop down that shows a user's calendars

### lookup  
This field is a lookup of another model type in the database.  
The database will always hold the id value alone but when models are read out it will be expanded to include the current name behind the id.  
In forms the field is represented as a auto completion lookup field. 

* `lookup`: The type of lookup. One of `Contact`, `Company`, `Deal`, `Case`, etc. (model types). 
* `multiple`: Allows multiple selection of the looked up model.

### user
This field is a user selector, showing a list of all of the account's users.  
* `multiple`: Allows multiple selection of users

### date (and datetime)
Represents a date or date and time value  
* `min`: Optional bottom end date
* `max`: Optional top end date

### recurrence
A specialised field for events to determine the event's recurrence. It's value is an object following the recurrence spec below:

`weekdays` represents which days of the week this event recurs at, with Monday=0, Tuesday=1 etc.
`interval` represents how many times recurrences are in the `interval_unit`, while `end_date`
and `end_count` control how many or until when this event recurs.
Note that `end_count` and `end_date` are mutually exclusive with end_date taking precedence.

```
{
    "weekdays": [0,1,2,3,4,5,6],
    "interval": 1,
    "interval_unit": "DAILY|WEEKLY|MONTHLY|YEARLY",
    "end_count": 3,
    "end_date": "2015-12-01"
}
```

For example, this recurrence happens weekly every Monday and Wednesday, until Christmas.
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