# Lab 01 — Chart structure

**Concepts:** Chart.yaml, values.yaml, templates/, `_helpers.tpl`, NOTES.txt.

```
charts/webapp/
├── Chart.yaml
├── values.yaml
├── values.schema.json
└── templates/
    ├── _helpers.tpl
    ├── deployment.yaml
    ├── service.yaml
    └── tests/test-connection.yaml
```

```bash
helm show chart charts/webapp
helm show values charts/webapp
```

A chart is the Kubernetes analogue of a Terraform module / Ansible role / Chef cookbook.
