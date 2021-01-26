# Dokku GitHub Action Example

An example repo showing how to use the official [dokku GitHub action](https://github.com/dokku/github-action) to deploy your app with continuous delivery.

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

Each time a pull request is opened a new review app is deployed.

The [example workflow](./.github/workflows/review-app.yml) uses [GitHub Deploys](https://docs.github.com/en/rest/reference/repos#deployments) and requires the following [environments](https://docs.github.com/en/actions/reference/environments) to be created:

- production
- review

You can add new environments in your repo settings. You can also take advantage of [environment protection rules](https://docs.github.com/en/actions/reference/environments#environment-protection-rules) to request reviews before deployments can take place.
