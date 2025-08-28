# HTML5 Desktop Sim

A semantic, framework-free **desktop simulation** used as a learning benchmark and living lab.  
Built to practice **HTML5 semantics & accessibility** first, then layer minimal CSS/JS and **security thinking** as the project grows.

> It aligns with the spirit of the [freeCodeCamp](https://www.freecodecamp.org/) curriculum, but all code and structure here are original and focused on real-world a11y habits. The “OS” model lets me add modular apps, each exercising a concrete concept.

---

## Why this exists

- **Semantics before styling** – pages read cleanly without CSS/JS.  
- **Accessibility by default** – WCAG-oriented checks in the workflow.  
- **Security mindset early** – features double as logging/triage scenarios.  
- **Low-dependency** – no build step; static hosting works.  
- **Portfolio with proof** – each feature maps to a learning goal and a short write-up.

---

## Current Features

### System chrome (shared UI)
- **Launcher** in the header to open apps, plus a visible-on-focus **Skip to main** link for keyboard users.  
- **Task bar & Status info** in the footer with semantic widgets: `<time>`, `<data>`, `<meter>`, `<progress>`, and a polite live region for notifications.

### Boot / Index
- Entry point to the desktop; invites selection from the **Launcher**.

### Files App
- Two views: **List** (`<ol>`) and **Table** (`<caption>`, `<thead>`, `<tbody>`, `<tfoot>`).  
- **Preview** via `<picture>` with AVIF/WEBP fallbacks, `srcset`/`sizes`, descriptive `alt`, and `<figcaption>`.  
- **Metadata** via `<dl>` (Name, MIME type, Size, Modified, Path).

### Media App
- **Video** (`webm`, `mp4`) with **poster** and **captions** (`.vtt`, EN/IT).  
- **Transcript** sections using `<details>/<summary>`.  
- **Audio** (`mp3`, `ogg`) with looping demo track.

### Settings App
A page-level `<form>` with native validation and accessible grouping:
- **General** – `username` (pattern, length, title) and `language` with `<optgroup>`.  
- **Display** – theme radios (Dark/Light/System), text size and brightness sliders with live `<output>`.  
- **Sound** – volume slider with live `<output>` + `Mute` checkbox.  
- **Network** – read-only status as a compact `<dl>`.  
- **Accessibility** – toggles for High Contrast / Reduce Motion and a **Focus Visibility** choice.  
- Submit/Reset controls and a polite `role="status"` region for feedback.

---

## CSS Layer (tokens & patterns)

Global stylesheet at **`CSS/styles.css`** provides:
- **Design tokens** for type/spacing/colors and a comfortable reading width (`--measure`).  
- **Focus styles** with offset ring, plus a `forced-colors` fallback.  
- **Fieldsets as cards** (rounded, bordered, padded).  
- **Consistent rhythm** and a centered main column.  
- **Responsive grids** for Settings (two columns ≥ 48rem).  
- Header/footer layout, accessible **skip link** reveal, and small form QoL tweaks.

---

## Accessibility

- **Semantic baseline:** headings, lists, captions, data elements used correctly.  
- **Surgical ARIA only:** `aria-current`, `aria-live`, `aria-labelledby` where native semantics need help.  
- **Targets:** working toward **WCAG 2.2 AA**.  
- **Tooling:** W3C HTML Validator, IBM Equal Access Checker, Lighthouse.

---

## Security & Blue-Team Tie-Ins

- **Observable events (planned):** user actions generate structured log entries.  
- **Attack-surface demos (incremental):** form hardening, session/role checks.  
- **Playbooks:** each scenario gets triage notes (what to look for, how to respond).  
- **Future SIEM:** export logs to Elastic/Splunk for analysis.

---

## Project Structure

```text
html5-desktop-sim/
├─ index.html        # Boot / landing
├─ files.html        # Files app (list/table, preview, metadata)
├─ media.html        # Media app (video/audio, captions, transcript)
├─ settings.html     # Settings app (form: General/Display/Sound/Network/Accessibility)
├─ CSS/
│  └─ styles.css     # Tokens, focus, layout, responsive grids
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
├─ LICENSE           # MIT
└─ README.md

---

## Development Notes
- Built and tested in **VS Code** with Live Server for preview.  
- Validated with **W3C HTML Validator**, **IBM Equal Access Checker**, and **Lighthouse**.  

---

## License
This project is licensed under the [MIT License](LICENSE).  
You can copy, adapt, and use this repo for workshops or lessons with attribution. 

---

## How to Run

Some features (captions) require HTTP, not `file://`.

- **Option A (VS Code):** Right-click `index.html` → **Open with Live Server**.  
- **Option B (Python):**
  ```bash
  python -m http.server 8000

