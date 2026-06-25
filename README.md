# CI/CD Pipeline with Docker + Prometheus + Grafana

A complete DevOps project showcasing CI/CD, containerization, and infrastructure monitoring.

## 🛠 Tech Stack

| Tool | Purpose |
|------|---------|
| Node.js + Express | Web application |
| Docker | Containerization |
| GitHub Actions | CI/CD automation |
| Docker Hub | Image registry |
| Prometheus | Metrics collection |
| Grafana | Monitoring dashboards |

## 🚀 How it works

1. Push code to GitHub
2. GitHub Actions automatically builds a Docker image
3. Image is pushed to Docker Hub
4. Prometheus collects server metrics every 15 seconds
5. Grafana displays live dashboards

## 📦 Run locally

```bash
# Start the app
docker run -p 3001:3000 mahtabvariyani/ci-cd-pipeline

# Start monitoring
cd monitoring
docker compose -f docker-compose.monitoring.yml up -d
```

## 📊 Dashboards

- Prometheus: http://localhost:9090
- Grafana: http://localhost:3002 (admin / admin123)
  - Import dashboard ID **1860** for server metrics

## 📁 Project Structure

```
ci-cd-pipeline/
├── .github/workflows/deploy.yml   # CI/CD pipeline
├── monitoring/
│   ├── prometheus.yml             # Prometheus config
│   └── docker-compose.monitoring.yml
├── Dockerfile                     # Container recipe
├── server.js                      # Web app
├── package.json                   # Dependencies
└── .gitignore
```
