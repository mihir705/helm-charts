# Charts

Reusable units (Terraform modules / Ansible roles / Chef cookbooks).

| Chart | Kubernetes objects | Maps from |
|-------|--------------------|-----------|
| `webapp` | Deploy, SVC, Ingress, HPA, PDB, CM, Secret, SA, helm test | ECS/Cloud Run/Container Apps service |
| `postgresql` | StatefulSet, PVC, Secret, SVC | RDS / Flexible Server / Cloud SQL (use those in prod) |
| `worker` | Deploy + HPA | SQS / Service Bus consumer |
| `cronjob` | CronJob | CodeBuild schedule / Cloud Scheduler |
| `migrate` | pre-install/upgrade hook Job | DB migration before rollout |
| `platform` | umbrella + conditions | `environments/prod/main.tf` |
