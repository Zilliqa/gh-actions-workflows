# GitHub Actions and Workflow

General purpose reusable Github Action workflows

## Introduction

Use provided [GitHub Actions reusable custom actions](https://docs.github.com/en/actions/creating-actions/about-custom-actions) 
to implement individual tasks that can combined to create jobs and customize workflows. It is possible to create own actions, or use and customize actions shared by the GitHub community.

## Actions

| Name | Description |
|------|-------------|
| [CI dockerized app build and push](./actions/ci-dockerized-app-build-push/README.md) | Bake and deploy Docker image to ECR or DockerHub |
| [Configure AWS credentials](./actions/configure-aws-credentials/README.md) | Configure AWS credential and region environment variables |
| [Configure AWS profile](./actions/configure-aws-profile/README.md) | Configure AWS profile in the config file |
| [Docker build and push](./actions/docker-build-push/README.md) | Build and push Docker images with Buildx |
| [Docker cache](./actions/docker-cache/README.md) | Generate docker cache configuration |
| [Generate tag](./actions/generate-tag/README.md) | Generate a tag to be consumed for a Docker image |
