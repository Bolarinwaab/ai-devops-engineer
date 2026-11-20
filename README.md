# AI DevOps Engineer

A starter portfolio project demonstrating an AI-assisted DevOps workflow with a small Python API, automated tests, containerisation, and Kubernetes deployment manifests.

## Project structure

- `app/` — minimal Flask health API
- `tests/` — automated API tests
- `Dockerfile` — container build
- `docker-compose.yml` — local run
- `.github/workflows/ci.yml` — GitHub Actions test and build pipeline
- `k8s/` — Kubernetes Deployment and Service
- `docs/` — architecture and operational notes

## Run locally

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
python -m app.main
```

Open `http://localhost:5000/health`.

## Run tests

```bash
pip install -r requirements-dev.txt
pytest
```

## Build and run with Docker

```bash
docker build -t ai-devops-engineer:local .
docker run --rm -p 5000:5000 ai-devops-engineer:local
```

Or use `docker compose up --build`.

## Kubernetes

```bash
kubectl apply -f k8s/
kubectl get deployments,services
```

The service is a ClusterIP. Use port-forwarding for local access:

```bash
kubectl port-forward service/ai-devops-engineer 8080:80
```

Then open `http://localhost:8080/health`.

## GitHub

Create a repository named `ai-devops-engineer`, upload the extracted project contents, and commit with:

`Initial release: AI DevOps Engineer`

The workflow runs tests and builds the container image on pushes and pull requests. It does not publish the image or deploy to a cloud account; configure those steps only after adding repository secrets and reviewing the target environment.

## Security notes

- Do not commit credentials, API keys, `.env` files, cloud service-account keys, or production secrets.
- Pin and regularly review dependencies before production use.
- This is a portfolio starter, not a production-hardened service.
