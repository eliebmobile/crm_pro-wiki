### Base Assumptions
* The user name is the email address
* Email must be unique
* 30 days free trial
* Sessions never expire unless the user explicitly logs out
* Login is possible using an email/password combo or login links emailed to the user
* Login links last for 15 minutes, after which a new one needs to be issued. 

### Registration Process

Registration begins with a user providing his/hers email address + captcha. If not already present in the database the user is then sent a validation email with a link to both confirm the email and log the user into the CRM.   
Once logged in the user can then provide additional information like his name, company name, password, as well as invite additional team members to the system by sending them invitation emails with special *login* links.

### Amendment 3.7.17
  
* Users will first pass a SMS challenge to establish valid mobile number + country
* Once passed SMS challenge, user does email captcha challenge
* Final user is locked out 30 days later unless upgraded to Pro.
* Day 25 user gets alerted to close 30.

### Billing Cycle 
Once the user has set his basic information, we register the user with Stripe for a subscription based monthly billing cycle, with a free month as trial. Once the free month completes the user will be billed. During that month the user should input his credit card details into the system.  
If the free month ends and the user has not yet filled in payment details, the account will be blocked until payment is sorted out.  

Any occurrence of delinquency in payments will result in an immediate and automatic account block, incurring charges per month until the block is lifted by paying any outstanding amounts.  

See also [Post Registration](/crmasp/crmpro/wiki/Post-Registration)