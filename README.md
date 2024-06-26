# Google Apps Script - aside template

This is a template for Google Apps Script projects
It includes a basic setup for a project with a `src` directory for the source code and a `test` directory for the tests.

## Environment

- Node.js
  - v20.12.1
- npm
  - v10.5.1
- aside
  - v1.3.4

## Login to Google

1. Install clasp

```sh
$ npm install -g @google/clasp
```

2. Login to Google

```sh
$ clasp login
```

3. Activate GoogleAppsScriptAPI

Access to [Google Apps Script API](https://script.google.com/home/usersettings) and activate it.

4. Create dev and prod Apps Script projects

Create scripts and copy the script ID of the dev and prod project.

*※ This script ID is used in the `clasp.json` file.*

## Setup

1. Clone this repository

```sh
$ git clone git@github.com:nago3/apps-script-template.git
```

2. Create a new project with [aside](https://github.com/google/aside) which is a package for building a GAS environment.

```sh
$ npx @google/aside init

? Project Title: › apps-script-template
? Generate package.json? … No / Yes<
? Script ID (optional): <Enter the script ID of the dev environment>
? Script ID for production environment (optional): <Enter the script ID of the prod environment>
```

## Run

Deploy development code to Google Apps Script.

```sh
$ npm run deploy
```

Deploy production code to Google Apps Script.

```sh
$ npm run deploy:prod
```

## After deployment

After deployment code, you got the script `version` ID of the project.
You can check the version ID and add the ID with `-i` to the .env file.

e.g.) return value of `npm run deploy`

```text
src/index.ts → dist...
created dist in 551ms
└─ dist/appsscript.json
└─ dist/index.js
Pushed 2 files.
Created version 1.
- AKfycbxYUxT1r4nviwCwzL8DuQ3JloDp_HgVQmK7nxxxxxxxxXXXXXXXXXXXxxxxxxxxXXXXXX @1.  ← This is the version ID
```

and so on, add the version ID to the `.env` file.

```env
PROD_DEPLOYMENT_ID="-i AKfycbxYUxT1r4nviwCwzL8DuQ3JloDp_HgVQmK7nxxxxxxxxXXXXXXXXXXXxxxxxxxxXXXXXX"
DEV_DEPLOYMENT_ID=""
```
