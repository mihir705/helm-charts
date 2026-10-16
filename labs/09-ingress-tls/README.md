# Lab 09 — Ingress and TLS

**Concepts:** Ingress, ingressClassName, TLS secret, pathType.

Prod values set `webapp.ingress.enabled: true` for `app.example.com`. Pair with ALB/NGINX Ingress on EKS/AKS/GKE from Terraform, not with a LoadBalancer Service per app unless you have to.
