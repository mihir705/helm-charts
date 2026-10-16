# Lab 05 — Dependencies and umbrella charts

**Concepts:** `Chart.yaml` `dependencies`, `condition:`, `helm dependency update`, umbrella `platform`.

```bash
helm dependency update charts/platform
ls charts/platform/charts/
helm lint charts/platform -f environments/lab/values.yaml
helm template shop charts/platform -f environments/lab/values.yaml
```

Turn off PostgreSQL in prod and use RDS from terraform-aws:

```yaml
postgresql:
  enabled: false
```
