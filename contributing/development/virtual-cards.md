---
description: How to setup Virtual Cards in local development
---

# Virtual Cards

{% hint style="warning" %}
This documentation is about development. To setup a production environment, see [https://docs.opencollective.com/help/fiscal-hosts/virtual-cards](https://docs.opencollective.com/help/fiscal-hosts/virtual-cards)
{% endhint %}

## Setup privacy in development

1. Create an account on [https://privacy.com](https://privacy.com)
2. Go to [https://privacy.com/account](https://privacy.com/account), scroll down to "Enable API", toggle the switch, click on Sandbox and copy the Sandbox API key (**NOT THE PRODUCTION ONE**)

![](<../../.gitbook/assets/image (16) (1) (1).png>)

3\. Connect to the database with your favorite tool (psql, DBeaver, Postico, etc.) and search for the host you want to enable Privacy for. Edit its `settings` to set `features.privacyVcc` to `true`

4\. Open the host settings and go to the "Fiscal host settings" > "Sending Money" section

5\. Paste your API Key in the "API Key" field and click on "Connect Privacy".
