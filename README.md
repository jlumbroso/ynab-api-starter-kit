# YNAB API Starter Kit

Do you want to build a web app with the [YNAB API](https://api.youneedabudget.com/), but are not sure how to get started?

Try this YNAB API Starter Kit!

Without **any** prior knowledge, it allows you to build:

- a web app that uses JavaScript and the [Vue.js](https://vuejs.org/) framework for its frontend,
- makes requests to the YNAB API through OAuth,
- and is entirely compiled on GitHub, and hosted on GitHub Pages!

[![Works with YNAB](./public/works_with_ynab.svg)](https://api.youneedabudget.com/)

## Live Demo

The starter project invites a user to authorize YNAB to share information with the project, provides a choice of budget, then displays all the transactions. It's probably not very useful, but it demonstrates several key features involved in building a YNAB web app.

View a [live demo](https://ynab.github.io/ynab-api-starter-kit/) of what this project will start off looking like or take a look below.

![Screen recording on 2018-03-28 at 12:37:23](https://user-images.githubusercontent.com/759811/38046244-c9806f0a-3284-11e8-8788-509912ec79c2.gif)

## Getting Started—Entirely Without Leaving Your Browser!

This method does not require installing anything on your computer, and does not require any prior knowledge. It will allow you to launch a copy of this project in less than 5 minutes, that you can start modifying and learning from. (_Later, you can also edit and work on this project on your computer, of course._)

### Step 1: Create your own copy of the project

1. [Sign-up for a GitHub account](https://github.com/signup), if you don't already have one.

2. Click [here](https://github.com/jlumbroso/ynab-api-starter-kit/generate) to generate a repository from this template (you can read GitHub's documentation on what it means to [create a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template#creating-a-repository-from-a-template)).

**NOTE:** In the following steps, we will assume the GitHub account you created has username `your-github-username` and that you have called your project `your-new-ynab-project`, but change these accordingly when following instructions.

### Step 2: Obtain an OAuth Client ID so the app can access the YNAB API

OAuth is the framework through which YNAB can share access to a user's data safely, without requiring that user share their credentials.

Every YNAB app requires their own OAuth Application credentials.

1. You will need a YNAB account, and [to be logged in](https://app.youneedabudget.com/users/authentication).

2. Go to the [YNAB Developer Settings](https://app.youneedabudget.com/settings/developer)
   and click [New Application](https://app.youneedabudget.com/oauth/applications/new).

3. The name, description, website URL and privacy policy URL are all information that will be provided to users for them to determine whether to trust your app (or not!); but these will not affect the operation of your app.

   The _Redirect URI(s)_ parameter is important, as it controls where the user data can be sent. It is important to add a URL to the app, in this case:

   ```
   https://<your-github-username>.github.io/<your-new-ynab-project>/
   ```

4. Check that you acknowledge the terms of service (after reading them!), and click "Save Application."

   You'll see your Client ID, Client Secret and Redirect URI(s) (you can [read more about these concepts in YNAB's documentation](https://api.youneedabudget.com/#outh-applications)). For this project, we will be using the _Implicit Grant Flow_ and will only need the Client ID.

5. Copy and paste the Client ID and URL to your app into the `src/config.json` file of the repository (you can edit them on GitHub directly):

   ```json
   {
     "clientId": "<your client ID>",
     "redirectUri": "https://<your-github-username>.github.io/<your-new-ynab-project>/"
   }
   ```

**NOTE:** At this point, your app will only be able to access the YNAB API in [Restricted Mode](https://api.youneedabudget.com/#oauth-restricted-mode): This means you can access it an unlimited number of times, but other users will only be able to authenticate a combined total of 25 times, before you will need to write api@youneedabudget.com to reset your quota or get your app officially approved.

### Step 3: Wait for GitHub Actions to deploy app to GitHub Pages

## Code Architecture of the App

Check out the [YNAB API Documentation](https://api.youneedabudget.com/) for more information on how to use the YNAB API.

This example uses [Vue.js](https://vuejs.org/) but it is not required. Feel free
to use whatever framework or libraries you prefer.

### [`src/App.vue`](https://github.com/ynab/ynab-api-starter-kit/blob/gh-pages/src/App.vue)

In the script portion of this page, you can see how to build an OAuth URI to
obtain an access token for the API.

It also has some examples on retrieving budgets and transactions.

### [`src/Transactions.vue`](https://github.com/ynab/ynab-api-starter-kit/blob/gh-pages/src/components/Transactions.vue)

This displays all the transactions when you've got them. It also has an example
of using `utils.convertMilliUnitsToCurrencyAmount` to convert the milliunits that
YNAB uses into the currency format of the budget.

## Local Development

### `npm start`

Runs the development server (defaults to `localhost:8080`) and watches for changes.

### `npm run build`

Builds the production assets for deployment. This will build to `dist/build.js`
which the `index.html` will load.

## Alternative Methods

### Cloning/forking the repository

If you're looking for a little less magic:

- Use git to clone it: `git clone https://github.com/ynab/ynab-api-starter-kit`
- From within the folder, run `npm install`
- Then run `npm start`

### Using the create-app

- Install [Node.js](https://nodejs.org/).
- In your terminal, run `npx ynab-api-starter-kit my-ynab-app`

This will:

- Create a copy of this project on your computer.
- Install all the dependencies.
- Start up the server ready for development.

## License

Copyright (c) 2019 You Need A Budget, LLC

Copyright (c) 2022 Jérémie Lumbroso

Licensed under the Apache-2.0 license
