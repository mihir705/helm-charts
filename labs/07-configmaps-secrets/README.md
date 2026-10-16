# Lab 07 — ConfigMaps and Secrets

**Concepts:** `envFrom` ConfigMap vs Secret, `existingSecret`, never commit prod secrets.

```bash
helm template lab charts/webapp --set envFromSecret=true \
  --set secrets.DATABASE_URL=postgres://x
```

Prod: External Secrets Operator / Sealed Secrets / CSI, not plaintext in git. See `environments/prod/secrets.yaml.example`.
