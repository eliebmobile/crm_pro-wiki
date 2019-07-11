Telephony is handled by the default telephony transport using Twilio as the platform backend.  
All accounts on the CRM that require telephony services are created sub account under the CRMpro Twilio account. 
Each of those sub accounts is represented by a TwilioAccount instance which holds the relevant account sid and tokens.  

Each account has a telephony balance which can be topped up and is used to perform various billable telephony events, from making outgoing calls, receiving them etc.  Once the balance is depleted, telephony services will be suspended until it is topped up.  
Auto top-up is possible where the user determines the account is to be topped up automatically once a balance drops beneath a certain threshold. 

## Number Validation
Before telephony services can be used the account needs to opt in to the telephony plan. At this point a sub account is created locally and with twilio. The local sub account contains the required API keys needed to communicate with Twilio for that specific account. 

Each account user will need to enter his primary phone number and then validate it via an automated voice call. Once validated, and the account balance is topped up the user can start making calls. 

## Sub Account Management

An account Twilio sub account is represented with a 1-1 relationship to a TwilioAccount. The TwilioAccount contains the sid and account token required to access the Twilio api. 
Every local call record contains the duration and twilio cost of the call. A background process ensures that data is synched across with Twilio to avoid discrepancies. 

