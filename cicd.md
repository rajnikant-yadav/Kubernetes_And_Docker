# GitHub Actions Overview

GitHub Actions is a powerful automation tool that allows you to automate tasks in your GitHub repository. Here's an overview of the main components:

## Workflow

A workflow is a series of tasks you want to automate. For example, you can create a workflow that builds and tests your code whenever someone pushes changes to your GitHub repository.

```yaml
name: Build and Test
on:
  push:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      # Add more steps for building and testing
```
## Job
Each task within your workflow is a job. Jobs can run one after the other or at the same time. For instance, building your code and running tests can be separate jobs in your workflow.
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      # Add more steps for building
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      # Add more steps for testing
```

## Step
Every action you take within a job is a step. Steps are the small actions that make up each job. For example, running a command or executing a script are steps.

```yaml

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Build project
        run: |
          npm install
          npm run build
```

## Action
Actions are pre-made tasks you can plug into your workflow. For instance, sending a notification or deploying your code can be done using actions.

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Deploy to production
        uses: JamesIves/github-pages-deploy-action@4.1.4
        with:
          ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
```
- name: Checkout code: This line specifies the first step in the job and gives it a name, "Checkout code". This step is responsible for checking out (or fetching) the repository's code into the runner environment where the workflow will run.
uses: actions/checkout@v2: This line defines the action to be executed in the "Checkout code" step. It specifies an action called "checkout" provided by GitHub. The @v2 indicates that it's using version 2 of this action.
- name: Build project: This line specifies the second step in the job and names it "Build project". This step will be responsible for building the project's code.
run: | npm install npm run build: This line defines what the "Build project" step should do. The run keyword indicates that the following lines are commands to be executed. The | symbol indicates that multiple commands will be run as part of this step. Here, it first runs npm install, which installs project dependencies, and then it runs npm run build, which typically builds the project's code. This assumes the project is using npm (Node Package Manager) and follows the convention of running npm run build to build the project.


## Runner
The runner is the environment where your workflow tasks and actions run. GitHub provides these runners, but you can also use your own.

## Event
Events trigger your workflow to start running. For example, someone pushing code changes or commenting on an issue can trigger your workflow.

```yaml
on:
  push:
    branches:
      - main
  issue_comment:
    types: [created, edited]
```