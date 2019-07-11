Calls are initiated via their respective CRMpro call records.  
The flow is as follows:  

* User creates a call record either explicitly or by clicking the call icon from a contact page or listing. 
* Once the call record is saved the user can initiate the physical call. 
* The application will then issue an outgoing call via the account's Twilio sub account to the **initiator's** phone number. The response of this request will contain the new call sid which is then saved against the local call record. 
* Twilio will initiate the call and in turn Twilio will do a POST request to the Twilio call hook endpoint at `/hooks/callresponse/`. 
* The request will contain the new call status and call sid which will then ensure the local call record is updated. 
* The response of the hook instructs Twilio to dial the target number at this point. Once the call is initiated additional events are sent to the hook endpoint which cause the call record to be updated. 
* Once the call is completed the final event is sent to `/hooks/callstatus/`. 
* All this time we maintain a proactive connection to Twilio to inquire about the call progress and status. As well a backend process will ensure all calls with a sid but with an out of date status are updated via Twilio (to account for scenarios where the UI is closed etc.)
* The call final cost is reduced from the account's own internal balance. 

## Notes
* During the call the user can add additional contacts to the call at any time, thus generating a conference call.  
* If the user's time zone is set and the call time is not civil, the user will be alerted before the call is initiated. 
* All calls are recorded by default. The recording is fetched locally and stored on our servers. 