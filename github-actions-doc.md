# GitHub Actions Basic Concepts Explained

## Event
An **event** is an activity in a GitHub repository that triggers a workflow to run. Examples include a pull request being opened, edited, or synchronized.

```yaml

on:
pull_request:
types:  [opened,  edited,  synchronize] # Trigger workflow on pull request events'
```

## Workflows

A workflow is a configurable automated process that will run one or more **jobs**
`validate-pr.yml`


## Jobs
A job is a set of steps in a workflow that is executed on the same runner.
```
jobs:
  validate-checklist:
    runs-on: ubuntu-latest # Use Ubuntu virtual machine

    steps:
    - name: Check PR Description
      id: check-description
      uses: actions/github-script@v6 # Run custom JavaScript code
      with:
        script: |
          const checklist = [
            "- [x] Answer 1:", // First checklist item
            "- [x] Answer 2:", // Second checklist item
            "- [x] Answer 3:", // Third checklist item          
            ];

          const prBody = context.payload.pull_request.body || ""; // Get PR description
          const missingItems = checklist.filter(item => !prBody.includes(item)); // Check for missing items

          if (missingItems.length > 0) {
            core.setFailed(`Checklist incomplete. Missing items: ${missingItems.join(", ")}`); // Fail if incomplete
          } else {
            core.info("Checklist is complete."); // Log success if complete
          }
```

## Actions: 
An action is a custom application for the GitHub Actions platform that performs a complex but frequently repeated task
`uses: actions/github-script@v6 # Run custom JavaScript code`

## Runners:  
A runner is a server that runs your workflows when they're triggered.
`runs-on: ubuntu-latest # Use Ubuntu virtual machine`

