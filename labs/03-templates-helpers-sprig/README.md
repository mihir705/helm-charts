# Lab 03 — Templates, helpers, Sprig

**Concepts:** Go templates, `include`, `define`, `nindent`, `toYaml`, `required`, Sprig (`trunc`, `quote`).

See `charts/webapp/templates/_helpers.tpl` — `fullname` must be DNS-safe (63 chars). That is why Terraform-style names get truncated in Kubernetes.
