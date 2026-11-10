# Rook Terminal Tour — Agent Assurance, End to End

> An interactive terminal walkthrough for **Rook** — Agent Assurance

This repository contains a single self-contained HTML page that simulates the full Rook CLI workflow in an animated terminal interface. It was built for live walkthroughs and stakeholder walkthroughs where showing a real terminal isn't practical.

---

## What is Rook?

**Rook** is an agent assurance tool by TestMu AI that lets teams explore, generate scenarios for, and run automated adversarial tests against LLM-powered agents — directly from the developer's machine, with zero infrastructure.

- No model API keys to hand over
- No SDKs to wrap around your code
- Runs in CI or locally with a single install

---

## What this walkthrough shows

The flow walks through **8 sequential steps** of a real Rook workflow run against a sample insurance-claims agent (`ClaimDesk AI`). Each step pauses at every command and waits for you to press **Enter** (or click the prompt button) before showing output — so you control the pace during a live walkthrough.

| Step | What it covers |
|------|---------------|
| 1 · Install Rook | `brew` and `npm` install paths, zero-infrastructure pitch |
| 2 · Launch Rook | `rook` TUI startup, ASCII banner, available commands, `/login` |
| 3 · Explore Agent | `/project use`, `/explore .` — agent discovery and feature analysis |
| 4 · Add Profile & Test | `/profile add`, `/profile test` — connecting Rook to the live agent |
| 5 · Generate Scenarios | `/generate --total 15 --class functional,adversarial` — writing test scenarios |
| 6 · Run Scenarios | `/run --concurrency 1` — executing scenarios, live results |
| 7 · Open Web UI | `/ui --local --no-open` — launching the local read-only dashboard |
| 8 · View Report | OWASP red-team coverage table, known gaps, next steps |

---

## How to use

### Locally

```bash
git clone https://github.com/Inderjeet0007/rook-cli-tour
cd rook-cli-tour
open index.html          # macOS
# or
start index.html         # Windows
# or serve it
python3 -m http.server 8000
```

No build step, no dependencies. Everything is inline in `index.html`.

### Walkthrough controls

| Action | Effect |
|--------|--------|
| **Enter** or **Space** | Run the current command (dismisses the amber prompt) |
| **Click the ↵ button** | Same as pressing Enter |
| **Next ▶** | Jump to the next step |
| **◀ Prev** | Go back to the previous step |
| **↺ Replay** | Restart the current step from the beginning |
| **Step sidebar** | Click any step to jump directly to it |

---

## Repository structure

```
rook-cli-tour/
├── index.html      # The entire flow — HTML, CSS, and JS in one file
└── README.md       # This file
```

The walkthrough is intentionally a single file so it can be:
- Shared as an email attachment
- Dropped into any static host (GitHub Pages, Vercel, Netlify, S3)
- Opened directly from disk with no server

---

## Customising for your agent

The step content lives in the `STEPS` array near the top of the `<script>` block in `index.html`. Each step is a label and an array of line descriptors. To adapt the walkthrough for a different agent:

1. Update the agent name, project ID, and feature counts in steps 2–6
2. Replace the `/explore` and `/profile` output with your agent's actual responses
3. Swap in your OWASP coverage numbers in step 8

The rendering engine (`renderLine`) and gate system (`showEnterHint` / `triggerGate`) don't need to change.

---

## Tech

- Vanilla HTML, CSS, and JavaScript — no frameworks, no build tooling
- [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) + [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts
- Dark theme tuned to GitHub's `#0d1117` base
- Responsive: sidebar hides on mobile, terminal scrolls independently

---

## About

Rook is part of the **TestMu AI** platform. For documentation, pricing, and the web UI, visit:

- Docs: [testmuai.com/support/docs](https://www.testmuai.com/support/docs)
- Web UI guide: [testmuai.com/support/docs/rook-web-ui](https://www.testmuai.com/support/docs/rook-web-ui)
- Install: `brew install lambdatest/rook/rook` or `npm install -g @testmuai/rook`

---