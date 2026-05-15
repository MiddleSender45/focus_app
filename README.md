# Wispora

> **Focus, journal, goals, calendar, alarm, and AI — your daily OS.**

Wispora is a fully self-contained, offline-capable productivity app built as a single HTML file with no external dependencies beyond Google Fonts. It combines a Pomodoro-style focus timer, daily journal, goal tracker, calendar, smart alarms, and a local AI chat assistant into a single, cohesive dashboard.

---

## ✨ Features

### 🏠 Home — Daily Command Center
A three-column layout giving you a full-day view at a glance:
- **Tasks** — Create, complete, edit, and delete tasks with optional time scheduling and recurrence rules (daily, weekdays, weekends, weekly). Tasks are tied to specific calendar dates.
- **Calendar** — Month-view calendar with navigation. Days with scheduled tasks show a dot indicator. Selecting a day filters the task list.
- **Goals** — Long-term and short-term goals organized in collapsible sections. Completed goals are archived into a separate "Completed" group.

### ⏱️ Focus — Pomodoro Timer
A deeply polished focus session experience:
- **30-minute focus / 5-minute break** cycle with a circular progress ring and animated tick marks.
- **Particle canvas** — ambient animated particle field that activates and intensifies during active sessions.
- **Bit/Bug session system** — Before starting, label each session as a "Bit" (linked to a specific goal) or a "Bug" (unfocused, no goal). Bits build progress toward goals; Bugs are logged for self-awareness.
- **Session stats panel** — Tracks total sessions, total focus minutes, goals completed, Bits earned, Bugs logged, and current streak.
- **Bits by Goal ledger** — Visual progress bars showing how many Bits have been earned per goal.
- **Bug log** — A collapsible list of all unlinked (bug) sessions with timestamps.
- Audible end-of-session chime (toggleable).

### 📓 Log — Daily Journal
A structured daily journal navigable by date:
- **Thoughts** — Free-form textarea for reflections.
- **Interactions** — Log notable conversations and connections.
- **Plans** — Notes for the next day.
- **Daily ratings** — Score Productivity, Fulfillment, and Health on a 1–5 scale.
- Quick-add panel for creating new goals and tasks directly from the journal view.

### ⏰ Alarm
- Live digital clock with a dot-based seconds display.
- Create alarms with a label and repeat schedule (once, daily, weekdays, weekends).
- Alarms fire a browser notification and audible chime.
- Toggle alarms on/off or delete them from the list.

### 💬 Chat — Local AI Assistant
- Connects to a locally running **Ollama** instance (default model: `gemma3:4b`).
- Understands natural language commands to **add tasks**, **set alarms**, and **add goals** without leaving the chat.
- Sends app context (tasks, goals, journal) with each request for personalized responses.
- Supports multiple named chat sessions with full history, creation, renaming, and deletion.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Structure | HTML5 (single-file) |
| Styling | Vanilla CSS with CSS custom properties |
| Logic | Vanilla JavaScript (no frameworks) |
| Typography | DM Sans + DM Mono (Google Fonts) |
| Storage | `localStorage` (all data is local) |
| AI | [Ollama](https://ollama.com/) REST API (local) |
| PWA | Web App Manifest + Service Worker (offline support) |

---

## 🚀 Getting Started

### Option 1: Open directly
Since the app is a single HTML file, the simplest way to run it is to open `index.html` directly in any modern browser.

```
open index.html
```

> Some PWA features (service worker, manifest) require serving over HTTP/HTTPS.

### Option 2: Serve locally
Use any static file server for the full PWA experience:

```bash
# Python
python -m http.server 8080

# Node.js (npx)
npx serve .

# VS Code
# Use the "Live Server" extension
```

Then navigate to `http://localhost:8080`.

### Option 3: Install as a PWA
Once served over HTTP(S), use your browser's "Install App" or "Add to Home Screen" prompt to install Wispora as a standalone desktop/mobile app.

---

## 🤖 AI Chat Setup (Optional)

The AI Chat panel requires [Ollama](https://ollama.com/) running locally.

1. **Install Ollama**: https://ollama.com/download
2. **Pull a model**:
   ```bash
   ollama pull gemma3:4b
   ```
3. **Start Ollama** (it usually starts automatically):
   ```bash
   ollama serve
   ```
4. Open Wispora — the chat panel will show a green status dot when connected.

> The app connects to `http://localhost:11434` by default. You can switch models using the dropdown in the chat panel.

---

## 💾 Data & Privacy

All data is stored exclusively in your browser's **`localStorage`** — nothing is ever sent to a server. This includes:

- Tasks and their completion state
- Goals (long-term / short-term)
- Daily journal entries
- Alarm configurations
- Focus session statistics, Bits, Bugs, and streak data
- AI chat history

**Clearing your browser storage will erase all app data.** Consider exporting important content manually if needed.

---

## 📁 File Structure

```
focus_app/
├── index.html       # Entire app (HTML + CSS + JS)
├── manifest.json    # PWA manifest
├── sw.js            # Service worker for offline caching
├── app-icon.png     # App icon shown in the sidebar
├── icon-192.png     # PWA icon (192×192)
└── icon-512.png     # PWA icon (512×512)
```

---

## 🎨 Design System

The UI is built on a dark purple/indigo theme with a CSS custom property design system:

| Token | Description |
|---|---|
| `--bg` / `--bg2` | App background surfaces |
| `--s0`…`--s3` | Elevated surface layers |
| `--p` | Brand purple (`#9d7ff5`) |
| `--teal` | Positive/complete color (`#52c9a8`) |
| `--amber` | Warning/bug color (`#f0b660`) |
| `--red` | Danger/urgent color (`#f07070`) |
| `--t0`…`--t2` | Text hierarchy (light to muted) |
| `--ease` | Spring easing curve |

Typography uses **DM Sans** for UI text and **DM Mono** for numerical/timer displays.

---
