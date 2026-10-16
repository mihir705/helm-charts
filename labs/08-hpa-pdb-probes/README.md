# Lab 08 — HPA, PDB, probes

**Concepts:** liveness vs readiness, HorizontalPodAutoscaler, PodDisruptionBudget.

Enabled in `environments/prod/values.yaml`. Lab keeps replicaCount=1 and autoscaling off.

Interview: readiness gates traffic; liveness restarts the container; PDB keeps minAvailable during node drains.
