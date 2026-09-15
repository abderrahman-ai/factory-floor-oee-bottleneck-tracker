<div align="center">

<br/>

```
    _________   ________________  ______  __   ____  ____________
   / ____/   | / ____/_  __/ __ \/ __ \ \/ /  / __ \/ ____/ ____/
  / /_  / /| |/ /     / / / / / / /_/ /\  /  / / / / __/ / __/   
 / __/ / ___ / /___  / / / /_/ / _, _/ / /  / /_/ / /___/ /___   
/_/   /_/  |_\____/ /_/  \____/_/ |_| /_/   \____/_____/_____/
```

<h3>Factory Floor OEE & Bottleneck Intelligence Tracker</h3>

<br/>

[![n8n](https://img.shields.io/badge/Built%20on-n8n-FF6584?style=flat-square&logo=n8n&logoColor=white)](https://n8n.io/)
[![Status](https://img.shields.io/badge/Status-Live-3ECF8E?style=flat-square)](https://n8n.io/)
[![Nodes](https://img.shields.io/badge/Nodes-16%20Nodes-1C3A5F?style=flat-square)](https://n8n.io/)
[![License](https://img.shields.io/badge/License-MIT-F7DF1E?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-00C48C?style=flat-square)](http://makeapullrequest.com)

<br/>

[**Quick Start**](#-installation) | [**Architecture**](#-architecture) | [**Node Inventory**](#-node-inventory) | [**Usage**](#-usage-examples)

<br/>

</div>

---

## What is this?

An automated n8n workflow for **Factory Floor OEE & Bottleneck Intelligence Tracker**. It processes incoming events, transforms data payloads, and handles conditional dispatch to downstream services.

| | Component | Purpose |
|---|---|---|
| **📥** | **StickyNote_Overview** | Ingests incoming webhooks or scheduled telemetry payloads |
| **🧠** | **StickyNote_Ingestion** | Evaluates logic conditions and enriches message data |
| **🚨** | **StickyNote_OEE** | Dispatches notifications and updates database records |

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
Supports incoming webhooks and scheduled cron jobs for automatic background processing.

---

**⚡ &nbsp;Data Normalization**  
Standardizes raw input fields before forwarding payloads to analytics databases.

---

**🔒 &nbsp;Error Handling**  
Catches execution exceptions to prevent failed runs from stopping pipeline flow.

</td>
<td width="50%" valign="top">

**🧠 &nbsp;Conditional Logic**  
Filters high-priority alerts so team members only receive urgent notifications.

---

**📊 &nbsp;System Synchronization**  
Keeps external databases, logs, and notification channels in sync.

---

**🔌 &nbsp;Easy Import**  
Import the blueprint JSON directly into your n8n workspace to get started.

</td>
</tr>
</table>

---

## 🔧 Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| Orchestration | [n8n](https://n8n.io/) | Workflow engine, cron scheduling, webhook routing |
| Execution Engine | Node.js / JavaScript | Payload parsing and custom data mapping |
| Transport Protocol | Webhook / REST APIs | API requests and notification delivery |
| Blueprint Format | JSON (n8n v1+) | Portable workflow definition file |

---

## ✅ Prerequisites

- **n8n instance** (self-hosted or [n8n Cloud](https://app.n8n.cloud))
- Relevant API credentials configured inside your n8n workspace

---

## ⚙️ Installation

### 1. Import the Workflow

```
Workflows -> Import from File -> workflow.json
```

### 2. Configure Credentials

```
+---------------------+-------------------+--------------------------------------+
| Credential          | Type              | Attach To                            |
+---------------------+-------------------+--------------------------------------+
| API / Webhook Keys  | HTTP / OAuth2     | Integration Nodes                    |
+---------------------+-------------------+--------------------------------------+
```

### 3. Activate Workflow

```
Workflows -> [Factory Floor OEE & Bottleneck Intelligence Tracker] -> Toggle Active
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

### cURL: Trigger Webhook

```bash
curl -X POST https://your-n8n-instance.com/webhook/factory-floor-oee-bottleneck-tracker \
  -H "Content-Type: application/json" \
  -d '{"timestamp": "2026-09-15T12:00:00Z", "event": "HEALTH_CHECK"}'
```

### Python: Send Event

```python
import requests

url = "https://your-n8n-instance.com/webhook/factory-floor-oee-bottleneck-tracker"
payload = {"event": "HEALTH_CHECK", "source": "python_script"}

res = requests.post(url, json=payload)
print("Response code:", res.status_code)
print("Data:", res.json())
```

---

## 📂 Project Structure

```
factory-floor-oee-bottleneck-tracker/
├── workflow.json      # Complete importable workflow definition
├── LICENSE            # MIT License file
└── README.md          # Project documentation
```

---

## 🤝 Contributing

Pull requests and issues are welcome.

```bash
# 1. Clone the repository
git clone https://github.com/abderrahman-ai/factory-floor-oee-bottleneck-tracker.git

# 2. Create your branch
git checkout -b patch/improvements

# 3. Commit your changes
git commit -m "docs: refine workflow description and node names"

# 4. Push to origin
git push origin patch/improvements
```

---

## 📄 License

Released under the **MIT License**. Check [`LICENSE`](LICENSE) for full details.

---

<div align="center">

<br/>

Built with [n8n](https://n8n.io/)

<br/>

**[Back to top](#)**

</div>
