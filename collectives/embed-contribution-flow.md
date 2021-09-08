---
description: To integrate a "Contribute" option directly on your website
---

# Embed contribution flow

{% hint style="warning" %}
This feature is currently in a beta-test phase. If you face any issue or need assistance, you can send a message on [Slack](https://slack.opencollective.com) \(\#﻿embed-contribution-flow channel\)
{% endhint %}

The embed contribution flow is a way to integrate Open Collective on your own website. Visitors will be able to contribute directly, by simply providing an email address.

![Embedded contribution on the website of an initiative](../.gitbook/assets/image%20%284%29.png)

## General considerations

* The widget will look better if it has some space, ideally the full page height & width
* The following URL parameters can be used to configure your integration:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Parameter</th>
      <th style="text-align:left">Value type</th>
      <th style="text-align:left">Default value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>useTheme</code>
      </td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">
        <p></p>
        <p>By default, the theme of your profile (defined by your primary color)
          will be used. If you rather want to use the default Open Collective theme,
          set this to <code>false</code>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>hideHeader</code>
      </td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left">false</td>
      <td style="text-align:left">Set this to <code>true</code> to hide the header at the top</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>disabedlPaymentMethodTypes</code>
      </td>
      <td style="text-align:left">[String]</td>
      <td style="text-align:left">null</td>
      <td style="text-align:left">A list of payment method types to disable. Example: <code>[CREDITCARD, MANUAL, CRYPTO]</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>tags</code>
      </td>
      <td style="text-align:left">[String]</td>
      <td style="text-align:left">null</td>
      <td style="text-align:left">
        <p>Some tags to attach to the orders. If you&apos;re embedding the contribution
          flow on multiple pages/websites, you can use this to track from where the
          contributions are coming from.</p>
        <p>Max number of tags: 30</p>
        <p>Max tag length: 32</p>
      </td>
    </tr>
  </tbody>
</table>

## Embed the default tier \(Donate\)

The simplest way to embed the contribution flow is by using the `/donate` URL \(e.g. [https://opencollective.com/babel/donate](https://opencollective.com/babel/donate)\). Just replace `COLLECTIVE_SLUG` by your collective slug below:

```markup
<iframe src="https://opencollective.com/embed/COLLECTIVE_SLUG/donate" style="width: 100%; min-height: 100vh;"></iframe>
```

## Embed a specific tier

To embed a specific tier, you'll need to know its ID. For that, go to your profile page, click on "Contribute" for the tier you want to embed then check the URL. It should look like `https://opencollective.com/COLLECTIVE_SLUG/contribute/TIER_SLUG-TIER_ID/checkout`

From this URL, you can deduct the embedded one \(prefix with `embed` and removes `/checkout`\):

```markup
<iframe src="https://opencollective.com/embed/COLLECTIVE_SLUG/contribute/TIER_SLUG-TIER_ID" style="width: 100%; min-height: 100vh;"></iframe>
```

