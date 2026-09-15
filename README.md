<div align="center">

# 🚀 —F—a—c—t—o—r—y— —F—l—o—o—r— —O—E—E— —&— —B—o—t—t—l—e—n—e—c—k— —I—n—t—e—l—l—i—g—e—n—c—e— —T—r—a—c—k—e—r—

**An end-to-end, enterprise-grade n8n automation workflow.**

[![n8n](https://img.shields.io/badge/n8n-%23FF6584.svg?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io/)
[![Status](https://img.shields.io/badge/Status-Active%20(Live)-success?style=for-the-badge)](https://n8n.io/)
[![Nodes](https://img.shields.io/badge/Nodes-16-blue?style=for-the-badge)](https://n8n.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

</div>

---

## 📌 Executive Summary

This n8n workflow provides a production-ready automation pipeline for **—F—a—c—t—o—r—y— —F—l—o—o—r— —O—E—E— —&— —B—o—t—t—l—e—n—e—c—k— —I—n—t—e—l—l—i—g—e—n—c—e— —T—r—a—c—k—e—r—**. It ingests incoming data, processes payloads through configured logic nodes, and routes insights/alerts across downstream channels.

---

## ⚡ Key Capabilities

* **🔄 End-to-End Automation:** Streamlines multi-step data processing and triggers actions automatically.
* **🧠 Intelligent Data Handling:** Integrates specialized nodes for data transformation, conditional evaluation, and API communication.
* **🚨 Real-Time Monitoring & Dispatch:** Ensures rapid incident response and data sync across connected systems.
* **📊 Scalable & Modular Architecture:** Built with n8n best practices for error handling, modularity, and high throughput.

---

## 📌 System Architecture & Process Flow

```mermaid
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

## 📂 Node Inventory & Pipeline Components

| # | Node Name | Type | Disabled |
|---|---|---|:---:|
| 1 | **StickyNote_Overview** | `stickyNote` | No |
| 2 | **StickyNote_Ingestion** | `stickyNote` | No |
| 3 | **StickyNote_OEE** | `stickyNote` | No |
| 4 | **StickyNote_AI** | `stickyNote` | No |
| 5 | **StickyNote_Reporting** | `stickyNote` | No |
| 6 | **Schedule_ShiftHandover** | `scheduleTrigger` | No |
| 7 | **Webhook_TelemetryIngest** | `webhook` | No |
| 8 | **StateTracking_Engine** | `code` | No |
| 9 | **OEE_ComputationEngine** | `code` | No |
| 10 | **Downtime_ParetoPreprocessor** | `code` | No |
| 11 | **AI_BottleneckSynthesizer** | `chainLlm` | No |
| 12 | **Gemini_ChatModel** | `lmChatGoogleGemini` | No |
| 13 | **Consolidate_AI_Insights** | `code` | No |
| 14 | **Executive_ReportGenerator** | `code` | No |
| 15 | **Telegram_ExecutiveDispatch** | `telegram` | No |
| 16 | **Webhook_ResponsePayload** | `set` | No |

---

## ⚙️ Setup & Deployment Instructions

### 1. Import Workflow Blueprint
1. Download the [`workflow.json`](./workflow.json) file from this repository.
2. Open your **n8n instance**.
3. Click **Workflows** -> **Import from File**.
4. Select `workflow.json`.

### 2. Configure Credentials & Environment
* Set up required API tokens, webhooks, or database credentials for any integrated service nodes.
* Ensure relevant environment variables or global variables referenced in Code/HTTP nodes are populated in your n8n settings.

### 3. Activate Pipeline
* Toggle the workflow status to **Active** to begin live execution.

---

## 🤝 Contribution & Maintenance

Contributions, improvements, and bug fixes are welcome! Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
