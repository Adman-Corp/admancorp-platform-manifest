# Onboarding A Cluster

This repository is organized by environment entrypoint with a cluster layer for mirrored Azure and GCP clusters.

Each environment should expose one entrypoint per target cluster:

```text
environments/
  dev/
    azure/
    gcp/
  uat/
    azure/
    gcp/
  prod/
    azure/
    gcp/
```
