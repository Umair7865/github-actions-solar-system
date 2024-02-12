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
