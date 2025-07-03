# Grafana and Prometheus Monitoring Setup
A minimal Docker Compose setup for deploying Prometheus and Grafana on a single machine. 

## Setup
Clone this repository with:
```sh
git clone https://github.com/kirillsaidov/grafana-prometheus-monitoring.git
```

### Configure
This is a simple monitoring setup with `node_exporter` installed locally. Please add correct address for `node_exporter` in [`prometheus/prometheus.yml`](./prometheus/prometheus.yml):
```yaml
scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['your_address:9100']
```

### Resource estimate
| Use Case                       | Targets | Scrape Interval | Retention  | **RAM**      | **Disk**        | **CPU**    |
| ------------------------------ | ------- | --------------- | ---------- | ------------ | --------------- | ---------- |
| 🧪 **Small (Dev/Test/Home)**   | 1–5     | 15s             | 15 days    | **2–3 GB**   | **5–10 GB**     | 1 core     |
| 🧩 **Medium (Team/Prod-lite)** | 5–25    | 15s–30s         | 30 days    | **4–8 GB**   | **20–50 GB**    | 2–4 cores  |
| 🏢 **Large (Prod/Infra-wide)** | 25–100+ | 5s–30s          | 30–90 days | **8–32+ GB** | **100–500+ GB** | 4–8+ cores |

### Install node exporter `node_exporter`:
#### Linux
```sh
# Ubuntu/Debian
sudo apt install prometheus-node-exporter

# CentOS/RHEL/Fedora
sudo yum install golang-github-prometheus-node_exporter
# or
sudo dnf install golang-github-prometheus-node_exporter
```

#### Windows
```sh
# Download latest release from GitHub
# Go to: https://github.com/prometheus/node_exporter/releases
# Download: node_exporter-*-windows-amd64.zip

# Extract and run
.\node_exporter.exe
```

#### Mac
```sh
# Install Homebrew first if you don't have it
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install node_exporter
brew install node_exporter

# Start the service
brew services start node_exporter

# Or run manually
node_exporter
```

## Run 
You need docker compose to run `Grafana` and `Prometheus`:
```sh
docker compose up -d
```

## LICENSE
Unlicense.

