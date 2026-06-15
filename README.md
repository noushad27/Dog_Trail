<div align="center">

<img src="https://img.shields.io/badge/version-1.0.0--beta-blueviolet?style=for-the-badge" />
<img src="https://img.shields.io/badge/license-MIT-green?style=for-the-badge" />
<img src="https://img.shields.io/badge/python-3.11+-blue?style=for-the-badge&logo=python" />
<img src="https://img.shields.io/badge/react-18-61DAFB?style=for-the-badge&logo=react" />
<img src="https://img.shields.io/badge/status-active--development-orange?style=for-the-badge" />

<br />
<br />

```
██████╗  ██████╗  ██████╗     ████████╗██████╗  █████╗ ██╗██╗
██╔══██╗██╔═══██╗██╔════╝     ╚══██╔══╝██╔══██╗██╔══██╗██║██║
██║  ██║██║   ██║██║  ███╗       ██║   ██████╔╝███████║██║██║
██║  ██║██║   ██║██║   ██║       ██║   ██╔══██╗██╔══██║██║██║
██████╔╝╚██████╔╝╚██████╔╝       ██║   ██║  ██║██║  ██║██║███████╗
╚═════╝  ╚═════╝  ╚═════╝        ╚═╝   ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝╚══════╝
```

# 🐾 Dog Trail
### *Hunt the rogue. Protect your network.*

**Dog Trail** is an open-source, consumer-friendly WiFi threat detection platform that sniffs out evil twin attacks, rogue access points, deauth floods, and suspicious networks — then explains everything in plain English using AI.

**No hacker knowledge needed. Your WiFi just got a guard dog.**

<br/>

[🚀 Quick Start](#-quick-start) · [📐 Architecture](#-architecture) · [🧠 AI Engine](#-ai-engine) · [📁 Project Structure](#-project-structure) · [🗺️ Roadmap](#-roadmap) · [🤝 Contributing](#-contributing)

<br/>

---

</div>

## 📌 What Is Dog Trail?

Most people have no idea if they're connected to a fake WiFi hotspot designed to steal their credentials, or if someone nearby is flooding deauthentication packets to kick them off a network. These attacks are real, cheap to execute, and invisible to the average user.

**Dog Trail changes that.**

It runs quietly in the background on your machine, sniffs the WiFi airspace around you using packet capture in monitor mode, detects anomalies using a trained Isolation Forest ML model, and delivers human-readable threat explanations via an integrated LLM (Anthropic Claude). Everything is surfaced through a clean, beautiful React/Electron desktop interface built for **non-technical users**.

Think of it as **Wireshark for your mom** — with AI threat analysis baked in.

---

## ✨ Features

| Category | Feature | Status |
|---|---|---|
| 🔍 **Threat Detection** | Evil Twin Attack Detection | ✅ Planned |
| 🔍 **Threat Detection** | Rogue Access Point Scanner | ✅ Planned |
| 🔍 **Threat Detection** | Deauthentication Flood Detection | ✅ Planned |
| 🔍 **Threat Detection** | Suspicious SSID / Hidden Network Alerts | ✅ Planned |
| 🔍 **Threat Detection** | PMKID / EAPOL Handshake Detection | 🔜 v1.1 |
| 🧠 **AI Engine** | Isolation Forest Anomaly Detection | ✅ Planned |
| 🧠 **AI Engine** | LLM-Powered Threat Explanations (Claude API) | ✅ Planned |
| 🧠 **AI Engine** | Auto-Severity Classification (Low / Medium / High / Critical) | ✅ Planned |
| 🧠 **AI Engine** | AI Suggested Remediation Steps | ✅ Planned |
| 📡 **Scanner** | Passive Packet Capture via Scapy | ✅ Planned |
| 📡 **Scanner** | Live SSID / BSSID / RSSI Monitoring | ✅ Planned |
| 📡 **Scanner** | Multi-channel Sweep | ✅ Planned |
| 💾 **Backend** | FastAPI REST Backend | ✅ Planned |
| 💾 **Backend** | SQLite Threat History Database | ✅ Planned |
| 💾 **Backend** | Real-time WebSocket Event Streaming | ✅ Planned |
| 🖥️ **Frontend** | React + Electron Desktop App | ✅ Planned |
| 🖥️ **Frontend** | Live Threat Feed Dashboard | ✅ Planned |
| 🖥️ **Frontend** | Historical Threat Log Viewer | ✅ Planned |
| 🖥️ **Frontend** | Network Map Visualization | 🔜 v1.1 |
| 🔔 **Alerts** | Desktop Notifications on Threat Detection | ✅ Planned |
| 🔔 **Alerts** | Sound Alert on Critical Threat | 🔜 v1.1 |
| 📤 **Export** | Export Threat Report as PDF | 🔜 v1.1 |

---

## 🧠 AI Engine

Dog Trail's intelligence layer has two components working together:

### 1. Isolation Forest (Anomaly Detection)
A trained `sklearn` Isolation Forest model analyzes the behavioral fingerprint of every access point and frame pattern in the environment. Features fed into the model include:

- Signal strength delta across channels
- Beacon frame interval variance
- SSID/BSSID mismatches (duplicate SSIDs, different BSSIDs)
- Deauthentication packet rate spike
- Probe response anomaly ratio

If a data point scores as an outlier — it gets flagged.

### 2. Claude LLM (Threat Narration)
Every flagged threat is passed to the **Anthropic Claude API**, which generates:

- A plain-English **explanation** of what the threat actually means
- A **severity score** with justification
- **Step-by-step remediation** advice the user can actually follow

> *"We detected a second access point broadcasting the same network name (SSID) as your router but from a different device. This is a classic Evil Twin attack — someone nearby may be trying to intercept your traffic. We recommend disconnecting from this network and verifying your router's MAC address."*

This is what makes Dog Trail different from every other WiFi scanning tool: **anyone can understand it.**

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    DOG TRAIL SYSTEM                     │
│                                                         │
│  ┌──────────────┐     ┌──────────────────────────────┐  │
│  │   Hardware   │     │        CORE ENGINE           │  │
│  │              │     │                              │  │
│  │  USB WiFi    │────▶│  Scapy (Monitor Mode)        │  │
│  │  Adapter     │     │  ├── Beacon Frame Parser     │  │
│  │  (Monitor    │     │  ├── Deauth Frame Detector   │  │
│  │   Mode)      │     │  └── Probe Request Sniffer   │  │
│  └──────────────┘     └──────────────┬───────────────┘  │
│                                      │                  │
│                                      ▼                  │
│                       ┌──────────────────────────────┐  │
│                       │        AI ENGINE             │  │
│                       │                              │  │
│                       │  Isolation Forest            │  │
│                       │  (sklearn anomaly detection) │  │
│                       │          +                   │  │
│                       │  Claude API                  │  │
│                       │  (threat explanation & NLP)  │  │
│                       └──────────────┬───────────────┘  │
│                                      │                  │
│                                      ▼                  │
│                       ┌──────────────────────────────┐  │
│                       │      FASTAPI BACKEND         │  │
│                       │                              │  │
│                       │  REST API + WebSocket        │  │
│                       │  SQLite (threat history)     │  │
│                       └──────────────┬───────────────┘  │
│                                      │                  │
│                                      ▼                  │
│                       ┌──────────────────────────────┐  │
│                       │   REACT / ELECTRON DESKTOP   │  │
│                       │                              │  │
│                       │  Live Threat Dashboard       │  │
│                       │  AI Explanation Panel        │  │
│                       │  Historical Log Viewer       │  │
│                       └──────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

---

## 🔍 Threat Detection Logic

### Evil Twin Attack
Dog Trail scans for duplicate SSIDs broadcasting from different BSSIDs (MAC addresses). When it detects two access points with the same name but different hardware identities, it raises an alert and cross-references signal strength and channel data to identify the impersonator.

```
SSID: "HomeNetwork"   BSSID: AA:BB:CC:11:22:33  ← Legitimate Router
SSID: "HomeNetwork"   BSSID: DE:AD:BE:EF:00:01  ← ⚠️ EVIL TWIN
```

### Deauthentication Flood
A spike in 802.11 deauthentication frames is a classic precursor to a Man-in-the-Middle attack. Dog Trail monitors deauth frame rate per time window and fires an alert when the rate exceeds the configured threshold.

### Rogue Access Point
Unknown access points that weren't present in the user's baseline trusted-networks list are flagged for review. Dog Trail maintains a local "known networks" whitelist in SQLite.

### Suspicious Hidden Networks
Probe responses from hidden SSIDs (empty SSID field in beacon frames) are logged and surfaced. If a hidden AP is broadcasting on the same channel as a user's known router, it triggers a Medium alert.

---

## 📁 Project Structure

```
dog-trail/
│
├── 📄 README.md                      ← You're here
├── 📄 LICENSE                        ← MIT License
├── 📄 .env.example                   ← Environment variable template
├── 📄 .gitignore
├── 📄 requirements.txt               ← Python dependencies
├── 📄 package.json                   ← Root Node.js config (Electron)
│
├── 📂 backend/                       ← Python / FastAPI Core
│   │
│   ├── 📄 main.py                    ← FastAPI app entrypoint
│   ├── 📄 config.py                  ← App configuration & env loading
│   │
│   ├── 📂 scanner/                   ← Packet capture engine
│   │   ├── 📄 __init__.py
│   │   ├── 📄 sniffer.py             ← Scapy monitor mode packet capture
│   │   ├── 📄 frame_parser.py        ← 802.11 beacon/probe/deauth parser
│   │   ├── 📄 channel_hopper.py      ← Multi-channel sweep logic
│   │   └── 📄 monitor_mode.py        ← Interface config & monitor mode setup
│   │
│   ├── 📂 detection/                 ← Threat detection logic
│   │   ├── 📄 __init__.py
│   │   ├── 📄 evil_twin.py           ← Evil twin attack detector
│   │   ├── 📄 deauth_flood.py        ← Deauth flood rate detector
│   │   ├── 📄 rogue_ap.py            ← Rogue AP detection vs whitelist
│   │   ├── 📄 hidden_ssid.py         ← Hidden network anomaly detector
│   │   └── 📄 threat_classifier.py   ← Severity scoring (LOW/MED/HIGH/CRIT)
│   │
│   ├── 📂 ai/                        ← AI & ML engine
│   │   ├── 📄 __init__.py
│   │   ├── 📄 isolation_forest.py    ← sklearn Isolation Forest model
│   │   ├── 📄 feature_extractor.py   ← Feature engineering from raw frames
│   │   ├── 📄 llm_explainer.py       ← Anthropic API: threat narration
│   │   ├── 📄 model_trainer.py       ← Offline model training script
│   │   └── 📂 models/                ← Serialized .pkl model files
│   │       └── 📄 isolation_forest_v1.pkl
│   │
│   ├── 📂 api/                       ← FastAPI routes
│   │   ├── 📄 __init__.py
│   │   ├── 📄 routes_threats.py      ← GET/POST threat endpoints
│   │   ├── 📄 routes_scanner.py      ← Scanner start/stop/status
│   │   ├── 📄 routes_networks.py     ← Known networks whitelist CRUD
│   │   └── 📄 websocket.py           ← WS: real-time threat event stream
│   │
│   ├── 📂 database/                  ← SQLite ORM & migrations
│   │   ├── 📄 __init__.py
│   │   ├── 📄 models.py              ← SQLAlchemy table definitions
│   │   ├── 📄 crud.py                ← Create/Read/Update/Delete helpers
│   │   └── 📄 db.py                  ← DB session factory
│   │
│   └── 📂 tests/                     ← Backend unit & integration tests
│       ├── 📄 test_detection.py
│       ├── 📄 test_ai.py
│       └── 📄 test_api.py
│
├── 📂 frontend/                      ← React + Electron Desktop App
│   │
│   ├── 📂 public/
│   │   └── 📄 index.html
│   │
│   ├── 📂 electron/                  ← Electron shell
│   │   ├── 📄 main.js                ← Electron main process
│   │   └── 📄 preload.js             ← Secure IPC bridge
│   │
│   └── 📂 src/
│       ├── 📄 App.jsx                ← Root app component
│       ├── 📄 index.jsx              ← React entrypoint
│       │
│       ├── 📂 components/            ← Reusable UI components
│       │   ├── 📄 ThreatCard.jsx     ← Individual threat display card
│       │   ├── 📄 ThreatBadge.jsx    ← Severity badge (color-coded)
│       │   ├── 📄 NetworkList.jsx    ← Detected networks table
│       │   ├── 📄 AIExplainer.jsx    ← Claude explanation panel
│       │   ├── 📄 ScannerStatus.jsx  ← Live scan status indicator
│       │   └── 📄 Notification.jsx   ← Desktop alert toast
│       │
│       ├── 📂 pages/                 ← App views/screens
│       │   ├── 📄 Dashboard.jsx      ← Main live threat feed
│       │   ├── 📄 History.jsx        ← Historical threat log
│       │   ├── 📄 Networks.jsx       ← Known networks whitelist manager
│       │   └── 📄 Settings.jsx       ← App configuration
│       │
│       ├── 📂 hooks/                 ← Custom React hooks
│       │   ├── 📄 useWebSocket.js    ← Real-time threat event subscription
│       │   └── 📄 useScanner.js      ← Scanner start/stop controls
│       │
│       ├── 📂 api/                   ← Frontend API client
│       │   └── 📄 client.js          ← Axios wrapper for FastAPI calls
│       │
│       └── 📂 styles/                ← Global styles
│           └── 📄 globals.css
│
├── 📂 hardware/                      ← Hardware setup docs
│   ├── 📄 ADAPTERS.md                ← Compatible USB WiFi adapter list
│   ├── 📄 MONITOR_MODE_SETUP.md      ← How to enable monitor mode
│   └── 📄 KALI_VIRTUALBOX.md        ← Kali Linux on VirtualBox guide
│
├── 📂 docs/                          ← Project documentation
│   ├── 📄 THREAT_TYPES.md            ← Detailed threat classification docs
│   ├── 📄 AI_MODEL.md                ← Isolation Forest training & features
│   ├── 📄 API_REFERENCE.md           ← Full FastAPI endpoint docs
│   └── 📄 ARCHITECTURE.md            ← Deep-dive system design
│
└── 📂 scripts/                       ← Dev & ops utility scripts
    ├── 📄 start_backend.sh           ← Launch FastAPI dev server
    ├── 📄 start_frontend.sh          ← Launch Electron/React app
    ├── 📄 train_model.py             ← Train/retrain Isolation Forest
    └── 📄 reset_db.py                ← Wipe & reinitialize SQLite DB
```

---

## 🛠️ Tech Stack

### Backend
| Tool | Purpose |
|---|---|
| **Python 3.11+** | Core language |
| **Scapy** | 802.11 packet capture & parsing |
| **FastAPI** | REST API + WebSocket server |
| **SQLite + SQLAlchemy** | Threat history persistence |
| **scikit-learn** | Isolation Forest anomaly detection |
| **Anthropic Claude API** | LLM-powered threat narration |
| **Uvicorn** | ASGI server |

### Frontend
| Tool | Purpose |
|---|---|
| **React 18** | UI framework |
| **Electron** | Desktop app shell |
| **Axios** | HTTP client for FastAPI |
| **WebSocket (native)** | Real-time threat streaming |
| **Tailwind CSS** | Styling |

### Dev & Infra
| Tool | Purpose |
|---|---|
| **Kali Linux (VirtualBox)** | Live packet capture environment |
| **Alfa AWUS036NHA / TP-Link TL-WN722N v1** | USB WiFi adapter (monitor mode) |
| **VS Code** | Primary IDE |
| **Git + GitHub** | Version control |

---

## 🚀 Quick Start

### Prerequisites

Before running Dog Trail, you'll need:

- Python 3.11+
- Node.js 18+
- A **USB WiFi adapter that supports monitor mode** (see [Compatible Adapters](hardware/ADAPTERS.md))
- Kali Linux or any Linux distro (for live scanning; Windows for frontend only)
- An **Anthropic API key** (for AI threat explanations)

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/dog-trail.git
cd dog-trail
```

### 2. Backend Setup

```bash
# Create a virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install Python dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env
# Edit .env and add your ANTHROPIC_API_KEY
```

### 3. Frontend Setup

```bash
cd frontend
npm install
```

### 4. Enable Monitor Mode

```bash
# Set your WiFi adapter to monitor mode (requires root/sudo on Linux)
sudo ip link set wlan1 down
sudo iw dev wlan1 set type monitor
sudo ip link set wlan1 up

# Or run the automated setup script
sudo bash scripts/start_backend.sh
```

> 📖 For detailed hardware setup, see [Monitor Mode Setup Guide](hardware/MONITOR_MODE_SETUP.md)

### 5. Launch

```bash
# Terminal 1 — Start the backend
cd backend
uvicorn main:app --reload --host 0.0.0.0 --port 8000

# Terminal 2 — Start the frontend desktop app
cd frontend
npm run electron
```

Dog Trail will open as a desktop application. Hit **"Start Scan"** and watch the guard dog go to work. 🐾

---

## 📡 Hardware Requirements

Dog Trail requires a **USB WiFi adapter with monitor mode support** to perform passive packet capture.

### ✅ Confirmed Compatible Adapters

| Adapter | Chipset | Monitor Mode | Packet Injection | Price |
|---|---|---|---|---|
| **Alfa AWUS036NHA** | Atheros AR9271 | ✅ Yes | ✅ Yes | ~$35 |
| **TP-Link TL-WN722N v1** | Atheros AR9271 | ✅ Yes | ✅ Yes | ~$15 |
| **Alfa AWUS036ACH** | RTL8812AU | ✅ Yes | ✅ Yes | ~$50 |

> ⚠️ **Important:** TP-Link TL-WN722N **v2 and v3** use a different chipset and do NOT support monitor mode. Only **v1** is compatible.

> See the full compatibility list in [hardware/ADAPTERS.md](hardware/ADAPTERS.md)

---

## 🔌 API Reference

Dog Trail exposes a REST API + WebSocket on `http://localhost:8000`.

### Threat Endpoints

```
GET    /api/threats              → List all detected threats (paginated)
GET    /api/threats/{id}         → Get a single threat with AI explanation
DELETE /api/threats/{id}         → Dismiss/delete a threat record
```

### Scanner Endpoints

```
POST   /api/scanner/start        → Start packet capture on the given interface
POST   /api/scanner/stop         → Stop the active scan session
GET    /api/scanner/status       → Get current scanner state and stats
```

### Networks Endpoints

```
GET    /api/networks             → List all detected networks
GET    /api/networks/trusted     → Get user's trusted networks whitelist
POST   /api/networks/trusted     → Add a network to the whitelist
DELETE /api/networks/trusted/{bssid} → Remove a network from whitelist
```

### WebSocket

```
WS     /ws/threats               → Real-time threat event stream (JSON)
```

**Threat Event Payload:**
```json
{
  "event": "threat_detected",
  "timestamp": "2025-06-15T14:30:00Z",
  "threat": {
    "id": "uuid",
    "type": "EVIL_TWIN",
    "severity": "HIGH",
    "ssid": "HomeNetwork",
    "bssid_attacker": "DE:AD:BE:EF:00:01",
    "bssid_legitimate": "AA:BB:CC:11:22:33",
    "channel": 6,
    "rssi": -62,
    "ai_explanation": "A second device is broadcasting under your network name...",
    "ai_remediation": "1. Disconnect immediately. 2. Verify your router MAC..."
  }
}
```

> Full API docs available at `http://localhost:8000/docs` (Swagger UI auto-generated by FastAPI)

---

## 🗺️ Roadmap

### v1.0.0 — Foundation (Current)
- [x] Project architecture & structure defined
- [ ] Scapy packet sniffer with monitor mode
- [ ] Evil twin & deauth flood detection
- [ ] Isolation Forest anomaly model
- [ ] FastAPI backend with SQLite
- [ ] Claude API threat narration integration
- [ ] React + Electron desktop UI
- [ ] Real-time WebSocket dashboard

### v1.1.0 — Enhanced Detection
- [ ] PMKID / EAPOL handshake capture detection
- [ ] Network map visualization (canvas/D3)
- [ ] Sound alert on critical threat
- [ ] PDF threat report export
- [ ] Model auto-retraining from confirmed threats

### v1.2.0 — Multi-Platform
- [ ] macOS support (CoreWLAN adapter)
- [ ] Windows passive scan mode (limited without monitor mode)
- [ ] Mobile companion app (React Native) for alerts

### v2.0.0 — Community Intelligence
- [ ] Anonymous threat database (opt-in crowdsourced)
- [ ] Location-tagged hotspot threat map
- [ ] Plugin system for custom detection rules

---

## 🤝 Contributing

Dog Trail is open-source and contributions are welcome. Whether you're a security researcher, ML engineer, or frontend developer — there's a place for you here.

### How to Contribute

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m "feat: add your feature"`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

### Contribution Areas

| Area | Skills Needed |
|---|---|
| Packet capture engine | Python, Scapy, 802.11 protocols |
| ML model improvement | scikit-learn, anomaly detection |
| Frontend dashboard | React, Tailwind CSS, Recharts |
| Threat detection rules | Network security knowledge |
| Documentation | Technical writing |
| Testing | pytest, unit testing |

Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a PR.

---

## 🔐 Ethics & Legal

Dog Trail is designed for **defensive, passive monitoring of networks you own or have explicit permission to monitor**.

- Dog Trail does **NOT** perform any active attacks
- Dog Trail does **NOT** decrypt or capture packet payloads
- Dog Trail does **NOT** facilitate unauthorized access to any network

> Using Dog Trail to monitor networks you don't own or have permission to monitor may be illegal in your jurisdiction. The authors take no responsibility for misuse.

---

## 📄 License

Dog Trail is released under the **MIT License**.

See [LICENSE](LICENSE) for full terms.

---

## 👤 Author

**iBaadsha**
B.Tech Computer Science | Kolkata, India
Cybersecurity & AI/ML Developer

[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat-square&logo=github)](https://github.com/yourusername)

---

<div align="center">

**Built with 🐾 and a lot of packet captures.**

*If Dog Trail has ever saved your data from an evil twin — star the repo. It motivates the dog.*

⭐ **Star this repo** · 🐛 **Report a Bug** · 💡 **Request a Feature**

</div>
