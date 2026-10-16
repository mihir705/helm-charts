# helm-charts

Job-ready Helm library: reusable charts, environment values, and labs. Terraform/OpenTofu create the cluster (EKS/AKS/GKE); Helm deploys workloads onto it.

## Structure

```
helm-charts/
├── charts/
│   ├── webapp/          # Deployment, Service, Ingress, HPA, PDB
│   ├── postgresql/      # StatefulSet + PVC
│   ├── worker/          # background consumer
│   ├── cronjob/
│   ├── migrate/         # Helm hooks
│   └── platform/        # umbrella (compose charts like a Terraform env)
├── environments/
│   ├── lab/values.yaml
│   └── prod/values.yaml
└── labs/00-setup … 12-gke-ci
```

## Curriculum

| Lab | Concepts |
|-----|----------|
| [00-setup](labs/00-setup/README.md) | helm, kubectl, kind/minikube |
| [01-chart-structure](labs/01-chart-structure/README.md) | Chart.yaml, templates |
| [02-values-and-overrides](labs/02-values-and-overrides/README.md) | `-f`, `--set`, env values |
| [03-templates-helpers-sprig](labs/03-templates-helpers-sprig/README.md) | `_helpers.tpl`, Sprig |
| [04-hooks-and-tests](labs/04-hooks-and-tests/README.md) | hooks, `helm test` |
| [05-dependencies-umbrella](labs/05-dependencies-umbrella/README.md) | Chart.yaml dependencies |
| [06-upgrades-rollbacks](labs/06-upgrades-rollbacks/README.md) | history, rollback, `--atomic` |
| [07-configmaps-secrets](labs/07-configmaps-secrets/README.md) | envFrom, existingSecret |
| [08-hpa-pdb-probes](labs/08-hpa-pdb-probes/README.md) | autoscaling, disruption, probes |
| [09-ingress-tls](labs/09-ingress-tls/README.md) | Ingress + TLS |
| [10-eks-hands-on](labs/10-eks-hands-on/README.md) | terraform-aws `eks_clusters` |
| [11-aks-hands-on](labs/11-aks-hands-on/README.md) | terraform-azure `aks_clusters` |
| [12-gke-ci](labs/12-gke-ci/README.md) | terraform-gcp `gke_clusters`, lint |

## How it maps

| Helm | Ansible | Chef | Terraform / OpenTofu |
|------|---------|------|----------------------|
| chart | role | cookbook | module |
| `values.yaml` | role defaults | attributes | variables defaults |
| `environments/*/values.yaml` | group_vars | environment | `terraform.tfvars` |
| `platform` umbrella | `site.yml` | Policyfile run_list | `environments/prod/main.tf` |
| `helm template` | `--check` | `--why-run` | `tofu plan` |
| `helm upgrade --install` | playbook apply | `chef-client` | `tofu apply` |
| `helm rollback` | (re-run old) | previous cookbook | state rollback (limited) |

Disable in-cluster PostgreSQL in prod and use RDS / Flexible Server / Cloud SQL from your IaC repos.

## Quick start (no cluster required)

```bash
cd /Users/mihir/code/helm-charts
helm lint charts/webapp
helm template lab charts/webapp --set replicaCount=2
helm dependency update charts/platform
helm template shop charts/platform -f environments/lab/values.yaml
```

On a cluster:

```bash
helm upgrade --install shop charts/platform -n app --create-namespace \
  -f environments/lab/values.yaml --wait
helm test shop -n app
```

Never commit `environments/prod/secrets.yaml`.
