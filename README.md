# gh-actions-workflows

Zilliqa's internal library of reusable GitHub composite actions.

## Available actions

| Action | Description |
|--------|-------------|
| [`actions/ci-dockerized-app-build-push`](./actions/ci-dockerized-app-build-push) | Build a Docker image and push it to a GCP Artifact Registry, GCR, or Docker Hub. Includes registry/GHA layer caching, optional Trivy scanning, and SARIF upload. |
| [`actions/generate-tag`](./actions/generate-tag) | Generate an image tag from the short Git commit SHA. |

Each action's full input/output reference is in its own `README.md`, auto-generated from `action.yml`.

## Usage

Reference an action with the standard `uses:` syntax. Pin to a major-version tag (`@v3`, `@v4`, …) — never `@main` from a consumer.

```yaml
jobs:
  build:
    runs-on: ubuntu-22.04
    permissions:
      id-token: write
      contents: read
    steps:
      - uses: actions/checkout@v6

      - name: Build & push image to GCP Artifact Registry
        uses: Zilliqa/gh-actions-workflows/actions/ci-dockerized-app-build-push@v3
        with:
          file: ./Dockerfile
          tag: europe-west1-docker.pkg.dev/zilliqa-prj/repo/app
          tag-length: 7
          tag-latest: ${{ github.ref == 'refs/heads/main' }}
          registry: europe-west1-docker.pkg.dev
          workload-identity-provider: ${{ secrets.GCP_WORKLOAD_IDENTITY_PROVIDER }}
          service-account: ${{ secrets.GCP_SERVICE_ACCOUNT }}
          cache-key: ${{ github.event.repository.name }}
          trivy-scan: true
```

## Versioning

Major version tags (`@v1`, `@v2`, …) are mutable — they always point at the latest release of that major. Minor/patch tags (`@v3.0.0`) are immutable.

| Tag | Status |
|-----|--------|
| `@v3` | Current stable. |
| `@v2` | Frozen — most existing consumers pin here. |
| `@v1` | Frozen — Node 12 / Node 16 era; migrate off when convenient. |

Each major release may include breaking changes; check the release notes before bumping. Cross-major migration guidance lives in the corresponding GitHub release.

## Compatibility notes

- Composite actions in this repo target **Node 24** runtime where the underlying third-party action requires it (e.g., `actions/checkout@v6`, the Docker stack `@v4/@v7`). Self-hosted runners must be on Actions Runner ≥ `2.327.1` and a glibc ≥ 2.31 base image (Ubuntu 22.04+, Debian 12+).
- AWS support has been removed; Zilliqa workloads run on GCP. Consumers needing AWS authentication should not move to a future `@v4`.

## Contributing

- One change per PR; keep the scope small.
- The `update-readme.yaml` workflow regenerates per-action `README.md` files automatically when `action.yml` changes — no manual edits to the auto-doc tables.
- Pre-existing tests live in `.github/workflows/test-*.yml` and run on every push; add coverage for new behavior there.

## License

See [LICENSE](./LICENSE).
