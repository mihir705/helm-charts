# Lab 04 — Hooks and tests

**Concepts:** `helm.sh/hook` (pre-install, pre-upgrade, test), hook-weight, hook-delete-policy, `helm test`.

```bash
helm template mig charts/migrate
# look for helm.sh/hook: pre-install,pre-upgrade

helm install lab-web charts/webapp --dry-run --debug
# after a real install:
# helm test lab-web
```

Migrations run as a Job **before** the webapp rolls out — same idea as a Terraform `null_resource` that must finish first, but native to Helm.
