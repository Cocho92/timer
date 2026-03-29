# CLAUDE.md

## Project Overview

A minimal Pomodoro-style timer application. Single-file static HTML — no build tools, no dependencies, no frameworks.

## Repository Structure

```
timer/
└── index.html   # The entire application (HTML + CSS + JS)
```

## Architecture

Everything lives in `index.html`:
- **HTML**: Minimal markup — a display div, quick-preset buttons, and start/reset controls
- **CSS**: Inline `<style>` block, Material Design-inspired dark theme
- **JS**: Inline `<script>` block, vanilla JavaScript

## Key State Variables

| Variable | Type | Purpose |
|---|---|---|
| `interval` | `number\|null` | `setInterval` handle |
| `isRunning` | `boolean` | Current run state |
| `endTime` | `number\|null` | Absolute timestamp (ms) when timer expires |
| `remainingMs` | `number` | Milliseconds left (updated on pause, used on resume) |

## Timer Logic

- Internal precision: **milliseconds** (not seconds)
- Tick interval: **100ms** for display accuracy
- Time tracking: `Date.now()` based — `remainingMs = endTime - Date.now()` — drift-resistant
- Display uses `Math.ceil(remainingMs / 1000)` so the display shows `0:01` until the last moment

## UI Language

The UI is in **Spanish**:
- `Iniciar` — Start
- `Pausar` — Pause
- `Continuar` — Resume/Continue
- `Reiniciar` — Reset

Keep all button labels and inline comments in Spanish.

## Design / Styling

Color palette (Material Design dark):
- Background: `#202124`
- Text: `#e8eaed`
- Accent (buttons, highlight): `#8ab4f8`
- Secondary button: `#3c4043`
- Border: `#5f6368`

Font stack: `'Google Sans', Roboto, Arial, sans-serif`

Button transitions: `0.2s` on all interactive elements.

## Development Workflow

No build step needed. Open `index.html` directly in a browser.

```bash
# Quick local server if needed
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Conventions

- **No external dependencies** — keep it pure HTML/CSS/JS
- **No module system** — global scope is fine for this scale
- **Keep it in one file** — do not split into separate CSS/JS files unless explicitly asked
- **Inline comments in Spanish** for code within the file
- Default timer preset is **25 minutes** (Pomodoro standard)
- Quick presets available: 25 min, 10 min, 5 min

## Audio

Completion alert uses the Web Audio API — a short 800 Hz beep (200ms). No external audio files.

## Git Branch

Active development branch: `claude/add-claude-documentation-3hiNk`
