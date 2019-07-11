### Content Templates
A campaign contains schedules of one or more templates. The template defines how the actual campaign output looks like per schedule. Each type of campaign might have a different configuration of a template, but in general the template itself is a dynamically generate text or html that is delivered to a Contact. 
For example, an Email campaign will have HTML or Plain Text templates while an SMS campaign will contain short terse messages.  
All templates can contain tags in the format of `$field_name` which are replaced with relevant values from each Contact record being sent to. For example, `$first_name` will be replaced with the Contact's first name. 

#### GET:
`/campaigns/templates/`
`/campaigns/templates/{TEMPLATE_UUID}/`

Get all or one specific template

##### Parameters 
* `type`: the type of templates to fetch when getting all templates. Can be one of `EMAIL` or `SMS`.

#### POST
`/campaigns/templates/`
`/campaigns/templates/{TEMPLATE_UUID}/`

Create or update a template.

##### Parameters
* `type`: The type of template. Can be one of `EMAIL` or `SMS` (required. Defaults to EMAIL)
* `name`: A name for this template for internal reference (required)
* `title`: The title of this template if applicable. For emails, this is the email subject.
* `template`: The contents of the actual template. For emails this is the rich HTML content, for SMS, the actual text message. 
* `plain_template`: Alternative plain text version of the template. Applicable for Emails only.

#### DELETE
`/campaigns/templates/{TEMPLATE_UUID}/`

Deletes a specific template


### Content Template Attachments

Show all attachments to a campaign template.  
Attachments can be either embedded images, ad-hoc file attachments or attachment of document records.

#### GET:
`/campaigns/templates/{TEMPLATE_UUID}/attachments/`  

Return a all attachments for this template

#### POST
`/campaigns/templates/{TEMPLATE_UUID}/attachments/`  
`/campaigns/templates/{TEMPLATE_UUID}/attachments/{ATTACHMENT_ID/`  

Add a file to this template. This POST request should be a `multipart/form-data` request that contains
a file in a key name `attachment`.

##### Parameters:
* `attachment`: The file field. Required for `EMBED` or `ATTACH`.
* `type`: The type of attachment file. One of `EMBED`, `ATTACH` or `DOCUMENT`.
  Defaults to EMBED.  When sending `EMBDED` or `ATTACH`, the attachment file is expected.
  If sending a DOCUMENT attachment, a document uuid is required
* `document_id`: A document uuid for when adding Document records as attachments.


#### DELETE
`/campaigns/templates/{TEMPLATE_UUID}/attachments/{ATTACHMENT_ID}/`  
Delete this attachment