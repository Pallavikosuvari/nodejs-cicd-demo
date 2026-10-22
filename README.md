# nodejs-demo-app – CI/CD with GitHub Actions

A sample Node.js (Express) app with an automated pipeline that **tests → builds a Docker image → pushes it to Docker Hub** on every push to `main`.
Docker Hub image: https://hub.docker.com/r/kosuvaripallipallavi/nodejs-demo-app
## Pipeline (`.github/workflows/main.yml`)
1. **test job** – checkout, set up Node 20, `npm ci`, `npm test` (Jest + Supertest).
2. **build-and-push job** – runs only if tests pass; logs in to Docker Hub, builds the image, pushes `latest` and the commit-SHA tag.

## Setup
Add these in *Repo → Settings → Secrets and variables → Actions*:
| Secret | Value |
|---|---|
| `DOCKERHUB_USERNAME` | your Docker Hub username |
| `DOCKERHUB_TOKEN` | Docker Hub access token (Read & Write) |

## Run locally
```bash
npm install && npm test && npm start        # http://localhost:3000
docker build -t nodejs-demo-app . && docker run -p 3000:3000 nodejs-demo-app
```
### GitHub Actions pipeline
<img width="1915" height="890" alt="Task1 pipeline success" src="https://github.com/user-attachments/assets/bc93ee92-8345-4490-999c-2bf2080bdaa7" />
### Docker Hub image
<img width="1902" height="930" alt="Dockerhub Success" src="https://github.com/user-attachments/assets/38cce863-f67b-47bf-b695-6bdbd885e751" />




