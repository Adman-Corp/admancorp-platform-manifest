# admancorp-platform-manifest

Platform manifest repository for AdmanCorp's Kubernetes platform.

This repository contains deployable Kubernetes manifests only.

It does not contain Argo CD `Application` or `ApplicationSet` objects.

## Structure

```text
.
├── docs/
├── environments/
│   ├── dev/
│   │   ├── azure/
│   │   └── gcp/
│   ├── uat/
│   │   ├── azure/
│   │   └── gcp/
│   └── prod/
│       ├── azure/
│       └── gcp/
├── platform/
│   ├── networking/
│   ├── observability/
│   ├── operators/
│   └── security/
└── shared/
```

## Usage

Each cluster-specific folder in `environments/` is a deployment entrypoint.

Your external Argo CD repository can target:

- `environments/dev/azure`
- `environments/dev/gcp`
- `environments/uat/azure`
- `environments/uat/gcp`
- `environments/prod/azure`
- `environments/prod/gcp`

## Conventions

- `platform/` contains reusable platform components
- `shared/` contains manifests reused across environments
- `base/` contains reusable manifests for a component
- `overlays/<env>/` contains environment-specific composition for a component

## Next Components To Add

- operator installation manifests
- Envoy Gateway manifests
- observability stack manifests
- policy and security manifests
