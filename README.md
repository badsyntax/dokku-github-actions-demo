# Dokku GitHub Action Example

An example repo showing how to use the official [dokku GitHub action](https://github.com/dokku/github-action) to deploy your app with continuous delivery.

## GitHub Secrets

The following secrets must be set:

- `GIT_REMOTE_URL` (eg `'ssh://dokku@dokku.me:22/appname'`)
- `SSH_PRIVATE_KEY`

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

The [example workflow](./.github/workflows/review-app.yml) uses GitHub Deploys and requires the following environments to be created:

- production
- review

Access the environment settings in your repo settings.
