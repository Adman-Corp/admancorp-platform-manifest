# Onboarding A Cluster

This repository uses Helm charts to deploy platform components. The umbrella chart `charts/admancorp-platform` composes all
components with environment and cloud-specific values files.

## Cluster entrypoints

Deploy the umbrella chart with the matching values file:

```text
charts/admancorp-platform/
  values-dev-azure.yaml
  values-dev-gcp.yaml
  values-uat-azure.yaml
  values-uat-gcp.yaml
  values-prod-azure.yaml
  values-prod-gcp.yaml
```

## Adding a new cluster

1. Add a new values file to `charts/admancorp-platform/`
2. Wire it into Argo CD as a new Application targeting the umbrella chart with the new values file
