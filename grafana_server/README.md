# 📊 Grafana + Prometheus Monitoring Stack 🚀

## 🌐 Introduction

Welcome to the ultimate monitoring and observability stack!
This setup combines the power of **Grafana**, **Prometheus**, and **Alertmanager** to deliver real-time infrastructure monitoring, performance analytics, and intelligent alerting for your services and applications.

Whether you're running a homelab 🏠, cloud environment ☁️, or production infrastructure 🏢, this stack provides everything needed to monitor system health efficiently.

---

# 🏗️ Stack Architecture

The entire monitoring solution is containerized using Docker for easy deployment, scalability, and maintenance.

## 🔹 Core Components

### 📈 Grafana

The visualization platform for metrics and analytics.

#### Features:

* Interactive dashboards 📊
* Real-time monitoring ⚡
* Alert visualization 🚨
* Community dashboard imports 🌍

#### Access:

* Port: `3000`

---

### 📦 Prometheus

The metrics collection and storage engine.

#### Responsibilities:

* Scrapes metrics from targets
* Stores time-series data
* Executes PromQL queries
* Sends alerts to Alertmanager

#### Access:

* Port: `9090`

---

### 🚨 Alertmanager

Handles alert processing and notification routing.

#### Features:

* Alert grouping & deduplication
* Silence management 🔕
* Notification routing 📬
* Multi-channel integrations:

  * Email ✉️
  * Slack 💬
  * Discord 🎮
  * Webhooks 🌐

#### Access:

* Port: `9093`

---

# 🔐 Internal Networking

All containers communicate securely using an isolated Docker bridge network.

### Benefits:

* Secure inter-service communication 🔒
* Reduced attack surface 🛡️
* Easy container discovery 🔍

---

# 💾 Persistent Storage

Persistent volumes are configured to retain important data even after restarts or upgrades.

### Stored Data Includes:

* Grafana dashboards & settings
* Prometheus metrics database
* Alertmanager configurations
* Alert rules & notification settings

---

# 📦 Included Services

| Service         | Purpose                    | Default Port |
| --------------- | -------------------------- | ------------ |
| 📈 Grafana      | Visualization & Dashboards | `3000`       |
| 📦 Prometheus   | Metrics Collection         | `9090`       |
| 🚨 Alertmanager | Alert Routing              | `9093`       |

---

# 🚀 Deployment Guide

## ✅ Prerequisites

Before starting, ensure the following are installed:

* Docker 🐳
* Docker Compose ⚙️
* Internet access for image pulling 🌐

Verify installation:

```bash
docker --version
docker compose version
```

---

# ⚙️ Configuration Setup

## 1️⃣ Review Environment Variables

Configure:

* Grafana admin username/password
* Storage locations
* Network settings
* Alert notification settings

Example:

```env
GF_SECURITY_ADMIN_USER=admin
GF_SECURITY_ADMIN_PASSWORD=strongpassword
```

---

## 2️⃣ Prepare Persistent Volumes

Create required directories:

```bash
mkdir -p ./data/{grafana,prometheus} && chmod -R 777 ./data
```

---

## 3️⃣ Start the Stack

Launch all services in detached mode:

```bash
docker compose up -d
```

Docker will automatically:

* Pull required images 📥
* Create networks 🌐
* Start containers 🚀

---

# 🔍 Post-Deployment Verification

## 🌐 Access Services

| Service      | URL                     |
| ------------ | ----------------------- |
| Grafana      | `http://SERVER-IP:3000` |
| Prometheus   | `http://SERVER-IP:9090` |
| Alertmanager | `http://SERVER-IP:9093` |

---

## 🔑 Login to Grafana

Use the credentials configured in your environment variables.

Default login page:

* Username: `admin`
* Password: `your-password`

⚠️ Change default passwords immediately in production.

---

## 🔗 Verify Prometheus Data Source

Inside Grafana:

```text
Connections → Data Sources → Prometheus
```

Ensure:

* Status is healthy ✅
* Metrics are visible 📊

---

## 📊 Import Dashboards

You can:

* Create custom dashboards ✨
* Import community dashboards 🌍
* Use dashboard IDs from Grafana Labs

Popular dashboard examples:

* Node Exporter
* Docker Monitoring
* Kubernetes Cluster Metrics
* System Resource Usage

---

## 🚨 Configure Alert Notifications

Open Alertmanager and configure:

* SMTP email alerts ✉️
* Slack notifications 💬
* Discord webhooks 🎮
* Teams integrations 🏢

---

# 🔒 Security Best Practices

## 🛡️ Use Strong Credentials

Never use default admin passwords in production environments.

---

## 🌐 Restrict External Access

Recommended exposure:

| Service      | Public Access   |
| ------------ | --------------- |
| Grafana      | ✅ Optional      |
| Prometheus   | ❌ Internal Only |
| Alertmanager | ❌ Internal Only |

Use:

* VPN access 🔐
* Firewall rules 🔥
* Reverse proxy restrictions 🚧

---

## 🔐 Enable HTTPS

Deploy behind a reverse proxy such as:

* Nginx
* Traefik
* Caddy

Benefits:

* SSL/TLS encryption 🔒
* Secure authentication
* Better routing & security

## Nginx Proxy Manager Guide
[Nginx Proxy Manager Guide](https://www.youtube.com/playlist?list=PL5Afhqcc17s2UCcuEyFnTMHbVkxl8EG_7)
---

## 👥 Manage Users Carefully

Recommended practices:

* Disable public sign-ups ❌
* Use role-based access 👤
* Apply least privilege principle 🛡️

---

# 📚 Recommended Enhancements

## 🔌 Exporters

Add exporters for advanced monitoring:

| Exporter          | Purpose              |
| ----------------- | -------------------- |
| Node Exporter     | Linux system metrics |
| cAdvisor          | Container metrics    |
| Blackbox Exporter | Endpoint monitoring  |
| MySQL Exporter    | Database monitoring  |
| Redis Exporter    | Redis metrics        |

---

# 🧰 Useful Commands

## View Running Containers

```bash
docker ps
```

## View Logs

```bash
docker compose logs -f
```

## Restart Stack

```bash
docker compose restart
```

## Stop Stack

```bash
docker compose down
```

---

# 🎯 Final Notes

This monitoring stack provides:

* 📈 Real-time observability
* 🚨 Intelligent alerting
* 📊 Beautiful dashboards
* 🔒 Secure monitoring infrastructure
* ⚡ Scalable deployment architecture

Perfect for:

* Homelabs 🏠
* VPS monitoring ☁️
* Production infrastructure 🏢
* Kubernetes environments ☸️
* Docker host monitoring 🐳


### 🔥 Top 10 Useful Links

1. **Awesome Prometheus Alerts (Main Collection)**
   Over 950+ ready-to-use Prometheus alert rules for Kubernetes, Docker, Linux, databases, observability stacks, networking, and more.
   [Awesome Prometheus Alerts](https://samber.github.io/awesome-prometheus-alerts)

2. **GitHub Repository – Awesome Prometheus Alerts**
   Source repository containing YAML alert rules and contributions from the community.
   [awesome-prometheus-alerts GitHub Repo](https://github.com/samber/awesome-prometheus-alerts)

---

These resources cover almost everything needed for:

* Docker monitoring 🐳
* Kubernetes ☸️
* Linux servers 🖥️
* SSL monitoring 🔒
* Grafana Mimir/Tempo/Loki 📊
* Databases 💾
* Networking 🌐
* Cloud providers ☁️
* Alertmanager routing 🚨

