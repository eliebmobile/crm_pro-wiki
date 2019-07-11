An account can be cancelled at any time by a user admin.  
By default the account is not deleted from the system upon cancellation. Instead it is marked as deleted with a date matching the current billion period end date, and it will be purged `n` number of days after that, where `n` is configured in `settings.ACCOUNT_PURGE_DAYS`. This allows the user time to revert their decision. As well as a refund is not issues when cancelling within a billing period, and there fort the current month is paid for.

When an account is created a 12 character cancellation code is generated. When a user wishes to cancel their account the code is either emailed to them or shown on the screen, and they are required to enter it exactly as shown to confirm their decision to cancel the account.  The user then has a choice to purge all data on the spot (not undo-able) or let the account sit out the grace period and unless reverted. Once the grace period is over, the account will be purged from the system along with all users and data. 

Billing for the period is *not* automatically refunded. 
