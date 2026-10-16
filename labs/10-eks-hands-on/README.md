# Lab 10 — EKS (terraform-aws / opentofu-aws)

1. Apply `eks_clusters` in terraform-aws / opentofu-aws.
2. `aws eks update-kubeconfig --name <cluster> --region <region>`
3. Deploy charts:

```bash
helm upgrade --install shop charts/platform -n app --create-namespace \
  -f environments/prod/values.yaml
```

| Terraform | Helm |
|-----------|------|
| `eks_clusters` | cluster to install into |
| `ecr_repositories` | `webapp.image.repository` |
| `rds_instances` | disable in-cluster postgresql; set DATABASE_URL |
| `alb` / ingress controller | `webapp.ingress` |
| `acm_certificate` | Ingress TLS annotation or cert-manager |
