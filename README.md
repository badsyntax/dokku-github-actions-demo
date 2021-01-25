# Dokku GitHub Action Example

An example repo showing how to use all the features of the official [dokku GitHub action](https://github.com/dokku/github-action).

## GitHub Secrets

The following secrets must be set:

- `GIT_REMOTE_URL` (eg `'ssh://dokku@dokku.me:22/appname'`)

## dokku Setup

The examples relies on an example app existing on the dokku server:

```bash
# on server
dokku apps:create github-actions-demo-app
```

Add the remote and deploy the app:

```bash
## on local
git remote add dokku dokku@dokku.proxima-web.com:github-actions-demo-app
git push dokku
```

Once deployed we can add TLS:

```bash
# on server
dokku letsencrypt github-actions-demo-ap
```

Visit https://github-actions-demo-app.dokku.proxima-web.com/ to confirm the deployment was successful.

## Build and Deploy Docker Image

The following demonstrates how to build the docker image and deploy to GitHub Container Registry:

```bash
docker build -t ghcr.io/badsyntax/github-actions-demo-app:latest .
echo $CR_PAT | docker login ghcr.io -u badsyntax --password-stdin
docker push ghcr.io/badsyntax/github-actions-demo-app:latest
```

To automate this

## Review Apps


