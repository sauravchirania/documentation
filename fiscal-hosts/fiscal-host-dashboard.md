# Fiscal Host Dashboard

**The Fiscal Host Dashboard is your one-stop-shop for seeing all the information and completing your actions as host admin.**

## How do I get to the Host Dashboard?

Click the **Dashboard** button on your host page, while logged in as host admin. This button is nested inside the **Actions** menu.

![Dashboard Button on Organization Page](../.gitbook/assets/fiscal_host_fiscal_host_dashboard_dashboard_2021-04-27.gif)

## What can I do on the host dashboard?

### Expenses

![](../.gitbook/assets/dashboard.jpeg)

**Filter**

* **Pending:** expense has been submitted but not yet approved by the Collective's core contributors
* **Approved:** Core Contributor has confirmed this expense is good to payout
* **Scheduled for Payment:** Host admin approved and the expense is being batched for payment
* **Processing:** expense was paid and it is being processed by the payment provider
* **Paid:** past expenses already complete

#### Go to Pay

Green button showing that an expense has been approved and there are sufficient funds. If you click this button, the pay expense modal will be displayed and you'll be able to pay for the expense using a suitable method.

![Pay Expense modal displayed for an expense submitted with Bank Account on a Host connected to Wise.](../.gitbook/assets/screenshot-from-2021-06-29-16-11-03.png)

The action button displayed in this modal will vary with the available integration the host have and the payout method selected by the user who submitted the expense.

In the case you're paying with PayPal, if you click the action button the expense will automatically be paid from the connected PayPal account. If you're using PayPal Payouts, the expense will be marked as Scheduled for Payment and automatically processed by the payment worker.

In the case you're paying with Wise, if you click the action button the expense will automatically be paid from your main Wise balance. If your Wise requires OTP authorization, the expense will be Scheduled for Payment and a banner will be displayed on top of your expenses list so you can pay all the scheduled expenses in a batch with a single validation.

![Scheduled Wise expenses are paid manually in batch with your account requires OTP authorization.](../.gitbook/assets/screenshot-from-2021-06-29-16-18-33.png)

#### Mark as Paid

Green button for manual payments. After paying via another method \(bank transfer, etc\), click this to deduct the amount for the Collective's budget in the system.

#### Edit

Host admins have permission to edit expenses at any time. For example, someone wasn't able to attach their receipt and emailed it instead, and you are adding it for them.

**Note:** If you edit an expense, it must be re-approved.

#### Open Expense

If you click the title of an individual expense, you will go to that expense's page. There, you can see all details and read or add [comments](../expenses-and-getting-paid/expense-comments.md).

#### Connect PayPal & refill balance

PayPal allows you to pre-approve $2,000 at a time to be paid through the API. This is a security feature. This means after you've paid out $2,000 in expenses, you need to refill the balance. If you try to pay an expense and get an error about the PayPal balance, it's time to refill.

When you click "refill balance" you will be prompted to log in to PayPal, and afterwards you'll be taken back to your dashboard.

You can see the connected PayPal account in the top right. This is the account expenses will be paid out of.

If you manage multiple PayPal accounts, make sure it's the right one! If it's not correct, open PayPal in another tab and manually log out, then click "refill balance" and use credentials for the right account.

#### Payment Error Troubleshooting

Payment errors will show in red next to the expense if they come up.

Common reasons for a payment to fail after clicking the "Pay with PayPal" button:

* Need to refill the pre-approval balance
  * Click the 'refill balance' button
* Insufficient funds to cover fees
  * There are not enough funds in the Collective to pay this expense. Many Collectives submit expenses in anticipation of future funding.
  * If a user submits an expense for 100% of the Collective's balance, there won't be enough to cover processing fees
  * Edit the expense total down to leave enough for the fees and inform the user by leaving a comment
* User's PayPal account is restricted
  * Ask the user to log into PayPal and resolve the issue on their side

### Financial contributions

This section of the dashboard shows all of your incoming contributions. You can filter this section by Period, Amount and Status. 

![](../.gitbook/assets/image%20%287%29.png)

### Pending applications

This section on the dashboard shows all of your current pending applications to join your fiscal host. You are able to see the Title, Admins, Purpose, Application message and Email of the Collective. You can then Approve or Reject their application. 

![](../.gitbook/assets/image%20%2844%29.png)

### Manage hosted Collectives and set custom fees

You can access a list of all your hosted Collectives by clicking on the **Hosted Collectives** tab. With the first dropdown menu, you can sort them by the period of time you've hosted them from the most recent to oldest and oldest to most recent. You can also filter them by fee structure: by **global host fee** or **custom fee**.

![](../.gitbook/assets/fiscal-host_fiscal-host-dashboard_manage_collectives_2020-08-12.png)

To add a custom fee to a specific Collective, either find them listed on the page or look for them by name on the search bar. Once you find the right Collective, click on the **Fee structure** button \(the one with a set of lines\).

![](../.gitbook/assets/fiscal-host_fiscal-host-dashboard_custom-fees_2020-08-12.gif)

You will be prompted to either choose your global fee structure or to create a custom fee for this specific Collective. Don't forget to save your changes!

