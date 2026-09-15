<div align="center">

<br/>

```
██████╗ ██████╗  ██████╗     ███╗   ██╗██████╗ ███╗   ██╗
██╔══██╗██╔══██╗██╔════╝     ████╗  ██║██╔══██╗████╗  ██║
██████╔╝██████╔╝██║  ███╗    ██╔██╗ ██║██████╔╝██╔██╗ ██║
██╔══██╗██╔═══╝ ██║   ██║    ██║╚██╗██║██╔═══╝ ██║╚██╗██║
██║  ██║██║     ╚██████╔╝    ██║ ╚████║██║     ██║ ╚████║
╚═╝  ╚═╝╚═╝      ╚═════╝     ╚═╝  ╚═══╝╚═╝     ╚═╝  ╚═══╝
                         FACTORY OEE
```

<h3>Factory Floor OEE & Bottleneck Intelligence Tracker</h3>

<br/>

[![n8n](https://img.shields.io/badge/Built%20on-n8n-FF6584?style=flat-square&logo=n8n&logoColor=white)](https://n8n.io/)
[![Status](https://img.shields.io/badge/Status-Live--Active-3ECF8E?style=flat-square)](https://n8n.io/)
[![Nodes](https://img.shields.io/badge/Nodes-16%20Nodes-1C3A5F?style=flat-square)](https://n8n.io/)
[![License](https://img.shields.io/badge/License-MIT-F7DF1E?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-00C48C?style=flat-square)](http://makeapullrequest.com)

<br/>

[**→ Quick Start**](#-installation) · [**→ Architecture**](#-architecture) · [**→ Node Inventory**](#-node-inventory) · [**→ Usage**](#-usage-examples)

<br/>

</div>

---

## What is this?

A production-ready, automated n8n pipeline for **Factory Floor OEE & Bottleneck Intelligence Tracker**. Designed for enterprise-grade execution, seamless API integration, and real-time operational dispatch.

| | Component | What it does |
|---|---|---|
| **📥** | **StickyNote_Overview** | Ingests triggers, webhooks, or scheduled telemetry payloads |
| **🧠** | **StickyNote_Ingestion** | Processes logic, evaluates conditions, and enriches data |
| **🚨** | **StickyNote_OEE** | Dispatches alert notifications, updates databases, and executes actions |

---

## 📑 Table of Contents

- [Architecture](#-architecture)
- [Core Features](#-core-features)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Node Inventory](#-node-inventory)
- [Usage Examples](#-usage-examples)
- [Project Structure](#-project-structure)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🏗 Architecture

```mermaid
%%{init: {'theme': 'dark', 'themeVariables': {'primaryColor': '#1a1a2e', 'primaryTextColor': '#e0e0e0', 'primaryBorderColor': '#F39C12', 'lineColor': '#F39C12', 'secondaryColor': '#16213e', 'edgeLabelBackground': '#0d0d0d', 'clusterBkg': '#0d0d0d'}}}%%
graph TD
    StickyNote_Overview["StickyNote_Overview<br/><i>(stickyNote)</i>"]
    StickyNote_Ingestion["StickyNote_Ingestion<br/><i>(stickyNote)</i>"]
    StickyNote_OEE["StickyNote_OEE<br/><i>(stickyNote)</i>"]
    StickyNote_AI["StickyNote_AI<br/><i>(stickyNote)</i>"]
    StickyNote_Reporting["StickyNote_Reporting<br/><i>(stickyNote)</i>"]
    Schedule_ShiftHandover["Schedule_ShiftHandover<br/><i>(scheduleTrigger)</i>"]
    Webhook_TelemetryIngest["Webhook_TelemetryIngest<br/><i>(webhook)</i>"]
    StateTracking_Engine["StateTracking_Engine<br/><i>(code)</i>"]
    OEE_ComputationEngine["OEE_ComputationEngine<br/><i>(code)</i>"]
    Downtime_ParetoPreprocessor["Downtime_ParetoPreprocessor<br/><i>(code)</i>"]
    AI_BottleneckSynthesizer["AI_BottleneckSynthesizer<br/><i>(chainLlm)</i>"]
    Gemini_ChatModel["Gemini_ChatModel<br/><i>(lmChatGoogleGemini)</i>"]
    Consolidate_AI_Insights["Consolidate_AI_Insights<br/><i>(code)</i>"]
    Executive_ReportGenerator["Executive_ReportGenerator<br/><i>(code)</i>"]
    Telegram_ExecutiveDispatch["Telegram_ExecutiveDispatch<br/><i>(telegram)</i>"]
    Webhook_ResponsePayload["Webhook_ResponsePayload<br/><i>(set)</i>"]
    AI_BottleneckSynthesizer --> Consolidate_AI_Insights
    Consolidate_AI_Insights --> Executive_ReportGenerator
    Downtime_ParetoPreprocessor --> AI_BottleneckSynthesizer
    Executive_ReportGenerator --> Telegram_ExecutiveDispatch
    Executive_ReportGenerator --> Webhook_ResponsePayload
    Gemini_ChatModel --> AI_BottleneckSynthesizer
    OEE_ComputationEngine --> Downtime_ParetoPreprocessor
    Schedule_ShiftHandover --> StateTracking_Engine
    StateTracking_Engine --> OEE_ComputationEngine
    Webhook_TelemetryIngest --> StateTracking_Engine
```

---

## ✦ Core Features

<table>
<tr>
<td width="50%" valign="top">

**📡 &nbsp;Event-Driven Triggering**  
Supports real-time webhooks and automated cron schedules for instant event evaluation without polling overhead.

---

**⚡ &nbsp;High-Throughput Processing**  
Structured data transformation nodes handle high payload concurrency with zero data degradation.

---

**🔒 &nbsp;Robust Error Handling**  
Built-in fallback handlers ensure graceful failures, detailed logging, and operational safety.

</td>
<td width="50%" valign="top">

**🧠 &nbsp;Intelligent Logic Routing**  
Conditional evaluation branches route high-priority anomalies directly to incident response teams.

---

**📊 &nbsp;Unified Telemetry Sync**  
Synchronizes metrics and operational logs across databases, analytical dashboards, and alert channels.

---

**🔌 &nbsp;Zero-Code Integration**  
Modular n8n blueprint imports directly into any n8n instance with zero extra dependencies.

</td>
</tr>
</table>

---

## 🔧 Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| Orchestration | [n8n](https://n8n.io/) | Workflow engine, cron scheduling, webhook handling |
| Execution Engine | Node.js / JavaScript | Code execution and custom payload transformations |
| Communication | Webhook / REST APIs | Bi-directional API integrations & alert dispatch |
| Blueprint Format | JSON (n8n v1+) | Importable, version-controlled workflow definition |

---

## ✅ Prerequisites

- **n8n instance** — self-hosted (v1.0+) or [n8n Cloud](https://app.n8n.cloud)
- **API Credentials** — Configure relevant integration service credentials inside your n8n credentials panel.

---

## ⚙️ Installation

### 1 · Import the Workflow

```
Workflows → ⋯ → Import from File → workflow.json
```

### 2 · Attach Credentials

```
┌─────────────────────┬───────────────────┬──────────────────────────────────────┐
│ Credential          │ Type              │ Attach To                            │
├─────────────────────┼───────────────────┼──────────────────────────────────────┤
│ API / Webhook Keys  │ HTTP / OAuth2     │ Integration & Service Nodes          │
└─────────────────────┴───────────────────┴──────────────────────────────────────┘
```

### 3 · Activate

```
Workflows → [Factory Floor OEE & Bottleneck Intelligence Tracker] → Toggle to Active ✓
```

---

## 📑 Node Inventory

| # | Node Name | Type | Status |
|---|---|---|:---:|
| `01` | **StickyNote_Overview** | `stickyNote` | Active |
| `02` | **StickyNote_Ingestion** | `stickyNote` | Active |
| `03` | **StickyNote_OEE** | `stickyNote` | Active |
| `04` | **StickyNote_AI** | `stickyNote` | Active |
| `05` | **StickyNote_Reporting** | `stickyNote` | Active |
| `06` | **Schedule_ShiftHandover** | `scheduleTrigger` | Active |
| `07` | **Webhook_TelemetryIngest** | `webhook` | Active |
| `08` | **StateTracking_Engine** | `code` | Active |
| `09` | **OEE_ComputationEngine** | `code` | Active |
| `10` | **Downtime_ParetoPreprocessor** | `code` | Active |
| `11` | **AI_BottleneckSynthesizer** | `chainLlm` | Active |
| `12` | **Gemini_ChatModel** | `lmChatGoogleGemini` | Active |
| `13` | **Consolidate_AI_Insights** | `code` | Active |
| `14` | **Executive_ReportGenerator** | `code` | Active |
| `15` | **Telegram_ExecutiveDispatch** | `telegram` | Active |
| `16` | **Webhook_ResponsePayload** | `set` | Active |

---

## 🧪 Usage Examples

### cURL — Trigger Workflow Webhook

```bash
curl -X POST https://your-n8n-instance.com/webhook/factory-floor-oee-bottleneck-tracker \
  -H "Content-Type: application/json" \
  -d '{"timestamp": "2026-09-15T12:00:00Z", "status": "TRIGGER_EVALUATION"}'
```

### Python — Trigger Integration

```python
import requests

url = "https://your-n8n-instance.com/webhook/factory-floor-oee-bottleneck-tracker"
payload = {"event": "HEALTH_CHECK", "source": "python_agent"}

response = requests.post(url, json=payload)
print("Status Code:", response.status_code)
print("Response:", response.json())
```

---

## 📂 Project Structure

```
factory-floor-oee-bottleneck-tracker/
├── workflow.json      # Complete importable workflow definition
├── LICENSE            # MIT License file
└── README.md          # Comprehensive documentation
```

---

## 🤝 Contributing

Contributions, feature requests, and bug reports are welcome!

```bash
# 1. Fork the repository
git clone https://github.com/abderrahman-ai/factory-floor-oee-bottleneck-tracker.git

# 2. Create your feature branch
git checkout -b feat/new-capability

# 3. Commit your changes
git commit -m "feat: enhance node error handling"

# 4. Push and open a Pull Request
git push origin feat/new-capability
```

---

## 📄 License

Released under the **MIT License** — see [`LICENSE`](LICENSE) for full details.

---

<div align="center">

<br/>

Built with [n8n](https://n8n.io/) · Automated Enterprise Operations

<br/>

**[⬆ Back to top](#)**

</div>
