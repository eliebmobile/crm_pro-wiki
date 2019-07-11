### Stripe

Stripe is used to manage all subscription based billing. A `Customer` record is generated for each account, with an applied subscription to one of the billing plans. When an account admin adds or deletes users, the account's `quantity` field is updated on Stripe.  

Billing Plans on the system match Stripe Plans via the `code` attribute, which corresponds to the `id` attribute of Stripe's `Plan` object.  BillingPlan models can be synched to the current state of Stripe's ones by issuing a `BillingPlan.objects.sync_down_plans()` call or using the management command `./manage.py stripe_syncplans`.

## Quickbooks

Quickbooks sync:  company name sync to QB:Customers, via deals and view quickbooks and can also populate quickbooks like widgets in the CRM.  Deals is like Sales in Quickbooks Online.

Quickbooks actions: new invoice, new payment, new estimate, sales receipt, credit memo, delayed charge, time activity, statement.

## Facebook

Facebook should sync all FB contacts to the CRM and a FB panel of Contacts should somehow be available.  Each FB contact should be able to be a real person in Cogmento.  Name matching, email matching, etc. also possible & can suggest.  Create contact from FB Friend, etc.

CRM with FB Ads: https://www.facebook.com/business/help/1588743581429919
https://www.facebook.com/business/help/908902042493104
## Twitter

Twitter app should sync to account, let you tweet, see list of previous tweets, but most importantly schedule / automate Tweets.  Should let you add single TW account for now.

If a contact has a Twitter, we need a TW panel in the contact view.

