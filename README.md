🧠 System Monitoring with Prometheus, Node Exporter & Grafana (Docker Compose)

📋 Overview

This project demonstrates a simple system monitoring setup using Prometheus, Node Exporter, and Grafana, all running as Docker containers.
It collects system metrics such as CPU usage and visualizes them in a Grafana dashboard.

---

🧩 Components

Prometheus – Metric collection and time-series database

Node Exporter – Exposes system metrics (CPU, memory, disk, etc.) from the host

Grafana – Visualization and dashboarding tool

---

🐳 Setup Using Docker Compose

1️⃣ Clone the repository

git clone https://github.com/your-username/prometheus-grafana-monitoring.git
cd prometheus-grafana-monitoring

2️⃣ Start the services

docker-compose up -d

This will start:

Prometheus (on port 9090)

Node Exporter (on port 9100)

Grafana (on port 3000)

---

⚙ Configuration Details

🧭 Prometheus

Configured to scrape metrics from Node Exporter and itself.
Example target:

scrape_configs:

- job_name: 'node'
  static_configs:
  - targets: ['node-exporter:9100']

📊 Grafana

After starting, open Grafana at:
👉 http://localhost:3000

Login with default credentials:
admin / admin

Then:

1. Add Prometheus as a data source (http://prometheus:9090)

2. Import or create a dashboard

3. Use metric:

rate(node_cpu_seconds_total[1m])

to visualize CPU usage.

---

📈 Example Dashboard

The sample Grafana dashboard tracks:

CPU Usage over time using node_cpu_seconds_total

System health summary via Node Exporter metrics

---

🧹 Stopping Services

docker-compose down

---

📚 Future Improvements

Add alerts via Alertmanager

Include more exporters (e.g., cAdvisor, Blackbox)

Use persistent storage for Prometheus and Grafana data
