# Dokku GitHub Action Example

An example repo showing how to use all the features of the official [dokku GitHub action](https://github.com/dokku/github-action).

## dokku Setup

The examples relies on an example app existing on the dokku server:

```bash
dokku apps:create github-actions-demo-app
```

We'll be using the [`Dockerfile`](./Dockerfile) to package our app.

## Build and Deploy Docker Image

The following demonstrates how to build the docker image and deploy to GitHub Container Registry:

```bash
docker build -t ghcr.io/badsyntax/github-actions-demo-app:latest .
echo $CR_PAT | docker login ghcr.io -u badsyntax --password-stdin
docker push ghcr.io/badsyntax/github-actions-demo-app:latest
```

To automate this

## Review Apps


