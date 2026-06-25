# 🚀 CI/CD Pipeline — Live on the Internet with HTTPS

> A complete production-grade DevOps project: containerized Node.js app with automated CI/CD, deployed to a real server, secured with SSL, and monitored with Prometheus + Grafana.

🌍 **Live at:** [https://servercicdpoplines.duckdns.org](https://servercicdpoplines.duckdns.org)
🔒 **Fully secured with SSL certificate from Let's Encrypt**

---

## ✅ What Makes This Production-Grade

| Feature | Status |
|---------|--------|
| Containerized with Docker | ✅ |
| Automated CI/CD on every push | ✅ |
| Deployed to real server (Hetzner VPS) | ✅ |
| Custom domain (DuckDNS) | ✅ |
| HTTPS with SSL certificate | ✅ 🔒 |
| Nginx reverse proxy | ✅ |
| Auto HTTP → HTTPS redirect | ✅ |
| Auto SSL renewal (Let's Encrypt) | ✅ |
| Live monitoring (Prometheus + Grafana) | ✅ |

---

## 🛠 Tech Stack

| Tool | Purpose |
|------|---------|
| Node.js + Express | Web application |
| Docker | Containerization |
| GitHub Actions | CI/CD — auto deploys on every git push |
| Docker Hub | Docker image registry |
| Hetzner CX23 | Real Ubuntu VPS (2 vCPU, 4GB RAM) |
| DuckDNS | Free domain pointing to server |
| Nginx | Reverse proxy + SSL termination |
| Let's Encrypt + Certbot | Free SSL certificate with auto-renewal |
| Prometheus | Metrics collection every 15 seconds |
| Grafana | Live monitoring dashboards |

---

## ⚙️ How the CI/CD Pipeline Works

Every time you push code to `main`, this happens **automatically**:

```
git push
    │
    ▼
GitHub detects the push
    │
    ▼
GitHub Actions runs automatically:
    │
    ├─ Job 1: build-and-push
    │     ✔ Checkout code
    │     ✔ Login to Docker Hub
    │     ✔ Build Docker image
    │     ✔ Push image to Docker Hub
    │
    └─ Job 2: deploy
          ✔ SSH into Hetzner server
          ✔ Pull latest Docker image
          ✔ Stop old container
          ✔ Start new container
          ✔ App live at https://servercicdpoplines.duckdns.org
```

Zero manual work. One push = live update in under 2 minutes.

---

## 🔒 HTTPS Architecture

```
Browser (HTTPS request)
        │
        ▼
Nginx (port 443) — handles SSL encryption
        │
        │ forwards internally
        ▼
Docker container (port 8000) — your app
        │
        ▼
Response encrypted and sent back to browser
```

- All traffic is encrypted end-to-end
- HTTP requests automatically redirect to HTTPS
- SSL certificate auto-renews every 90 days via Certbot

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

| Dashboard | URL | Login |
|-----------|-----|-------|
| Prometheus | http://localhost:9090 | — |
| Grafana | http://localhost:3002 | admin / admin123 |

Import Grafana dashboard ID **1860** for live CPU, RAM, disk metrics.

---

## 📁 Project Structure

```
ci-cd-pipeline/
├── .github/
│   └── workflows/
│       └── deploy.yml              # CI/CD pipeline — auto build & deploy
├── monitoring/
│   ├── prometheus.yml              # Prometheus scrape config
│   └── docker-compose.monitoring.yml
├── Dockerfile                      # Container build recipe
├── server.js                       # Node.js web app
├── package.json                    # Dependencies
└── .gitignore
```

---

## 🔐 GitHub Secrets Required

| Secret | Purpose |
|--------|---------|
| `DOCKERHUB_USERNAME` | Docker Hub login |
| `DOCKERHUB_TOKEN` | Docker Hub access token |
| `SERVER_HOST` | Server IP address |
| `SERVER_USER` | SSH username |
| `SERVER_SSH_KEY` | Private SSH key for automated deployment |

---

## 🌍 Server Setup

| Spec | Value |
|------|-------|
| Provider | Hetzner Cloud |
| Type | CX23 |
| OS | Ubuntu 24 LTS |
| CPU | 2 vCPU |
| RAM | 4 GB |
| Domain | servercicdpoplines.duckdns.org |
| SSL | Let's Encrypt (auto-renewing) |
| Reverse Proxy | Nginx |

---

## 📈 

- Containerizing applications with Docker
- Writing multi-job CI/CD pipelines with GitHub Actions
- Deploying to a real Linux server via automated SSH
- Setting up Nginx as a reverse proxy
- Securing a server with free SSL (Let's Encrypt + Certbot)
- Configuring automatic HTTP → HTTPS redirects
- Setting up infrastructure monitoring with Prometheus & Grafana
- Managing secrets securely in GitHub Actions

---

*DevOps project — from zero to a live, auto-deploying, SSL-secured, monitored application.*
