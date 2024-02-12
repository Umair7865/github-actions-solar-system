# Solar System NodeJS Application

A simple HTML+MongoDB+NodeJS project to display Solar System and it's planets.

---
## Requirements

For development, you will only need Node.js and NPM installed in your environement.

### Node
- #### Node installation on Windows

  Just go on [official Node.js website](https://nodejs.org/) and download the installer.
Also, be sure to have `git` available in your PATH, `npm` might need it (You can find git [here](https://git-scm.com/)).

- #### Node installation on Ubuntu

  You can install nodejs and npm easily with apt install, just run the following commands.

      $ sudo apt install nodejs
      $ sudo apt install npm

- #### Other Operating Systems
  You can find more information about the installation on the [official Node.js website](https://nodejs.org/) and the [official NPM website](https://npmjs.org/).

If the installation was successful, you should be able to run the following command.

    $ node --version
    v8.11.3

    $ npm --version
    6.1.0

---
## Install Dependencies from `package.json`
    $ npm install

## Run Unit Testing
    $ npm test

## Run Code Coverage
    $ npm run coverage

## Run Application
    $ npm start

## Access Application on Browser
    http://localhost:3000/

------------------------------------------------------------

Navigate to your GitHub account and explore github-actions-solar-system repository
Go to the Actions Tab and click on I understand my workflows, go ahead and enable them
There is a workflow file named solar-system.yml
There is one job named - unit-testing
The Job includes multiple steps to:

Checkout repository
Setup Node.js
Install dependencies
Run unit tests
Archive test reports
Do the following
1) Create a new branch from the main and name it feature/workflow and switch to it

A workflow should be triggered. Check that it fails in the unit testing step.
2) Work on the feature/workflow branch, add the following environment variables at the workflow level:
MONGO_URI: ‘mongodb+srv://supercluster.d83jj.mongodb.net/superData'
MONGO_USERNAME: superuser
MONGO_PASSWORD: SuperPassword
For MONGO_PASSWORD, add it as a Repository Secret and refer it in the workflow environment variables
3) Trigger the workflow and check that it runs successfully




Was the feature/workflow branch created successfully?

Is the MONGO_URI variable configured correctly?

Is the MONGO_USERNAME variable configured correctly?

Is the MONGO_PASSWORD secret being created?

Does the MONGO_PASSWORD environment variable in the workflow reference a value in secrets?




====================== S O L U T I O N ==========================

Exploring the Repository on GitHub:

Log into your GitHub account.
Navigate to the github-actions-solar-system repository within your account.
Enabling GitHub Actions:

Go to the "Actions" tab in the repository.
If you see a prompt like "I understand my workflows, go ahead and enable them", click on it. This will enable GitHub Actions for your repository.
Understanding the Workflow File:

Locate the solar-system.yml file in the repository. It should be under .github/workflows.
Understand the structure of the workflow, especially the unit-testing job. Notice the steps it includes, such as checking out the repository, setting up Node.js, installing dependencies, running unit tests, and archiving test reports.
Creating and Switching to a New Branch:

Open your command line or use the GitHub UI to create a new branch from main called feature/workflow.
Switch to this new branch either by using the command line (git checkout feature/workflow) or by using the GitHub UI.
Monitoring the Workflow Trigger:

After switching to the feature/workflow branch, a workflow might automatically be triggered.
Check the Actions tab to see if the workflow runs and fails at the unit testing step, as expected.
Adding Environment Variables to the Workflow:

On the feature/workflow branch, edit the solar-system.yml workflow file.
Add the required environment variables at the workflow level:
MONGO_URI: ‘mongodb+srv://supercluster.d83jj.mongodb.net/superData'
MONGO_USERNAME: superuser
For MONGO_PASSWORD, you'll need to add it as a secret.
Adding a Repository Secret:

Go to the repository settings on GitHub.
Navigate to "Secrets" and choose "New repository secret".
Name the secret (e.g., MONGO_PASSWORD) and set its value to SuperPassword.
Save the secret.
Referencing the Repository Secret in the Workflow:

In the solar-system.yml file, reference the secret in the environment variables section like this:
MONGO_PASSWORD: ${{ secrets.MONGO_PASSWORD }}
Commit and push the changes to the feature/workflow branch.
Triggering the Workflow:

Make a new commit to the feature/workflow branch or use the GitHub UI to manually trigger the workflow.
This action will trigger the workflow.
Verifying the Workflow Execution:

Once the workflow is triggered, monitor its execution in the Actions tab.
Ensure that the workflow completes successfully, particularly the unit testing step.
Refer to the YAML file below to configure your Solar System Workflow, notice the MONGO_PASSWORD env value is reference from secrets.

Open in editor mode for better view
---
name: Solar System Workflow
on:
  workflow_dispatch: null
  push:
    branches:
      - main
      - feature/*
env:
  MONGO_URI: mongodb+srv://supercluster.d83jj.mongodb.net/superData
  MONGO_USERNAME: superuser
  MONGO_PASSWORD: ${{ secrets.MONGO_PASSWORD }}
jobs:
  unit-testing:
    name: Unit Testing
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4
      - name: Setup NodeJS Version
        uses: actions/setup-node@v3
        with:
          node-version: 20
      - name: Install Dependencies
        run: npm install
      - name: Unit Testing
        run: npm test
      - name: Archive Test Result
        uses: actions/upload-artifact@v3
        with:
          name: Mocha-Test-Result
          path: test-results.xml


=========================================================================


