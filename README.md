![Dashboard Preview](dashboard.png)

# 📞🔧 Asterisk Monitoring Stack — Prometheus + Grafana

A lightweight monitoring stack for **Asterisk PBX**, powered by `Prometheus`, `Grafana`, and a Python-based `asterisk_exporter`.

---

## 🧩 Stack Components

- 🧠 **Prometheus** – collects metrics from Asterisk and Python exporter.
- 📊 **Grafana** – dashboards for visualizing performance and peer status.
- 🐍 **asterisk_exporter** – Python Prometheus exporter for Asterisk metrics.

---

## 🚀 Quick Start

### 1. 📥 Clone the repository

```bash
git clone https://github.com/XlurichX/asterisk-stats.git
cd asterisk-stats
```

---

### 2. 🐳 Start the stack with Docker

```bash
docker-compose up -d
```

📁 **Included files**:

- `docker-compose.yml` – Runs Prometheus and Grafana containers  
- `prometheus/prometheus.yml` – Scrape config for Prometheus  
- `asterisk_dashboard.json` – Prebuilt Grafana dashboard (manual import)  
- `README_dashboard.md` – Description of dashboard metrics and layout  

---

### 3. ⚙️ Set up `asterisk_exporter`

**Requirements**:

- Python `3.6+`
- `pip`
- Asterisk with AMI access (`/etc/asterisk/manager.conf`)

Example `manager.conf`:

```ini
[general]
enabled = yes
port = 5038
bindaddr = 127.0.0.1

[exporter]
secret = <strong_password>
read = system,call,log,verbose,command,agent,user,config,originate
write = system,call,log,verbose,command,agent,user,config,originate
```

🔧 Install and run exporter:

```bash
pip install asterisk-exporter

asterisk_exporter start \
  --host 0.0.0.0 \
  --port 8088 \
  --user exporter \
  --password <password_from_conf> &
```

---

### 4. 📟 Access Grafana

- Open: [http://localhost:3000](http://localhost:3000)
- Login: `admin` / `admin`

🧩 Connect data source:

1. Go to **Connections → Data sources**
2. Select **Prometheus**
3. Set URL to: `http://prometheus:9090`
4. Save & Test

📈 Import the dashboard:

- Create a new dashboard
- Click **Import**
- Upload `asterisk_dashboard.json`

📝 Panel and metric descriptions are available in [`README_dashboard.md`](./README_dashboard.md)

---

## 🛠️ Customize & Extend

Want more metrics? You can enhance the exporter to capture:

- 📞 Caller IDs  
- 📊 Call statistics  
- 🔄 Call direction (incoming/outgoing)  
- 📡 Trunk usage  

Check the asterisk_exporter code or fork this project to add more features.

---

## ✅ Result

A simple, effective way to monitor Asterisk with modern observability tools 🚀

