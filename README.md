# CI/CD Pipeline Demo

This repo shows a basic install dependencies workflow as well as an update dependencies workflow.

## Install Dependencies Code

- Name: human readable
- on: signals what will trigger the action
- jobs: top level keyword, contains jobs that the workflow will perform.
  - options are: build, test, deploy
- runs-on: sets the os environment
- uses
  - action/checkout: performs a git checkout operation to clone your repo into the runner. @v4 is the version
  - actions/setup-node: github actions way to set up node in your environment
- build step: if there is a build command in the package.json, it'll run it
- cache: speeds up subsequent runs by caching downloaded npm packages
- npm ci: This runs a clean install and is meant for automated environments: [docs](https://docs.npmjs.com/cli/v10/commands/npm-ci?v=true)
- **note the indentation and - between `-name` and `uses` or `run`**

## Update Dependencies Workflow

- Set to run weekly at 2 am or when ran by command in the github actions gui
- update naming conventions
- did not need matrix as this will run the updates a bunch of times which probably isn't needed
- permissions: sets write perms with the temporary github token when update-deps is executed
  -with ref develop is used to create a development branch for security updates to be updated to (this isn't necessary. I've mostly done this to make it easier to compare code)
- Create pull request uses peter-evans
  - pr gets a token for temp access, creates a message and temp branch etc
  - peter-evans/create-pull-request is a popular action
- **Point of interest**: review the branch where this workflow was initially set up and then the changes in main. now if you look at the **run workflow** button in the actions tab, you can select with branch to run the workflow from
