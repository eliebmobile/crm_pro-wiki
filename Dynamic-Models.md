A Dynamic model is a model that defines a base set of fields, and allows any dynamically generated arbitrary set of fields to be added to it and changed at any time for different model instances. The Dynamic model is a base for any specialised models that require that functionality.  Its important to note that the dynamic aspect of the model relates to its instantiations across different users and accounts. For example, account A might define a Contact record with 5 additional fields beyond the built in name field, while account B might require a more elaborate set of 25 additional fields.  

All Dynamic models are based on the `core.models.DynamicModel` object. That model defines a fixed set of fields all extending models will share, as well as a `values` JSON field. In the background this JSON field is stored in a PostgreSQL JSONB field. The Dynamic model allows for getting and setting any field regardless if its a built-in model field or a dynamic mutable one stored in the `values` data structure. 

All Dynamic models are driven by a template; the `ModelTemplate` model. The template defines which additional fields are required for this model instance as well as meta data about their presentation and any additional requirements. The templates are associated with user accounts and are loaded with the model when required to determine which fields are available for this model instance. Although default templates are provided initially, an account can completely change the template to suit their needs.

Dynamic models also support the idea of a recycle bin for objects. When deleted, they are simply marked as such by setting the `deleted_at` date field to the time of deletion. They are then assumed to be in the Recycle Bin/Trash. Those deleted models can be deleted for good of course, but that has to be explicitly requested.

The fixed fields in all Dynamic Models are: 

* `id`: The primary key of the model is UUID field 
* `account`: The user `Account` this model belongs to
* `created_by`: The user who created this model
* `created_at`: The model creation time (UTC)
* `last_modified`: The model's last modification time (UTC)
* `deleted_at`: The model's deletion time (UTC). When not null, designates the object to be deleted.
* `values`: A JSONB backed JSON field holding all the dynamically generated fields for this model. 
* `batch_id`: A unique UUID to group objects by their method of insertion.
* `aux_ud`: An alternative id field. Useful when importing for external systems where the original id is required. 

For Dynamic Model filtering and querying, see here: https://github.com/crmasp/crmpro/wiki/Dynamic-Model-Filtering