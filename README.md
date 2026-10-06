# Rootine
> **An AI-Driven Desktop Productivity & Telemetry Tracking System**

 **Project Status:** *In Active Development (Planning & Setup Phase — CS 499 Capstone)*

**Author:** Rehmat Kataria  
**Degree:** BA in Computer Science and Economics  
**Course:** CS 499 Capstone (2026–2027)  
**Faculty Advisor:** Dr. Cao  

---

## Overview

**Rootine** is an upcoming local-first desktop application designed to bridge the intention-action gap in personal productivity. Traditional productivity apps rely on friction-heavy manual task logging, leading to tracking fatigue and abandoned habits. 

Rootine creates an automated, closed-loop accountability engine by combining:
1. **AI Goal Decomposition:** Converting broad ambitions into daily 15–30 minute micro-tasks.
2. **Calendar Integration:** Syncing micro-tasks directly with Google Calendar via OAuth 2.0.
3. **Passive Telemetry:** Monitoring active OS process titles and browser tabs locally to verify execution without manual input.
4. **Gamification & Rewards:** Translating verified completed tasks into a living 2D virtual garden that unlocks user-configured leisure rewards.

---

## Planned Tech Stack

* **Desktop Framework:** Tauri (Rust + React / TypeScript)
* **Local Database:** SQLite (`tauri-plugin-sql`)
* **Styling & UI:** Tailwind CSS, Lucide Icons
* **Browser Extension:** JavaScript (Manifest V3)
* **AI Engine:** Google Gemini API (Free Tier)
* **External Integrations:** Google Calendar API, GitHub REST API

---

## Planned Architecture
```
┌────────────────────────────────────────────────────────────────────────┐
│                          Rootine Desktop App                           │
│                                                                        │
│  ┌───────────────────────────┐            ┌─────────────────────────┐  │
│  │   React / TypeScript UI   │───────────>│   Embedded SQLite DB    │  │
│  │   (Garden UI, Dashboard)  │            │   (Goals, Logs, State)  │  │
│  └─────────────┬─────────────┘            └────────────▲────────────┘  │
│                │                                       │               │
│                │ IPC                                   │ SQL           │
│                ▼                                       │               │
│  ┌─────────────────────────────────────────────────────┴────────────┐  │
│  │                         Rust Native Core                         │  │
│  │  • Active Window Listener (OS Process Polling)                   │  │
│  │  • Local HTTP Telemetry Server (127.0.0.1)                       │  │
│  └──────────────────────────────────────────────────────────────────┘  │
└───────────────▲────────────────────────────────────────┬───────────────┘
                │                                        │
                │ Local HTTP                             │ External REST
                │                                        ▼
┌───────────────┴──────────────┐            ┌────────────────────────────┐
│ Manifest V3 Browser Ext.     │            │ External REST APIs         │
│ (Active Domain Listener)     │            │ • Gemini API               │
└──────────────────────────────┘            │ • Google Calendar API      │
                                            └────────────────────────────┘
```

---

## 6-Month Development Roadmap

- [ ] **Month 1:** Project setup, Tauri + React scaffolding, local SQLite database schemas.
- [ ] **Month 2:** Gemini API integration for goal decomposition & Google Calendar OAuth sync.
- [ ] **Month 3:** Native Rust active window process listener & Manifest V3 browser extension.
- [ ] **Month 4:** Task verification matching engine & virtual garden growth state mechanics.
- [ ] **Month 5:** Analytics progress dashboard, custom Reward Store, and usability testing.
- [ ] **Month 6:** Bug fixing, performance optimization, and final capstone presentation.

---

## Local Development Setup (Upcoming)

*Instructions will be updated as core repository modules are committed.*

```bash
# Clone repository
git clone [https://github.com/your-username/rootine.git](https://github.com/your-username/rootine.git)
cd rootine

# Install dependencies
npm install

# Run application in dev mode
npm run tauri dev
