Note that all model types can relate to all other model types.

## Contact

A person in the system. Contacts have a first and last name. The rest of the fields are defined by the template used by the account.  
NOTE: To be decided: Contacts have a fixed type selection to determine the status of the contact: Lead, Qualified Lead, Disqualified Lead, Lost Lead etc. 

## Company

A company in the system. A company might be (non exclusively) connected to one or more contacts (employees). 

## Address 

A physical location that can be attached to a contact or a company. Note that Address models are mixins that can be applied to any other model type. 

## Communication Channels

A non physical way to reach a contact or company, like a phone number, email address, fax etc. As the case with addresses, those are also mixins that can be applied to any model type. 

## Deal

A deal performed with one or more contacts and/or a company. A deal has a monetary value which is defined by a collection of *Products* or *Services* attached to the deal. 

## Task

An arbitrary task to perform by one or more contacts. A task can also be related to other models such as deals or cases. 

## Case 

A problem/issue originating from a contact or company which is to be resolved. e.g., a support case. 

## Call 

A log for a telephone call to a contact

## Document

A document stored on the system

## Product

A product or a service that has a monetary value and can be part of a deal.

## Campaign

A bulk sendout of information to contacts via email, sms, other other means. 
