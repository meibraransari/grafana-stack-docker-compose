# 📊 Grafana Client Monitoring Stack

Welcome to the **Grafana Client** monitoring stack! This Docker Compose configuration sets up the necessary agents (`Node Exporter` and `cAdvisor`) to collect system and container metrics. These metrics can then be scraped by a Prometheus server and visualized in Grafana.

## 🚀 Features

- **Node Exporter**: Collects hardware and OS-level metrics from the host machine.
- **cAdvisor**: Analyzes resource usage and performance characteristics of running containers.
- **Resource Constraints**: Configured with reasonable CPU and memory limits to ensure the monitoring agents don't consume excessive host resources.
- **Log Management**: Built-in JSON file logging with size and file rotation limits to prevent disk space issues.

## 🛠️ Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed on the host.
- [Docker Compose](https://docs.docker.com/compose/install/) installed.
- A Prometheus server configured to scrape metrics from this client.

## 📦 Services Overview

### 1. Node Exporter (`nodeexporter`)
- **Image**: `prom/node-exporter:latest`
- **Port**: `9100`
- **Purpose**: Exposes system metrics (CPU, memory, disk I/O, etc.) for Prometheus to scrape.

### 2. cAdvisor (`cadvisor`)
- **Image**: `gcr.io/cadvisor/cadvisor:latest`
- **Port**: `8080`
- **Purpose**: Exposes container metrics (resource usage and performance) for Prometheus to scrape.

## 🚦 Getting Started

1. **Clone Repository & Navigate to the directory**:
   ```bash
   git clone https://github.com/meibraransari/grafana-stack-docker-compose.git
   cd grafana-stack-docker-compose/
   rm -rf grafana_server # This is not needed if you are only deploying the client
   cd grafana_client
   ```

2. **Start the services** in detached mode:
   ```bash
   docker compose up -d
   ```

3. **Verify the services are running**:
   ```bash
   docker compose ps
   ```

4. **Test the metric endpoints** in your browser or using `curl`:
   - Node Exporter metrics: `http://<your-host-ip>:9100/metrics`
   - cAdvisor metrics: `http://<your-host-ip>:8080/metrics`

## ⚙️ Configuration Details

- **Environment Variables**: The project name is set to `gs` via the `.env` file (`COMPOSE_PROJECT_NAME=gs`).
- **Resource Limits**: Both containers are constrained to maximum limits (e.g., `0.5` CPU, `256M`/`512M` RAM) and reserved resources to guarantee stability.
- **Volumes**: Read-only mounts to host directories (`/proc`, `/sys`, `/`, `/var/lib/docker`) are required for the agents to gather metrics accurately. Note that the `/cgroup` mount for cAdvisor is specific to Linux and may not work on macOS.

## Configure promethius server to add below targets to scrape 
```bash
  - job_name: 'Docker_Node'
    scrape_interval: 30s
    scrape_timeout: 30s
    metrics_path: /metrics
    static_configs:
      - targets: ['<your-host-ip>:9100','<your-host-ip>:8080']
        labels:
          instance: Docker_Node
```

### Reload the Prometheus config
```bash
curl -X POST http://localhost:9090/-/reload
```
### Check prometheus targets
```bash
http://<Prometheus-server-ip>:9090/api/v1/targets
```

### Check in Grafana dashboard
```bash
http://<Grafana-server-ip>:3000/
```

## 🛑 Stopping the Services

To stop and remove the containers, run:
```bash
docker compose down
```

## 📝 Notes
- Ensure your host firewalls allow traffic on ports `9100` and `8080` from your Prometheus server.
- The configuration uses `restart: unless-stopped` to ensure the agents automatically start on system boot or Docker daemon restart.
