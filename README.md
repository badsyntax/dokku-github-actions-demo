# Dokku GitHub Action Example

How to use the official [dokku GitHub action](https://github.com/dokku/github-action) to deploy your app using continuous delivery with GitHub Actions and GitHub Deploys.

GitHub Deploys is still in public beta but it's stablish and is a useful mechanism to manage your deployment workflows. You can use [environment protection rules](https://docs.github.com/en/actions/reference/environments#environment-protection-rules) to give you granular control over [who can deploy](https://docs.github.com/en/actions/managing-workflow-runs/reviewing-deployments) and to where.

## Workflows

This repository demonstrates how to:

- Deploy `review` apps to a `review` environment where a pull request is created or updated. Assigned reviewers will need to approve the deployment.
- Deploy a `production` app to a `production` environment on changes to the main/master branch. No deployment review is required.

### Review Apps

Each time a pull request is opened or updated a new review app is deployed. The review app will be deployed to url `http://github-actions-demo-app-${{ github.event.pull_request.number }}.dokku.proxima-web.com`.

You'll need to create the following following environments in the repository settings:

- production
- review

Take advantage of the [environment protection rules](https://docs.github.com/en/actions/reference/environments#environment-protection-rules) to enable deploy restrictions.

#### Screenshots

Pull request created, but deploy is awaiting approval:

GitHub Actions deploy workflow awaiting approval:

Approving the deploy workflow:

Deployment in progress:

Deployment


## GitHub Secrets

The following secrets must be set:

- `SSH_PRIVATE_KEY`

You'll see reference to a secret called `GITHUB_TOKEN` in the workflow files, but there's no need to manually set this yourself as this is set by GitHub Actions.

If you want to see debug information, you can create a secret called `ACTIONS_STEP_DEBUG` with a value of `true`.

## dokku Setup

```bash
# on server
dokku apps:create github-actions-demo-app
```

```bash
# on local
git remote add dokku dokku@dokku.proxima-web.com:github-actions-demo-app
git push dokku
```

Visit http://github-actions-demo-app.dokku.proxima-web.com/ to confirm the deployment was successful.

## Review Apps



