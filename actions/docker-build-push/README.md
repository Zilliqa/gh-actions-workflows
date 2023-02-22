# Docker build and push GitHub Action

## About

GitHub Action to build and push Docker images with [Buildx](https://github.com/docker/buildx)
with full support of the features provided by [Moby BuildKit](https://github.com/moby/buildkit)
builder toolkit. This includes multi-platform build, secrets, remote cache, etc.
and different builder deployment/namespacing options.
___

* [Usage](#usage)
  * [Git context](#git-context)
  * [Path context](#path-context)
* [Inputs](#inputs)
* [Outputs](#outputs)

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
        uses: Zilliqa/gh-actions-workflows/actions/docker-build-push@v1
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
        uses: Zilliqa/gh-actions-workflows/actions/docker-build-push@v1
        with:
          context: "{{defaultContext}}:mysubdir"
          push: true
          tags: user/app:latest
```

Building from the current repository automatically uses the [GitHub Token](https://docs.github.com/en/actions/security-guides/automatic-token-authentication),
so it does not need to be passed. If you want to authenticate against another
private repository, you have to use a [secret](https://docs.docker.com/build/ci/github-actions/examples/#secrets)
named `GIT_AUTH_TOKEN` to be able to authenticate against it with Buildx:

```yaml
      -
        name: Build and push
        uses: Zilliqa/gh-actions-workflows/actions/docker-build-push@v1
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
      - name: Checkout
        uses: actions/checkout@v3
      - name: Login to Docker Hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      - name: Build and push
        uses: Zilliqa/gh-actions-workflows/actions/docker-build-push@v1
        with:
          context: .
          push: true
          tags: user/app:latest
```

## Inputs

<!-- AUTO-DOC-INPUT:START - Do not remove or modify this section -->

|   INPUT    |  TYPE  | REQUIRED | DEFAULT  |             DESCRIPTION             |
|------------|--------|----------|----------|-------------------------------------|
| build-args | string |  false   |          |    Arguments to build the image     |
| cache-from | string |  false   |          |           Docker registry           |
|  cache-to  | string |  false   |          | The username to access the registry |
|  context   | string |  false   |          | The context to build the Dockerfile |
|    file    | string |   true   |          |     The path to the Dockerfile      |
|    pull    | string |  false   | `"true"` |      Enable/disable image pull      |
|    push    | string |  false   | `"true"` |      Enable/disable image push      |
|    tags    | string |   true   |          |        The tags of the image        |
|   target   | string |  false   |          | The target to build in the<br>image |

<!-- AUTO-DOC-INPUT:END -->

## Outputs

<!-- AUTO-DOC-OUTPUT:START - Do not remove or modify this section -->

|  OUTPUT  |  TYPE  |      DESCRIPTION      |
|----------|--------|-----------------------|
|  digest  | string |     Image digest      |
| imageid  | string |       Image ID        |
| metadata | string | Build result metadata |

<!-- AUTO-DOC-OUTPUT:END -->
