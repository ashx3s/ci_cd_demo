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
