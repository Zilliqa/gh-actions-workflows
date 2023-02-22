# Configure AWS credentials GitHub Action

## About

GitHub Action to build and push Docker images with [Buildx](https://github.com/docker/buildx)
with full support of the features provided by [Moby BuildKit](https://github.com/moby/buildkit)
builder toolkit. This includes multi-platform build, secrets, remote cache, etc.
and different builder deployment/namespacing options.
___

* [Usage](#usage)
  * [Git context](#git-context)
  * [Path context](#path-context)
* [Examples](#examples)
* [Customizing](#customizing)
  * [inputs](#inputs)
  * [outputs](#outputs)
* [Troubleshooting](#troubleshooting)
* [Contributing](#contributing)

## Usage

In the examples below we are also using one other actions:

* [`login`](https://github.com/docker/login-action) action will take care to
  log in against a Docker registry.

### Git context

By default, this action uses the [Git context](https://docs.docker.com/engine/reference/commandline/build/#git-repositories),
so you don't need to use the [`actions/checkout`](https://github.com/actions/checkout/)
action to check out the repository as this will be done directly by [BuildKit](https://github.com/moby/buildkit).

The git reference will be based on the [event that triggered your workflow](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows)
and will result in the following context: `https://github.com/<owner>/<repo>.git#<ref>`.

```yaml
name: ci

on:
  push:
    branches:
      - 'main'

jobs:
  docker:
    runs-on: ubuntu-latest
    steps:
      - name: Login to Docker Hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      - name: Build and push
        uses: Zilliqa/gh-actions-workflows/actions@v1
        with:
          push: true
          tags: user/app:latest
```

Be careful because **any file mutation in the steps that precede the build step
will be ignored, including processing of the `.dockerignore` file** since
the context is based on the Git reference. However, you can use the
[Path context](#path-context) using the [`context` input](#inputs) alongside
the [`actions/checkout`](https://github.com/actions/checkout/) action to remove
this restriction.

Default Git context can also be provided using the [Handlebars template](https://handlebarsjs.com/guide/)
expression `{{defaultContext}}`. Here we can use it to provide a subdirectory
to the default Git context:

```yaml
      - name: Build and push
        uses: Zilliqa/gh-actions-workflows/actions@v1
        with:
          context: "{{defaultContext}}:mysubdir"
          push: true
          tags: user/app:latest
```

> **Warning**
>
> Subdirectory for Git context is available from [BuildKit v0.9.0](https://github.com/moby/buildkit/releases/tag/v0.9.0).
> If you're using the `docker` builder (default if `setup-buildx-action` not used),
> then BuildKit in Docker Engine will be used. As Docker Engine < v22.x.x embeds
> Buildkit 0.8.2 at the moment, it does not support this feature. It's therefore
> required to use the `setup-buildx-action` at the moment.

Building from the current repository automatically uses the [GitHub Token](https://docs.github.com/en/actions/security-guides/automatic-token-authentication),
so it does not need to be passed. If you want to authenticate against another
private repository, you have to use a [secret](https://docs.docker.com/build/ci/github-actions/examples/#secrets)
named `GIT_AUTH_TOKEN` to be able to authenticate against it with Buildx:

```yaml
      -
        name: Build and push
        uses: Zilliqa/gh-actions-workflows/actions@v1
        with:
          push: true
          tags: user/app:latest
          secrets: |
            GIT_AUTH_TOKEN=${{ secrets.MYTOKEN }}
```

### Path context

```yaml
name: ci

on:
  push:
    branches:
      - 'main'

jobs:
  docker:
    runs-on: ubuntu-latest
    steps:
      -
        name: Checkout
        uses: actions/checkout@v3
      -
        name: Set up QEMU
        uses: docker/setup-qemu-action@v2
      -
        name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v2
      -
        name: Login to Docker Hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      -
        name: Build and push
        uses: Zilliqa/gh-actions-workflows/actions@v1
        with:
          context: .
          push: true
          tags: user/app:latest
```


## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|         INPUT         |  TYPE  | REQUIRED | DEFAULT  |          DESCRIPTION          |
|-----------------------|--------|----------|----------|-------------------------------|
|      aws-region       | string |   true   |          |        The AWS region         |
|       oidc-role       | string |   true   |          |   The identity provide role   |
|     profile-name      | string |  false   |          | The AWS configuration profile |
| role-duration-seconds | string |  false   | `"1200"` | Assume role session duration  |
|    role-to-assume     | string |   true   |          |      The role to assume       |

<!-- AUTO-DOC-INPUT:END -->

## Outputs
