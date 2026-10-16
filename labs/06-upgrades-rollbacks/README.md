# Lab 06 — Install, upgrade, history, rollback

**Concepts:** release, revision, `--wait`, `--atomic`, `helm history`, `helm rollback`.

```bash
helm install shop charts/platform -n app --create-namespace \
  -f environments/lab/values.yaml --dry-run

# real cluster:
helm upgrade --install shop charts/platform -n app -f environments/lab/values.yaml --wait
helm history shop -n app
helm rollback shop 1 -n app
helm uninstall shop -n app
```

`--atomic` rolls back automatically if the release fails (safer prod).
