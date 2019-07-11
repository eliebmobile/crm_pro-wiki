Each account can define its own custom fields for each [model type](https://github.com/eliebmobile/crm_pro-wiki/blob/master/Model-Types.md), the Meta Data calls allow the user to retrieve and set those fields on the account templates. 

#### GET
`/templates/{MODEL_TYPE}/`   
Retrieve the template for this model type.  
{MODEL_TYPE} can be one of:  
* contact
* company
* deal
* task
* case
* call
* document
* event

#### Response

Response will contain all of the meta data for the requested model.  
The order of the fields in the `fields` key determines the rendering order of the fields in a UI.  

```
{
  "process_time": 0.01542210578918457,
  "response": {
    "results": {
      "Contact": {
        "fields": [
          {
            "max_length": 30,
            "required": false,
            "type": "string",
            "name": "car",
            "label": "Car Make"
          },
          {
            "name": "face",
            "required": true,
            "label": "Face Quality",
            "empty_text": "Select Face",
            "type": "options",
            "options": [
              "Nice",
              "Not Very Nice"
            ]
          },
          {
            "range": [
              5,
              10
            ],
            "required": false,
            "type": "integer",
            "name": "num_of_cats",
            "label": "How Many Kittens"
          },
          {
            "required": false,
            "type": "string",
            "name": "mental_state",
            "label": "Mental State"
          },
          {
            "required": false,
            "type": "date",
            "name": "date_of_last_visit",
            "label": "Date of last visit"
          }
        ]
      }
    },
    "success": true
  }
}
```


#### POST
`/templates/{MODEL_TYPE}/`   

Get model templates.
 
#### POST
`/templates/{MODEL_TYPE}/`

Add or update a field in this template. If a field name is supplied and already exists it will be updated.  

##### Parameters:
`field` a JSON value with field parameters
`position` - optional position for the new field. If not provided the field is added to end of the field list.
