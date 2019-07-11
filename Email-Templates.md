Email templates, and all other content templates, are parsed as [Mustache](https://mustache.github.io/) templates. 

Tags look like this: `{{contact:first_name}}` and support is there for list loops and conditional presentation based on existing or non existing values, as supported by Mustache. 

The editor used in the UI is Alloy Editor which is based on CKEditor under the hood. The editor has been extended to include selectors for all available tags based on the user's model templates. 

The tricky part of email templates in crmpro is managing images.  
Images are sent as embedded images which means the image tag refers to a `cid` based on the image file name while the image itself is attached to the email. Alloy editor itself supports displaying of images using their base64 encoded `data:` url. There for the backend should convert all image tags in a template to base64 `data` encoded images when loading templates for editing in the UI, but save them using the standard and shorted `cid` embedded attachments when storing them in the database or preparing them to be sent off. 

For example, if a user creates the following template:  

```
<h1>Hello {{contact:first_name}}</h1>  
Here is an image of a cat:  
<img src="data:image/png;base64,iVBORw0KGg..VERY LONG BASE64 STRING HERE.."/>
```

The template would have the image saved as an attachment in the user's templates dir, and the tag replaced with a corresponding `<img src="cid:filename.jpg"/>`. When loading the template to the UI for editing the reverse is done - the image is read, and converted to base64 string representation being sent to the browser. 
