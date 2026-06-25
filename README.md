# 🚀 CI/CD Pipeline — Live on the Internet

> A complete DevOps project: containerized Node.js app with automated CI/CD, deployed to a real server, with live monitoring.

🌍 **Live at:** [http://servercicdpoplines.duckdns.org:8000](http://servercicdpoplines.duckdns.org:8000)

---

## 🛠 Tech Stack

| Tool | Purpose |
|------|---------|
| Node.js + Express | Web application |
| Docker | Containerization |
| GitHub Actions | CI/CD automation — auto deploys on every push |
| Docker Hub | Docker image registry |
| Hetzner CX23 | Real Ubuntu server (2 vCPU, 4GB RAM) |
| DuckDNS | Free domain pointing to server |
| Prometheus | Metrics collection every 15s |
| Grafana | Live monitoring dashboards |

---

## ⚙️ How the CI/CD Pipeline Works

Every time you push code to the `main` branch, this happens **automatically**:

```
git push
    │
    ▼
GitHub detects push
    │
    ▼
GitHub Actions spins up a Linux runner
    │
    ├─ Job 1: build-and-push
    │     • Checks out code
    │     • Logs into Docker Hub
    │     • Builds Docker image
    │     • Pushes image to Docker Hub
    │
    └─ Job 2: deploy
          • SSHs into Hetzner server
          • Pulls latest Docker image
          • Stops old container
          • Starts new container
          • App is live ✅
```

Zero manual work. One push = live update.

---

## 📦 Run Locally

```bash
# Clone the repo
git clone https://github.com/mah404/ci-cd-pipeline.git
cd ci-cd-pipeline

# Build and run with Docker
docker build -t my-app .
docker run -p 3001:3000 my-app

# Visit: http://localhost:3001
```

---

## 📊 Monitoring Stack

```bash
cd monitoring
docker compose -f docker-compose.monitoring.yml up -d
```

| Dashboard | URL |
|-----------|-----|
| Prometheus | http://localhost:9090 |
| Grafana | http://localhost:3002 |

Import Grafana dashboard ID **1860** for live CPU, RAM, disk metrics.

---

## 📁 Project Structure

```
ci-cd-pipeline/
├── .github/
│   └── workflows/
│       └── deploy.yml          # CI/CD pipeline config
├── monitoring/
│   ├── prometheus.yml          # Prometheus scrape config
│   └── docker-compose.monitoring.yml
├── Dockerfile                  # Container build recipe
├── server.js                   # Node.js web app
├── package.json                # Dependencies
└── .gitignore
```

---

## 🔐 GitHub Secrets Required

| Secret | Purpose |
|--------|---------|
| `DOCKERHUB_USERNAME` | Docker Hub login |
| `DOCKERHUB_TOKEN` | Docker Hub access token |
| `SERVER_HOST` | Server IP address |
| `SERVER_USER` | SSH username (root) |
| `SERVER_SSH_KEY` | Private SSH key for deployment |

---

## 📈 

- Containerizing applications with Docker
- Writing CI/CD pipelines with GitHub Actions
- Deploying to a real Linux server via SSH automation
- Setting up infrastructure monitoring with Prometheus & Grafana
- Managing secrets securely in GitHub
- Using DuckDNS for free domain mapping

---

*Built a DevOps project — from zero to a live, auto-deploying, monitored application.*
