The actual registration process is streamlined and only requires an email address.  
However there are additional details we need to capture before the user can use the system.  
Once the user logged in for the first time, we present a form or wizard that captures the following information: 

* Selected Plan
* First and Last name
* Account or Company Name
* Credit Card Information

Part of this process is to create a Stripe customer record for this account.  
The request can only be performed once per account (once successful) and will be rejected for accounts that have already gone through the process.  

See [Post Registration](/crmasp/crmpro/wiki/Post-Registration-Edge) for the spec of this request. 