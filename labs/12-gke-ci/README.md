# Lab 12 — GKE + CI lint

terraform-gcp / opentofu-gcp: apply `gke_clusters`, then:

```bash
gcloud container clusters get-credentials <name> --region <region>
helm upgrade --install shop charts/platform -n app --create-namespace \
  -f environments/prod/values.yaml
```

CI (this repo): `helm lint` + `helm template` on every chart, plus umbrella with lab values.

```bash
helm lint charts/webapp
helm template ci charts/webapp >/dev/null
```

`helm template` is the Helm equivalent of `tofu plan` for YAML (no cluster required).
