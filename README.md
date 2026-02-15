# clawland-grafana

Grafana data source plugin for the Clawland edge AI ecosystem.

---

## Overview

`clawland-grafana` is a Grafana data source plugin that connects to the [clawland-fleet](https://github.com/Clawland-AI/clawland-fleet) API, enabling deep visualization of edge node metrics, sensor data, and fleet health in Grafana dashboards.

## Features

- **Sensor Data Queries** — Query temperature, humidity, dissolved oxygen, and any sensor data from edge nodes
- **Fleet Metrics** — Node uptime, CPU/memory usage, network latency, agent session counts
- **Alert History** — Visualize alert patterns, resolution times, and escalation chains
- **Node Comparison** — Compare metrics across multiple nodes and groups
- **Annotations** — Auto-annotate graphs with alert events and command executions
- **Variables** — Template variables for node ID, node group, sensor type, and time range

## Quick Start

### Installation

```bash
# Install via Grafana CLI
grafana-cli plugins install clawland-datasource

# Or build from source
git clone https://github.com/Clawland-AI/clawland-grafana.git
cd clawland-grafana
mage build
```

### Configuration

1. Add data source in Grafana → Configuration → Data Sources
2. Select "Clawland Fleet"
3. Enter your moltclaw Fleet Manager URL and API key
4. Click "Save & Test"

## Example Dashboards

Pre-built dashboards included:

| Dashboard | Description |
|-----------|-------------|
| **Fleet Overview** | All nodes health matrix with uptime and alerts |
| **Datacenter Monitoring** | Server room temperature, humidity, UPS status |
| **Aquaculture** | Dissolved oxygen, pH, temperature per pond |
| **Sensor Deep Dive** | Single sensor historical analysis with trends |

## Tech Stack

| Component | Technology |
|-----------|------------|
| Plugin Backend | Go (Grafana Plugin SDK) |
| Plugin Frontend | React + TypeScript |
| Data Protocol | JSON over HTTP |
| Build | Mage |

## Directory Structure

```
clawland-grafana/
├── pkg/
│   ├── plugin/
│   │   ├── datasource.go      # Data source implementation
│   │   ├── query.go            # Query handlers
│   │   └── models.go           # Data models
│   └── fleet/
│       └── client.go           # Fleet API client
├── src/
│   ├── components/
│   │   ├── ConfigEditor.tsx    # Data source config UI
│   │   └── QueryEditor.tsx     # Query builder UI
│   └── module.ts               # Plugin entry point
├── provisioning/
│   └── dashboards/             # Pre-built dashboard JSON
│       ├── fleet-overview.json
│       ├── datacenter.json
│       └── aquaculture.json
├── go.mod
├── package.json
├── LICENSE                      # Apache 2.0
└── README.md
```

## Related Repositories

- [clawland-fleet](https://github.com/Clawland-AI/clawland-fleet) — Backend API for fleet data
- [clawland-dashboard](https://github.com/Clawland-AI/clawland-dashboard) — Dedicated Clawland dashboard
- [moltclaw](https://github.com/Clawland-AI/moltclaw) — Cloud AI Gateway

## Contributing

See [CONTRIBUTING.md](https://github.com/Clawland-AI/.github/blob/main/CONTRIBUTING.md). Plugin development earns contribution points toward the quarterly [Revenue Pool](https://github.com/Clawland-AI/.github/blob/main/CONTRIBUTOR-REVENUE-SHARE.md).

## License

Apache 2.0 — See [LICENSE](LICENSE)
