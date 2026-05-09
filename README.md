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
│   │   ├── base/
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

Mirror clusters should share a common environment base and keep only cloud-specific differences in thin overlays.

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
- `environments/<env>/base` contains the common desired state for mirrored clusters in the same environment
- `base/` contains reusable manifests for a component
- `overlays/<env>/` contains environment-specific composition for a component

## Observability

The repository now includes a minimal observability base for `dev`:

- `kube-prometheus-stack` for Prometheus, Alertmanager, and Grafana
- `loki` in single-binary mode for centralized logs

The current setup is intentionally conservative:

- persistence enabled for dev
- no public ingress yet
- no SSO yet
- no log shipper yet

The next observability component to add is a collector such as Promtail or Alloy.
