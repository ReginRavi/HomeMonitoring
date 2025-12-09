# Home Network Monitoring

Monitor your home network devices using Prometheus, Grafana, and Blackbox Exporter.

## Features

- 🏠 **Device Monitoring** - Ping monitoring for all network devices
- 📊 **Latency Tracking** - Real-time latency graphs
- ✅ **Uptime Monitoring** - Track device availability
- 🌐 **Internet Connectivity** - Monitor connection to external DNS

## Quick Start

```bash
# Start the monitoring stack
docker compose up -d

# Access Grafana
open http://localhost:3001
# Login: admin / admin
```

## Services

| Service | Port | Description |
|---------|------|-------------|
| Grafana | 3001 | Dashboards & Visualization |
| Prometheus | 9091 | Metrics Storage |
| Blackbox Exporter | 9115 | ICMP/HTTP Probing |

## Adding Devices

Edit `prometheus/prometheus.yml` and add device IPs to the `blackbox-icmp` targets:

```yaml
- targets:
    - 192.168.0.1    # Router
    - 192.168.0.100  # New device
```

Then restart Prometheus:
```bash
docker restart home-prometheus
```

## Project Structure

```
├── docker-compose.yml
├── prometheus/
│   └── prometheus.yml
├── blackbox-exporter/
│   └── blackbox.yml
└── grafana/
    ├── dashboards/
    └── provisioning/
```
