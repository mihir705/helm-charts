# Lab 02 — Values and overrides

**Concepts:** default values, `-f` files, `--set`, precedence (rightmost wins).

```bash
helm template lab charts/webapp
helm template lab charts/webapp --set replicaCount=3
helm template prod charts/platform -f environments/lab/values.yaml
helm template prod charts/platform -f environments/prod/values.yaml
```

`environments/*/values.yaml` is the same idea as `terraform.tfvars`. Disable unused subcharts instead of empty `{}`.
