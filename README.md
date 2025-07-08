# 🤖 AI Sales Agent (n8n + GPT + CRM + Calendar)

An AI-powered multi-channel sales agent built using **n8n**, **OpenAI GPT**, **Airtable CRM**, and **Meta APIs** (WhatsApp, Facebook, Instagram). The agent qualifies leads, responds intelligently via GPT, logs to CRM, and schedules consultations — fully automated.

---

## 🌟 Features

- 🔗 **Multi-Channel Triggers**: WhatsApp, Facebook Messenger, Instagram, and Website Chat
- 🧠 **GPT-Powered Conversations**: Smart replies for Paint Protection Film (PPF), Ceramic Coating, Window Tint
- 🔍 **Lead Qualification Flow**: State-based intent capture → contact info → scheduling
- 🗒️ **Consultation Booking**: Integrated with `calendarAgent` workflow
- 🗂️ **CRM Automation**: Creates/updates Contacts and Opportunities in Airtable via `crmAgent`
- 🗣️ **Voice Support**: Audio messages transcribed via OpenAI Whisper
- 🧠 **Memory Persistence**: Session-aware using PostgreSQL memory node

---

## 📌 Architecture Overview

```
Meta Platforms (WA/FB/IG) or Chat UI
    ↓
Webhook Trigger
    ↓
Preprocessing & Session Handling
    ↓
GPT Agent (LangChain + OpenAI Chat Model)
    ↓
State Machine Logic:
  → Qualify → Collect Info → Log to CRM → Schedule → Confirm
    ↓
CRM Agent (Airtable API) & Calendar Agent
    ↓
Channel-specific response
```

---

## 🔧 Stack & Technologies

| Component           | Tech Used                                                   |
| ------------------- | ----------------------------------------------------------- |
| Workflow Engine     | n8n (Self-hosted or Cloud)                                  |
| LLM                 | OpenAI GPT-4o via LangChain plugin                          |
| Voice Transcription | OpenAI Whisper (audio to text)                              |
| CRM                 | Airtable                                                    |
| Calendar Booking    | Sub-agent using `calendarAgent`                             |
| Data Storage        | PostgreSQL memory + Airtable                                |
| Channels Supported  | WhatsApp Cloud API, Instagram, Facebook, Website Chat       |
| Integrations        | Webhooks, HTTP, JSON Mapping, Conditions, Switch, Custom JS |

---

## ♻️ Conversation Flow States

1. **INITIAL** – Greet and listen
2. **QUALIFYING** – Understand interest in services
3. **CONTACT\_COLLECTION** – Collect Name & Email (only if not from WhatsApp)
4. **SCHEDULING** – Book via calendar agent and log opportunity
5. **FOLLOW\_UP** – Confirm date/time and close politely

---

## 📁 Repository Structure (recommended layout)

```
ai-sales-agent-n8n/
├── workflows/
│   └── ai_sales_agent_workflow.json
├── assets/
│   └── preview.png
├── README.md
└── .env.example
```

---

## 🚀 Getting Started

1. **Import Workflow** into n8n (use the provided `.json`)
2. **Set up Credentials**:
   - OpenAI API Key
   - WhatsApp Cloud API
   - Airtable API Key
   - Facebook & Instagram Graph API setup
3. **Create Sub-Agent Workflows**:
   - `calendarAgent` – for booking logic
   - `crmAgent` – for Airtable actions (create/update contacts/opportunities)
4. **Configure Webhook URLs** in Meta platforms
5. **Test Trigger Events** from WhatsApp/Facebook/IG

---

## 🧠 Prompt Engineering

The GPT agent uses a carefully crafted `systemMessage` with:

- Service domain limits (PPF, Ceramic, Tint)
- Conversational rules (160 char max, friendly, no lists)
- Dynamic state-based logic
- Contextual memory for contact & CRM data
- Embedded tool usage (`calendarAgent`, `crmAgent`)

---

## 📸 Preview



---

## 📬 Contact

Built with 🔧 by [Vivek Pandey](https://www.linkedin.com/in/vivek-pandey-tech/)\
Email: [vivek110902@outlook.com](mailto\:vivek110902@outlook.com)\
Custom workflows & AI agents on request 🚀

---

## 🧪 License

MIT License – use freely and modify as needed.

