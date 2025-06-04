# architecture-menifests
A centralized repository of declarative Kubernetes manifests that define the architectural layout and deployment structure for GitOps workflows managed by Argo CD.

# GitOps Architecture Repository Template

This repository serves as a template for managing Kubernetes clusters using a GitOps approach with Argo CD. It is designed to support declarative application deployments and centralized management of Helm charts and values.

## Usage

- **Fork this repository** to manage each cluster or organization separately.
- All Kubernetes resources are managed declaratively via Git. Argo CD continuously syncs these resources into the cluster.

## Directory Structure

```plaintext
./
├── applications/                    # Argo CD Application definitions
│   └── Applications.yaml            # Lists all Argo CD Applications to be managed
├── charts/                          # In-house versioned Helm charts
│   ├── argocd/                      # Example: Argo CD chart
│   │   ├── 1.0.0/                   # Version 1.0.0
│   │   └── 1.0.2/                   # Version 1.0.2
│   └── nginx/                       # Example: nginx chart
│       ├── 1.0.0/                   # Version 1.0.0
│       └── 1.0.2/                   # Version 1.0.2
├── Projects/                        # Project or domain-level resources
│   ├── istio/                       # Istio VirtualServices, Gateways, etc.
│   ├── menifests/                   # Custom Kubernetes resources (e.g., Deployments)
│   └── values/                      # Chart-specific values.yaml files
│       ├── argocd/
│       └── nginx/
└── README.md
```

## Operational Guidelines

### 1. Repository per Cluster

- Each cluster should maintain its own Git repository by forking this template.
- `applications/Applications.yaml` should declare all Argo CD Applications for that cluster.
- Customize `Projects/values` and `Projects/menifests` per project or environment.

### 2. Helm Chart Versioning

- The `charts/` directory stores versioned Helm charts locally.
- Multiple versions can coexist to support different environments or rollback needs.
- Customize behavior via separate values files under `Projects/values/`.

### 3. Istio Resource Management

- `Projects/istio/` contains Istio-specific configurations such as `VirtualService`, `Gateway`, and `DestinationRule`.
- These are treated as first-class GitOps-managed Kubernetes resources.

---

## Notes

- This structure is a best-practice GitOps layout using Argo CD and Helm.
- You are free to rename or restructure directories as needed for your organization.
- For automation, consider adding pre-merge validation and `argocd app diff` in CI/CD pipelines.
