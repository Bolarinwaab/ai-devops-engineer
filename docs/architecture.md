# Architecture overview

```text
Developer
   |
   v
GitHub repository
   |
   v
GitHub Actions CI
   |-- install dependencies
   |-- run pytest
   |-- build container image
   |
   v
Container image
   |
   v
Kubernetes Deployment (2 replicas)
   |
   v
Kubernetes Service
```

The included pipeline validates code and builds an image. It deliberately stops before registry publishing or deployment so that credentials, cloud target, and release approvals can be configured safely.
