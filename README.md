# 🫧 Bubble — Focus Study Tool

> *Create your personal focus space. Only what you need. Nothing more.*

[![GitHub Pages](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-4DF0C5?style=flat-square&logo=github)](https://yourusername.github.io/bubble)
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)
[![No dependencies](https://img.shields.io/badge/Dependencies-None-green?style=flat-square)]()
[![Pure HTML/CSS/JS](https://img.shields.io/badge/Stack-HTML%20%2F%20CSS%20%2F%20JS-orange?style=flat-square)]()

---

## What is Bubble?

Bubble is a browser-based focus environment designed to eliminate digital distractions during study sessions. It creates a **protected workspace** — a "bubble" — where only the resources you explicitly select are accessible. Everything else disappears.

The core insight behind Bubble is simple: the problem with studying in the digital age is not a lack of willpower, but a surplus of friction-free distractions. Bubble inverts the equation — it makes staying focused the **path of least resistance**.

---

## Features

### 🎯 Guided Session Setup
A four-step onboarding flow that helps you define your session before it begins:
- **Session naming** — give your study block a name that appears in the final report
- **Document selection** — load local files (PDF, images, text) directly into the bubble
- **Site whitelisting** — choose from curated presets or add custom URLs
- **Timer selection** — Pomodoro (25 min), deep focus (45 min), long session (90 min), or unlimited

### 📄 Integrated Document Viewer
PDF files, images, and text documents are rendered directly inside Bubble using the [PDF.js](https://mozilla.github.io/pdf.js/) library — no external apps, no context switching.

### 🌐 Whitelisted Site Access
Select exactly which websites you need. Sites open in a new tab with the bubble session still active. Presets include: ChatGPT, Claude, YouTube, Wikipedia, Google Scholar, Notion, Wolfram Alpha, DeepL, GitHub, Google Drive, Quizlet, Anki Web.

### ⏱ Session Timer
A live countdown (or elapsed time) displayed in the top bar throughout the session. Visual alert when time is running low.

### 🛡 Fullscreen Protection
Bubble launches in fullscreen mode, hiding the OS taskbar, browser tabs, and all desktop elements. If the user accidentally exits fullscreen (e.g. by pressing Esc), a **re-engagement overlay** appears with a 5-second countdown and automatically returns to fullscreen — unless the user consciously chooses to exit.

### 📊 Session Report
After every session, Bubble generates a detailed report including:
- Total study duration
- Session name and date
- All documents and sites used
- A visual resource distribution chart
- An inspirational quote
- Export to `.txt` file

---

## Getting Started

### Option 1 — Run locally (zero setup)

```bash
git clone https://github.com/yourusername/bubble.git
cd bubble
```

Then simply open `index.html` in your browser. No build step, no dependencies, no server required.

> **Recommended:** Use Google Chrome or Microsoft Edge for the best fullscreen API support and PDF rendering.

### Option 2 — Deploy to GitHub Pages (free hosting)

1. Fork this repository
2. Go to **Settings → Pages**
3. Under *Source*, select `main` branch and `/` (root) folder
4. Click **Save** — your site will be live at `https://yourusername.github.io/bubble`

---

## Usage

1. Open Bubble in your browser
2. Click **"Create your bubble"** — the app enters fullscreen automatically
3. Follow the 4-step setup:
   - Name your session
   - Add local study files
   - Select the websites you need
   - Choose a study duration
4. Press **"✦ Create Bubble"** — the transition animation plays
5. Study using the sidebar to navigate between documents and sites
6. Press **"Exit Bubble"** when done — your session report is generated

---

## Technical Architecture

Bubble is a **single-file web application** — the entire product lives in `index.html`. This is a deliberate design choice: it makes the tool trivially simple to host, share, fork, and audit.

```
bubble/
├── index.html        ← The entire application (HTML + CSS + JS)
└── README.md         ← This file
```

### Technology Stack

| Layer | Technology | Why |
|---|---|---|
| UI | Vanilla HTML5 / CSS3 | Zero build step, maximum portability |
| Logic | Vanilla JavaScript (ES6+) | No framework overhead |
| Animations | CSS Keyframes + Canvas API | Smooth, GPU-accelerated |
| PDF Rendering | PDF.js (CDN) | Industry-standard, Mozilla-maintained |
| Fonts | Google Fonts (Syne + DM Sans) | Distinctive, readable |
| Hosting | GitHub Pages | Free, reliable, no backend |

### How Fullscreen Protection Works

Bubble uses the [Fullscreen API](https://developer.mozilla.org/en-US/docs/Web/API/Fullscreen_API) to occupy the entire screen at session start. The `fullscreenchange` event is monitored throughout the session. If fullscreen is exited unexpectedly, the re-engagement overlay fires immediately and re-requests fullscreen after 5 seconds — unless the user explicitly chooses to exit. This creates meaningful **psychological friction** against impulsive session abandonment without requiring any system-level permissions.

### Privacy & Security

- **Zero data transmission.** All data (files, session info, site selections) remains in the browser's memory. Nothing is sent to any server.
- **No accounts, no login.** Bubble requires no authentication of any kind.
- **No tracking, no analytics.** There is no telemetry of any kind embedded in the application.
- **Local file access.** Files are read via the browser's `File` API. They are never uploaded anywhere.
- **Open source.** The entire codebase is visible and auditable in a single file.

---

## Browser Compatibility

| Browser | Fullscreen | PDF Viewer | Recommended |
|---|---|---|---|
| Google Chrome 90+ | ✅ | ✅ | ⭐ Best |
| Microsoft Edge 90+ | ✅ | ✅ | ⭐ Best |
| Firefox 90+ | ✅ | ✅ | ✅ Good |
| Safari 15+ | ⚠️ Limited | ✅ | ⚠️ Limited |

> Safari has restricted Fullscreen API behavior. The re-engagement overlay still works, but fullscreen re-entry may require user interaction.

---

## Known Limitations

Bubble is designed to be a **lightweight, frictionless focus tool** — not a system-level content blocker. The following limitations are inherent to browser-based applications:

| Limitation | Context |
|---|---|
| **Esc key exits fullscreen** | This is a browser-level security constraint that cannot be overridden by any webpage. Bubble mitigates this with the 5-second re-engagement overlay. |
| **Cannot block desktop apps** | Bubble does not prevent access to games, local applications, or OS-level notifications. It operates within the browser only. |
| **Sites open in new tabs** | Due to browser security policies (CORS, X-Frame-Options), most modern websites block embedding via `<iframe>`. Whitelisted sites open in a new tab instead. |
| **No content filtering on sites** | Bubble cannot restrict what you do within a whitelisted site (e.g. it cannot limit YouTube to educational content only). |

---

## Roadmap

### v1.1 — Chrome Extension
A companion browser extension that enforces the site whitelist at the network level — intercepting all navigation attempts and blocking any URL not in the active bubble. This would make the protection significantly more robust without requiring any external service.

### v1.2 — Session History
Persist session reports locally using `localStorage`, allowing users to review their study history over time.

### v1.3 — Custom Presets
Save and name collections of sites and file types as reusable "study profiles" (e.g. *"Maths Exam Mode"*, *"Thesis Writing Mode"*).

### v2.0 — Mobile (iOS / Android)
A native mobile application that can restrict app access at the OS level using platform-specific focus APIs (iOS Screen Time, Android Digital Wellbeing). This is architecturally distinct from the web version and will be developed as a separate project.

---

## Contributing

Contributions are welcome. Please open an issue before submitting a PR to discuss the proposed change.

```bash
git clone https://github.com/yourusername/bubble.git
# Make your changes to index.html
# Open index.html in browser to test
# Submit a PR
```

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">
  <br>
  <strong>Built for students, by a student.</strong><br>
  <em>Stay in the bubble. 🫧</em>
</div>
