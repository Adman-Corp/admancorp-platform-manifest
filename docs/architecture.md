# Architecture

This repository contains deployable Kubernetes platform manifests only.

It does not contain Argo CD `Application`, `ApplicationSet`, or bootstrap objects.

## Layout

- `platform/`: reusable platform components grouped by domain
- `shared/`: manifests reused by multiple components or environments
- `environments/`: environment entrypoints consumed by GitOps tooling

## Deployment Model

Each environment folder under `environments/` is a composition root.

The external Argo CD repository should target one of these paths:

- `environments/dev`
- `environments/uat`
- `environments/prod`

Environment folders reference reusable components from `platform/` and `shared/`.
