# Testing

Tests are intended to be run either on development machines \(`NODE_ENV=development`\) or on a test server such as circleci \(`NODE_ENV=circleci`\). This documentation concentrates on the development testing experience.

## Setup and Running Tests

We use [Mocha](https://mochajs.org/) for unit-testing and [Cypress](https://www.cypress.io/) for end-to-end \(e2e\) testing. More details on setting up your local machine for tests can be found at, [https://github.com/opencollective/opencollective-frontend/blob/main/docs/e2e.md](https://github.com/opencollective/opencollective-frontend/blob/main/docs/e2e.md).

## How to debug when GitHub is challenging the oAuth process?

* Run the api with the `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET` env variables \(you can find them [here](https://github.com/organizations/OpenCollective/settings/applications/346712)\).
* Run the website, go to [http://localhost:3000/opensource/apply](http://localhost:3000/opensource/apply) and go through the flow. Use the login `opencollectivetest` and the password that is stored in 1Password.

