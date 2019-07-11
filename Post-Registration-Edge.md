Update required user information after registration.  This edge is for internal use and is part of the setup process for a new account.  
Although the form which submits to this edge is ultimately part of the application, there is a convenience 
standard html form available as well.

#### GET:
`/register/completeinfoform/`  

Return the form containing all the required fields.

#### POST
This endpoint should be called once per account, and only once. It will be rejected if the account has already passed through this process. 

`/register/completeinfo/`

##### Parameters
The endpoint allows submitting the data in two parts or all together. Each parameter below is assigned a group (in __[SQUARE-BRACKETS]__) and the only restriction is that all fields of a group must be present for the data to be updated. 

* `plan_id`: The id of the plan selected. 
* `first_name`: User's first name
* `last_name`: User's last name
* `password`: User's new password
* `password_confirm`: Password confirmation. Should match `password`
* `account_name`: Account or company name
* `cc_name`: Credit card name
* `cc_number`: Credit card number
* `cc_exp`: Credit card expiration in 4 digit format
* `cc_cvv`: Credit card security code

