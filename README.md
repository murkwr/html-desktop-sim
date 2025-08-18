# HTML5 Desktop Sim

A semantic, framework-free **desktop simulation** used as a learning benchmark and a living lab.  
Built to practice **HTML5 semantics & accessibility** first, then layer minimal CSS/JS and **security thinking** as the project grows.

> Part of my path through FreeCodeCamp’s Full Stack curriculum and a transition toward **SOC Analyst** work. The “OS” model lets me add modular apps, each exercising a concrete concept.

---

## Why this exists

- **Semantics before styling** — pages read cleanly without CSS/JS.  
- **Accessibility by default** — WCAG-oriented checks in the workflow.  
- **Security mindset early** — features double as logging/triage scenarios.  
- **Low-dependency** — no build step; static hosting works.  
- **Portfolio with proof** — each feature maps to a learning goal and write-up.

---

## Current Features

- **Boot / Index** — entry into the desktop environment; clear, navigable structure.

- **Files App**
  - Two views: **List** (`<ol>`) and **Table** (`<table>` with `<thead>`, `<tbody>`, `<tfoot>`).  
  - File preview with `<picture>` + `srcset` and a `<figcaption>`.  
  - Metadata with `<dl>` (Name, MIME type, Size, Modified, Path).  
  - Accessible nav: `aria-current`, logical heading order.

- **Media App**
  - Video (`webm`, `mp4`) with **captions** (`.vtt`).  
  - Audio (`mp3`, `ogg`).  
  - Transcripts via `<details>` / `<summary>`.  
  - Status bar with `<meter>`, `<progress>`, and live notifications (`aria-live`).

---

## Planned / In Progress

- **Settings** — semantic form patterns (`<form>`, `<fieldset>`, `<legend>`, `<label>`, native validation).  
- **Event Viewer** — synthetic “system” logs; export as JSON/NDJSON for SIEM practice.  
- **Network Panel** — visualize mock HTTP requests/responses + security headers.  
- **Security Center** — guided responses and mini incident playbooks.  
- **Terminal** — constrained command input to parse/search logs.  
- **CSS Layering** — tokens for typography, spacing, focus states, reduced motion.

---

## Accessibility

- **Semantic baseline:** headings, lists, captions, data elements used correctly.  
- **Surgical ARIA only:** `aria-current`, `aria-live`, `aria-labelledby` where native semantics need help.  
- **Targets:** aiming toward **WCAG 2.2 AA**.  
- **Tooling:** W3C HTML Validator, IBM Equal Access Checker, Lighthouse.

---

## Security & Blue-Team Tie-Ins

- **Observable events:** user actions generate structured log entries.  
- **Attack-surface demos (incremental):** form hardening, session/role checks.  
- **Playbooks:** each scenario gets triage notes (what to look for, how to respond).  
- **Future SIEM:** export logs to Elastic/Splunk for analysis.

---

## Project Structure

html5-desktop-sim/
├─ index.html       # Boot/landing
├─ files.html      # Files app (list/table, preview, metadata)
├─ media.html      # Media app (video/audio, captions, transcript)
├─ settings.html   # Settings app (scaffold)
├─ resources/
│  ├─ dove_poster.webp
│  ├─ dove_transcript_en.vtt
│  ├─ dove_transcript_it.vtt
│  ├─ dove_video.mp4
│  ├─ dove_video.webm
│  ├─ drifting.mp3
│  ├─ drifting.ogg
│  ├─ puffin-portrait.avif
│  ├─ puffin-portrait.webp
│  ├─ puffin-portrait-640.jpg
│  └─ puffin-portrait-1280.jpg
└─ README.md

---

## Development Notes
- Built and tested in **VS Code** with Live Server for preview.  
- Validated with **W3C HTML Validator**, **IBM Equal Access Checker**, and **Lighthouse**.  

---

## License
This project is licensed under the [MIT License](LICENSE).  
You are free to use, modify, and distribute with attribution.  

---

## How to Run

Some features (captions) require HTTP, not `file://`.

- **Option A (VS Code):** Right-click `index.html` → **Open with Live Server**.  
- **Option B (Python):**
  ```bash
  python -m http.server 8000

