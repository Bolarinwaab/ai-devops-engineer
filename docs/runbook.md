# Basic operations runbook

## Check service health

```bash
curl http://localhost:5000/health
```

Expected response: `{"status":"healthy"}`.

## Troubleshooting

- **Container exits:** inspect `docker logs <container-id>`.
- **Tests fail:** install development requirements and run `pytest -q`.
- **Kubernetes pods not ready:** run `kubectl describe pod <pod-name>` and `kubectl logs <pod-name>`.
- **Image cannot be pulled:** ensure the image exists in the cluster's image environment or publish it to a registry and update the manifest.

## Recovery

For Kubernetes, inspect rollout status with `kubectl rollout status deployment/ai-devops-engineer`. Roll back a previous rollout with `kubectl rollout undo deployment/ai-devops-engineer` when an earlier healthy revision exists.
