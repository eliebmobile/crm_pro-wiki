Dynamic models can be queried using their local built in fields or any field in the dynamic template. 
The DynamicModelFilter object is used to take a filter from user input and convert it into a model query that will return results. 

Filters are a map of keys whose values are either the filtered value required or a map with an operator to match the value against. Valid operators are `eq`, `contains`, `gt`, `gte`, `lt`, `lte`, `startswith`, `endswith`, `has_all`, `has_any`. When no operator is defined (the value is a string), `eq` is used as default. Searches are case insensitive.

The filter map can also contain an `exclude` key. This is used to exclude records from the query.   

The filter structure is as follows: 

```
[
        {
            'and': [
                {'name': 'field_name', 'operator': 'contains', 'value': 'search value'}
            ],
            'or': [
                {'name': 'field_name', 'operator': 'contains', 'value': 'search value'}
            ]
        },
        {
            'exclude: [
                {'name': 'field_name', 'operator': 'contains', 'value': 'search value'}
            ]
        }
    ]
```

### Sorting 

In order to control sort order of the returned results, add the `sort` query parameter which contains a sort key and optional direction modifier. By default sorting is done in Ascending order. To get it in Descending order, prefix the key with a `-` symbol.  

`sort=first_name` : Sort by first name ascending   
`sort=-last_name` : Sort by last name descending  