---
name: adk-web
description: >-
  Use this for the ADK developer web UI — the browser dev interface for the
  Agent Development Kit. Covers BOTH the easy built-in `adk web` (ships with
  `pip install google-adk`, serves on :8000) and the standalone
  github.com/google/adk-web Angular app run against an `adk api_server` backend.
  Trigger on "ADK web UI", "adk web", "adk-web", running or customizing the ADK
  dev UI, viewing agent traces/events/evals in a browser, or contributing to
  adk-web. Note the built-in `adk web` command is also documented in the `adk`
  skill.
---

# ADK Web UI

The ADK Web UI is a browser-based developer interface for testing, inspecting, and debugging ADK agents — chat, events, tracing, artifacts, evaluations, and state inspection. It is a development tool, **not intended for production deployments**.

There are two ways to run it. Pick the path that matches your goal:

- **Path A — Built-in `adk web`** (recommended for almost everyone). Ships inside the `google-adk` Python package; no Node.js or Angular needed. Use this to just run the UI against your agents.
- **Path B — Standalone adk-web from source** (`github.com/google/adk-web`). The full Angular source for the same UI. Use this only when you want to modify, fork, or contribute to the web UI itself. Requires Node.js + Angular CLI and a separately running `adk api_server` backend.

---

## Path A — Built-in dev UI (recommended)

No Angular or Node.js required. Install the package and point it at an agents directory.

Prerequisites: Python 3.10+.

```bash
# 1. Install the ADK Python package
pip install google-adk

# 2. Start the web UI, pointing at your agents directory
adk web path/to/agents_dir
```

Then open **http://localhost:8000** in your browser.

`AGENTS_DIR` is optional and defaults to the current directory.

**Common options for `adk web`:**

| Option | Purpose | Default |
|--------|---------|---------|
| `--port` | Server port | 8000 |
| `--host` | Host binding | 127.0.0.1 |
| `--session_service_uri` | Custom session storage | In-memory |
| `--artifact_service_uri` | Custom artifact storage | Local `.adk/artifacts` |
| `--reload` / `--no-reload` | Auto-reload on code changes | true |

Example with options:

```bash
adk web path/to/agents_dir --port 3000 --session_service_uri "sqlite:///sessions.db"
```

> The `adk web` command itself is also documented in the `adk` skill (the broader ADK CLI).

---

## Path B — Standalone adk-web from source (customizing / contributing)

Use this only when you need to modify or contribute to the UI. You run two processes side by side: the Angular dev server (port 4200) and the ADK API backend (port 8000).

Prerequisites:

- Node.js and npm — https://nodejs.org/en
- Angular CLI — https://angular.dev/tools/cli
- The `google-adk` Python package (provides the `adk api_server` backend)

### Step 1 — Clone and install

```bash
git clone https://github.com/google/adk-web
cd adk-web
npm install
```

### Step 2 — Start the ADK API backend (terminal 1)

```bash
adk api_server --allow_origins=http://localhost:4200 --host=0.0.0.0
```

The `--allow_origins` flag lets the Angular dev server (port 4200) call the backend API (port 8000). Both processes must run simultaneously.

> If you get `adk: command not found`, install `google-adk` or activate your virtual environment.

### Step 3 — Start the Angular dev server (terminal 2)

```bash
npm run serve --backend=http://localhost:8000
```

The UI is served at **http://localhost:4200**.

---

## What the UI gives you

- **Chat** — real-time agent messaging and session management
- **Events** — event history inspection per session
- **Tracing** — execution flow and request trace visualization
- **Artifacts** — view and manage agent-produced artifacts
- **Evaluations** — run and view evaluation metrics
- **Agent Builder / Visual Builder** — drag-and-drop workflow editing (Python only)
- **State inspection** — view and modify session state

---

## Official documentation

| URL | Description |
|-----|-------------|
| https://github.com/google/adk-web | Official standalone Angular source repo + README (setup commands) |
| https://github.com/google/adk-python | ADK Python package — ships `adk web` and `adk api_server` CLI |
| https://adk.dev/runtime/web-interface/ | Official docs: `adk web` usage, flags, features, supported runtimes |
| https://adk.dev/get-started/ | ADK getting-started hub and navigation |
| https://adk.dev/ | ADK documentation home |
| https://github.com/google/adk-samples | Official agent samples for testing with the dev UI |
