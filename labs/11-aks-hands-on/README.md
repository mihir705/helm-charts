# Lab 11 — AKS (terraform-azure / opentofu-azure)

1. Apply `aks_clusters`.
2. `az aks get-credentials -g <rg> -n <cluster>`
3. `helm upgrade --install shop charts/platform -n app --create-namespace -f environments/prod/values.yaml`

| Terraform | Helm |
|-----------|------|
| `aks_clusters` | target cluster |
| `container_registry` | image repository |
| `postgresql_flexible` | disable chart postgresql |
| `application_gateway` / ingress | `webapp.ingress.className` |
