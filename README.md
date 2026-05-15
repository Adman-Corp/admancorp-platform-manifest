# admancorp-platform-manifest

Platform manifest repository for AdmanCorp's Kubernetes platform, managed as Helm charts.

## Structure

```
.
├── charts/
│   ├── admancorp-platform/   # Umbrella chart composing all components
│   ├── namespaces/           # Shared Kubernetes namespaces
│   ├── cert-manager/         # cert-manager operator
│   ├── external-secrets/     # External Secrets operator
│   ├── envoy-gateway/        # Envoy Gateway + Gateway API configuration
│   ├── kyverno/              # Kyverno policy engine
│   ├── kube-prometheus-stack/ # Prometheus + Grafana + Alertmanager
│   ├── loki/                 # Loki log aggregation
│   └── alloy/                # Grafana Alloy log collector
└── docs/
```

## Usage

The umbrella chart `charts/admancorp-platform` composes all components. Deploy with environment-specific values:

```bash
helm dependency update charts/admancorp-platform

# Dev
helm install platform charts/admancorp-platform -f charts/admancorp-platform/values-dev-azure.yaml
helm install platform charts/admancorp-platform -f charts/admancorp-platform/values-dev-gcp.yaml

# UAT
helm install platform charts/admancorp-platform -f charts/admancorp-platform/values-uat-azure.yaml
helm install platform charts/admancorp-platform -f charts/admancorp-platform/values-uat-gcp.yaml

# Prod
helm install platform charts/admancorp-platform -f charts/admancorp-platform/values-prod-azure.yaml
helm install platform charts/admancorp-platform -f charts/admancorp-platform/values-prod-gcp.yaml
```

## Observability

Observability components (kube-prometheus-stack, loki, alloy) are included in the umbrella chart with conditions that default to disabled. Enable them per environment via values:

- **dev**: all observability disabled
- **uat/prod**: all observability enabled
