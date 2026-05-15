# Conventions

## General

- Use Helm charts as the composition and deployment mechanism
- Keep one platform component per chart in `charts/`
- The umbrella chart `charts/admancorp-platform` composes all components together
- Environment and cloud-specific variations are expressed via values files
- Per-component values defaults live in each chart's `values.yaml`; overrides flow through the umbrella chart's values files

## Secrets

Do not commit raw secrets to this repository.

Store only:

- `ExternalSecret`
- secret references
- certificate requests

## GitOps Entry Points

Argo CD should point to the umbrella chart directory with the appropriate values file for each cluster.

## Mirror Clusters

- When Azure and GCP clusters mirror the same environment, they share the same values for domain, component enablement, etc.
- Only the `envoyServiceHostname` (external-dns annotation) differs per cloud
- Keep cloud-specific differences in the values file, not in separate overlay trees
