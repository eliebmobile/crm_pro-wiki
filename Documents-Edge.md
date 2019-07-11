Get and Update document records.

#### GET:
`/documents/`  
`/documents/{UUID}/`  
Return multiple or single document records

##### Parameters 
`filter` can be provided with search data following the [JSON filter spec](/crmasp/crmpro/wiki/Dynamic-Model-Filtering).

#### POST

POST requests should be sent as multi-part requests and contain a file upload in a field named `file`.
The document fields can include `title`, `description` and any other custom generated field.

`/documents/{UUID}/`  
`/documents/`

Create or update a document record.
Besides the document fields, the following parameters can be sent:

`model_id`: Creates/updates this document and assign it to this model id
`model_type`: The type of model the above id is from. One of (contact|company|call|event|case|task|deal).   

#### Response

The response contains the new document data and a report detailing any problems or concerns during
the contact creation. If any non template fields were provided they will be omitted and reported
back in that data.

## Assign Documents to Recrods

You can assign a Document record to any other record by calling this edge:

`/documents/{DOCUMENT_UUID}/assign/{MODEL_TYPE}/{MODEL_ID}/`

Where `MODEL_TYPE` can be one of: contact, company, case, deal, call, event and `MODEL_ID` is the UUID of the model to assign.