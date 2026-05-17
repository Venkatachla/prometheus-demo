# Prometheus Monitoring with GitHub Actions CI/CD

## Project Overview
This project demonstrates a complete, beginner-friendly DevOps CI/CD pipeline using **GitHub Actions** to automatically build and monitor a **Node.js** application using **Prometheus**. It showcases the fundamentals of monitoring automation, metrics scraping, and automated pipeline verification. 

## Features
- **Automated CI/CD Pipeline:** Fully automated workflow using GitHub Actions.
- **Node.js Application:** A lightweight Express.js app exposing metrics.
- **Prometheus Integration:** Automated setup and metrics scraping.
- **Metrics Endpoint:** Real-time application metrics exposed at `/metrics`.
- **Target Validation:** Automated checks to ensure Prometheus targets are healthy.

## Technologies Used
- **Node.js & Express.js:** Application backend.
- **prom-client:** Library to generate Prometheus metrics for Node.js.
- **Prometheus:** Time-series database and monitoring system.
- **Docker:** Containerization (Dockerfile included for deployment).
- **GitHub Actions:** CI/CD pipeline and automation.
- **YAML:** Configuration for both GitHub Actions and Prometheus.

## Pipeline Explanation
The CI/CD pipeline automates the entire monitoring lifecycle:
1. **Trigger:** The pipeline starts automatically when code is pushed to the `main` branch.
2. **Setup:** It checks out the repository and configures the Node.js environment.
3. **App Startup:** The Node.js application is started in the background.
4. **Prometheus Setup:** Prometheus is dynamically downloaded, configured with `prometheus.yml`, and started.
5. **Scraping:** Prometheus begins scraping the application's `/metrics` endpoint.
6. **Verification:** `curl` commands verify the application metrics, the Prometheus UI, and the target health.

## Monitoring Explanation
Prometheus operates on a **Pull Model**. Instead of the application pushing data to a server, Prometheus actively "pulls" or "scrapes" metrics from the application's `/metrics` endpoint every 5 seconds (defined by `scrape_interval`). These metrics are stored in a time-series database and can be used for alerting or visualization (e.g., with Grafana).

## Setup & Running Instructions

### Local Execution
1. Install dependencies:
   ```bash
   npm install
   ```
2. Start the application:
   ```bash
   npm start
   ```
3. Run Prometheus locally using Docker:
   ```bash
   docker run -p 9090:9090 -v ${PWD}/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus
   ```

### Pushing to GitHub
```bash
git init
git add .
git commit -m "Initial commit - Prometheus monitoring project"
git branch -M main
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main
```

## Important URLs
- **`http://localhost:3000`** - The Node.js application home page.
- **`http://localhost:3000/metrics`** - The metrics endpoint scraped by Prometheus.
- **`http://localhost:9090`** - The Prometheus Web UI.
- **`http://localhost:9090/api/v1/targets`** - API endpoint to check the status of monitored targets.

## Screenshots
*(Add screenshots of the GitHub Actions success workflow, Prometheus UI, and Metrics endpoint here)*
