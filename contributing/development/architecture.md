# Architecture

## Collectives

In Open Collective, every entity is a collective and can be accessed publicly via their unique slug `https://opencollective.com/:slug`. In our public API, Collectives are usually refered to as `Accounts`. You can think about it like "profiles" that's what we really store in that table.

A Collective can be of type:

* **COLLECTIVE** e.g. [Webpack](https://opencollective.com/webpack)
* **EVENT** e.g. [BrusselsTogether Meetup 4](https://opencollective.com/brussels/together/events/meetup-4)
* **ORGANIZATION** e.g. [iDoneThis](https://opencollective.com/idonethis), [DigitalOcean](https://opencollective.com/digitalocean), etc.
* **USER** e.g. [xdamman](https://opencollective.com/xdamman)
* **PROJECT**
* **FUND**

## Members

A Member connects two profiles together. It can have multiple roles (one role per row):

* **HOST** legal holder of the bank account that holds the money on behalf of the collective
* **ADMIN** users who can approve expenses for the collective
* **MEMBER** aka core contributors
* **BACKER** users who gave money to the collective

## Orders

An Order is the intent to give money to an Account. It is created by a UserId on behalf of a collective (which can be their own UserCollective or any other Collective that they are a member of).

Attributes:

| Attribute        | Definition                        | Example                               |
| ---------------- | --------------------------------- | ------------------------------------- |
| UserCollectiveId | User who created the order        | /xdamman                              |
| FromCollectiveId | Source of the money               | /digitalocean                         |
| CollectiveId     | Destination of the money          | /webpack                              |
| currency         | currency of the ToCollectiveId    | USD                                   |
| amount           | amount in cents                   | 10000                                 |
| SubscriptionId   | References recurring subscription |                                       |
| status           | status of the order               | PENDING -> APPROVED\|REJECTED -> PAID |

## Transactions

A Transaction records money moving from one account to another ac. In this example, a collective [webpack](https://opencollective.com/webpack) is giving €100 to [Women Who Code Berlin](https://opencollective.com/wwcodeberlin) hosted by [Women Who Code 501(c)(3)](https://opencollective.com/wwcode).

| Attribute                          | Definition                                                                                                                                                      | Example                                        |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| OrderId                            | References the order                                                                                                                                            | 1                                              |
| FromCollectiveId                   | Source of the money (virtual account)                                                                                                                           | /webpack                                       |
| ToCollectiveId                     | Destination of the money (virtual account)                                                                                                                      | /wwcodeberlin                                  |
| PaymentMethodId                    | Payment method (e.g. if there wasn't enough funds in the `FromCollectiveId`)                                                                                    | `NULL`                                         |
| FromHostId                         | Source of the money                                                                                                                                             | /opensource                                    |
| ToHostId                           | Destination of the money                                                                                                                                        | /wwcode                                        |
| FromHostAmount                     | total amount in cents paid by the host of the `FromCollectiveId` in the currency of the host                                                                    | -11481 (-$114.81)                              |
| FromCollectiveAmount               | total amount that increases/decreases the balance of the `FromCollectiveId` in the currency of the FromCollectiveId                                             | -11481                                         |
| paymentProcessorFeesInHostCurrency | fees for the payment processor in cents                                                                                                                         |                                                |
| hostFeesInHostCurrency             | fees for the host in cents in the currency of the host (which might be different than the currency of the collective, e.g. WWCode (USD) and WWCode Berlin (EUR) | 574 (5% of €100 in USD)                        |
| platformFeesInHostCurrency         | fees for the platform (Open Collective)                                                                                                                         | 574 (5% of €100 in USD)                        |
| ToHostAmount                       | net amount in cents received by the host of the `ToCollectiveId` in the currency of the `ToHostId`                                                              | 9630 (€100 - (2.9% + $0.30) - €5 platform fee) |
| ToCollectiveAmount                 | total amount that increases/decreases the balance of the `ToCollectiveId` in the currency of the order                                                          | 9580 (€96.30 - €5 host fee)                    |
| FromHostCurrency                   | currency of the `FromHostId`                                                                                                                                    | USD                                            |
| FromCollectiveCurrency             | currency of the `FromCollectiveId`                                                                                                                              | USD                                            |
| ToCollectiveCurrency               | currency of the collective that receives the money                                                                                                              | EUR                                            |
| ToHostCurrency                     | currency of the order (currency of the `ToCollectiveId`)                                                                                                        | USD                                            |
| fxrate                             | Foreign eXchange Rate from the currency of the order (`ToCollectiveCurrency`) to the currency of the host of the `FromCollectiveId` (float)                     | 1.15                                           |

Note: The Collective currency might be different than the Host Currency (both for the source "From" and the recipient "To"). The fxrate only takes into account the conversion between `ToCollectiveCurrency` to `ToHostId`.
