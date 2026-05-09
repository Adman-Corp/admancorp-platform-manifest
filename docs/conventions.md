# Conventions

## General

- Use `kustomize` as the default composition mechanism
- Keep one platform capability per folder
- Keep reusable manifests in `base/`
- Put environment-specific adjustments in `overlays/dev`, `overlays/uat`, and `overlays/prod`

## Secrets

Do not commit raw secrets to this repository.

Store only:

- `ExternalSecret`
- secret references
- certificate requests

## GitOps Entry Points

Argo CD should point to the environment directories, not directly to individual components, unless you intentionally want smaller applications.

## Mirror Clusters

- When Azure and GCP clusters are meant to mirror the same environment, compose the shared desired state in `environments/<env>/base`
- Keep `environments/<env>/azure` and `environments/<env>/gcp` as thin overlays with only provider-specific changes
- Prefer a single shared base over copying full environment compositions between clouds
