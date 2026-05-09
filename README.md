# 🚀 Grafana Monitoring Platform

Welcome to the **Grafana Monitoring Platform** repository.  
This project is organized into separate client and server components to provide a scalable, maintainable, and production-ready monitoring ecosystem using Grafana and related observability tools.

---

# 📂 Repository Structure

```text
.
├── grafana_client/   # Frontend / UI related configurations and dashboards
├── grafana_server/   # Backend monitoring stack and infrastructure services
└── README.md         # Project documentation
````

---

# 📑 Project Index

| 📁 Directory      | 📄 Documentation                                 | 📝 Description                                                                                   |
| ----------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `grafana_client/` | [Open Client README](./grafana_client/README.md) | Grafana dashboards, UI configurations, visualization assets, and frontend monitoring resources   |
| `grafana_server/` | [Open Server README](./grafana_server/README.md) | Prometheus, Alertmanager, Docker Compose stack, exporters, and backend monitoring infrastructure |

---

# 🧩 Project Components

## 🖥️ grafana_server

The `grafana_server` module contains the backend monitoring stack and infrastructure services.

### Includes:

* Prometheus configuration 📦
* Alertmanager setup 🚨
* Docker Compose deployment 🐳
* Exporter integrations 🔌
* Monitoring infrastructure ⚡

### Core Services

| Service      | Purpose                       |
| ------------ | ----------------------------- |
| Grafana      | Visualization Platform        |
| Prometheus   | Metrics Collection & Storage  |
| Alertmanager | Alert Routing & Notifications |


## 🔌 grafana_client

The `grafana_client` module contains exporter-related configurations and monitoring integrations used for collecting metrics from various services and systems.

### Includes:

* Prometheus exporters 📦
* Exporter configurations ⚙️
* Service monitoring integrations 🔗
* Metrics collection endpoints 📊
* Custom exporter setups 🛠️

### Purpose

This component focuses on:

* Collecting infrastructure metrics 📈
* Exposing application statistics 📡
* Monitoring system resources 🖥️
* Providing data sources for Prometheus 📦
* Extending observability coverage 🌐


---

# 🌟 Features

- ✅ Real-Time Monitoring
- ✅ Docker-Based Deployment
- ✅ Grafana Dashboards
- ✅ Prometheus Metrics Collection
- ✅ Alertmanager Notifications
- ✅ Persistent Storage Support
- ✅ Modular Client/Server Architecture
- ✅ Production Ready Monitoring Stack

---

# 🚀 Quick Start

## Clone Repository

```bash
git clone https://github.com/meibraransari/grafana-stack-docker-compose.git
cd grafana-stack-docker-compose
```

---

## Start Monitoring Stack

```bash
cd grafana_server
mkdir -p ./data/{grafana,prometheus} && chmod -R 777 ./data
docker compose up -d
```

---

# 🌐 Default Ports

| Service      | Port   |
| ------------ | ------ |
| Grafana      | `3000` |
| Prometheus   | `9090` |
| Alertmanager | `9093` |

---

# 🔒 Security Recommendations

* Use strong passwords 🔑
* Restrict internal services 🌐
* Enable HTTPS via reverse proxy 🔒
* Secure persistent storage 💾
* Disable public signups 🚫

---

# 🎯 Final Notes

This repository provides a scalable observability platform suitable for:

* Homelabs 🏠
* VPS Monitoring ☁️
* Enterprise Infrastructure 🏢
* Kubernetes Clusters ☸️
* Docker Environments 🐳

Happy Monitoring 🚀


# ❤️ Contributing

Contributions are welcome!

Feel free to:

* Improve dashboards 📈
* Add exporters 🔌
* Optimize configurations ⚡
* Enhance alert rules 🚨
* Improve documentation 📚

---

# 📄 License

Licensed under the MIT License.

---
## 💼 Connect with Me 👇😊

*   🔥 [**YouTube**](https://www.youtube.com/@DevOpsinAction?sub_confirmation=1)
*   ✍️ [**Blog**](https://ibraransari.blogspot.com/)
*   💼 [**LinkedIn**](https://www.linkedin.com/in/ansariibrar/)
*   👨‍💻 [**GitHub**](https://github.com/meibraransari?tab=repositories)
*   💬 [**Telegram**](https://t.me/DevOpsinActionTelegram)
*   🐳 [**Docker Hub**](https://hub.docker.com/u/ibraransaridocker)

### ⭐ If You Found This Helpful...

***Please star the repo and share it! Thanks a lot!*** 🌟
