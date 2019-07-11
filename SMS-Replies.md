When sending out SMS campaign messages, like any other campaign transport, the contact has the option to reply to the message. The first and default reply option is to unsubscribe from the campaign or unsubscribe from all future campaigns. 

SMS replies are defined as Actions. The only action implemented at the moment is the `Stop` action which removes a contact from a campaign or from all future campaigns by setting the `do_not_text` flag of the contact to `True`. When a reply arrives through a Twilio registered number, Twilio will notify us via the `/hooks/twilio/` endpoint. If the reply's first word resolves to a configured Action object it will be called. 

### SMS Actions

#### Stop 

Format:   
  `STOP` : remove from this campaign  
  `STOP ALL` : Set do not text flag to True - remove from this and all future campaigns.

