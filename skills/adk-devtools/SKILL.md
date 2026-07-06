---
name: adk-devtools
description: >-
  Use this for the Google Agent Development Kit (ADK) for TypeScript/JavaScript — the
  `@google/adk` SDK plus the `@google/adk-devtools` CLI, invoked via `npx @google/adk-devtools`.
  Reach for it whenever building AI agents in TypeScript or JS with Google ADK: `@google/adk`,
  `npx @google/adk-devtools`, ADK web / run / create / deploy inside a Node or TS project, or
  agents that share types with a Next.js/React frontend. This is the JS/TS implementation —
  NOT the Python ADK (use the `adk` skill for that). They are parallel, non-interoperable
  implementations; do not mix them. If the project is Node/TypeScript, this is the right skill.
---

# ADK CLI (TypeScript / JavaScript)

The **Agent Development Kit (ADK) for JavaScript/TypeScript** is Google's open-source, code-first
toolkit for building, evaluating, and deploying AI agents in Node.js (and the browser). It is split
into two npm packages:

- **`@google/adk`** — the runtime SDK your agent code imports from (`LlmAgent`, `BaseAgent`, etc.). Ships ESM, CommonJS, and browser bundles.
- **`@google/adk-devtools`** — the dev-only CLI (banner: `ADK CLI`, bin name: `adk`) for scaffolding, running, serving, and deploying agents.

This skill covers CLI v1.3.0. Every command and flag below is taken from the `--help` output of
that version — none are invented.

## Install

```bash
# Runtime SDK — agent code imports from here
npm install @google/adk

# Dev-only CLI tooling
npm install -D @google/adk-devtools
```

Yarn: `yarn add @google/adk` and `yarn add -D @google/adk-devtools`.

**Prerequisites:** Node.js 24 (24.13.0+) and npm 11.8.0+, per the official TypeScript
getting-started guide (https://adk.dev/get-started/typescript); the packages declare no
`engines` constraint in their npm metadata.

### CRITICAL: invoke via `npx`, not bare `adk`

`@google/adk-devtools` registers a bin named **`adk`** — which **collides** with the binary the
**Python ADK** also installs on the system PATH. If both are present, the bare `adk` command is
ambiguous. Always invoke the JS/TS CLI explicitly:

```bash
# Preferred — no PATH collision with Python adk
npx @google/adk-devtools <command> [options]

# Or use the local bin directly
./node_modules/.bin/adk <command> [options]
```

Do **not** rely on a bare `adk` when Python ADK may also be on PATH. All examples in this skill use
`npx @google/adk-devtools`.

## When to use this vs the Python ADK

Pick a lane: an agent is written in **either** Python **or** TypeScript, never both. Use this JS/TS
ADK (`@google/adk`, github.com/google/adk-js) when your agent lives in a Node.js backend, a Next.js
or React app, or the browser — especially when you want to share types between the agent and a TS
frontend. Use the **Python ADK** (`google-adk`, the `adk` skill) for Python backends. The two are
parallel, independent implementations of the same concept and are **not interoperable** at the
agent level — they only share branding, docs (adk.dev), and the `adk-samples` repo.

## Commands

Top-level commands: `web`, `api_server`, `create`, `run`, `deploy`, `integration`.
Global options: `-v, --version` (CLI version), `-h, --help`.

### create — scaffold a new agent

Creates a new agent project.

```bash
npx @google/adk-devtools create [options] [agent]
```

- `agent` — name to give the new agent (default: `adk_agent`).
- `-y, --yes` — skip confirmation prompts (non-interactive).
- `--model <string>` — model used for the root agent.
- `--api_key <string>` — API key to access the model (e.g. Google AI API key).
- `--project <string>` — Google Cloud project (for using Vertex AI as backend).
- `--region <string>` — Google Cloud region (for using Vertex AI as backend).
- `--language <string>` — `ts` or `js` as the output language.

Example:

```bash
npx @google/adk-devtools create my_agent --language ts --model gemini-flash-latest --yes
```

### run — run an agent in the terminal (REPL)

Runs an agent file interactively.

```bash
npx @google/adk-devtools run [options] <agent>
```

- `<agent>` — agent file path (`.js` or `.ts`).
- `--save_session [boolean]` — save the session to a JSON file on exit (default: `false`).
- `--session_id <string>` — session ID to save to on exit when `--save_session` is set (prompted if unset).
- `--replay <string>` — JSON file with initial session state + user queries; runs them against a fresh session non-interactively (no further interaction).
- `--resume <string>` — JSON file with a previously saved session (from `--save_session`); re-displays it and lets you continue interacting.
- `-v, --verbose [boolean]` — verbose level (default: `false`).
- `--log_level <string>` — log level (default: `info`).
- `--session_service_uri <string>` — session service URI; supports `memory://` for in-memory.
- `--artifact_service_uri <string>` — artifact service URI; supports `gs://<bucket name>` for GCS.
- `--otel_to_cloud [boolean]` — send OTel traces to cloud (default: `false`).
- `--compile [boolean]` — compile TS agent file to JS before execution (default: `true`).
- `--bundle [boolean]` — bundle the agent before execution (default: `true`).
- `--file_type <string>` — `cjs` or `esm`.
- `--reload_agents [boolean]` — watch agent files for changes and automatically reload them (default: `false`; changes take effect on the next agent run).

Example:

```bash
npx @google/adk-devtools run my_agent/agent.ts --save_session
```

### web — start the development Web UI server

Starts the ADK web server (UI + API).

```bash
npx @google/adk-devtools web [options] [agents_dir]
```

- `agents_dir` — agent file or directory of agents to serve (defaults to the current directory). For a directory, the layout is `agents_dir/{agentName}.js` or `agents_dir/{agentName}/agent.js`; each file must `export` the `rootAgent` as an instance of `BaseAgent` (e.g. `LlmAgent`).
- `-h, --host <string>` — binding host (default: `localhost`).
- `-p, --port <number>` — server port (default: `8000`).
- `--allow_origins <string>` — allowed origins (default: empty).
- `-v, --verbose [boolean]` — verbose level (default: `false`).
- `--log_level <string>` — log level (default: `info`).
- `--session_service_uri <string>` — session service URI; supports `memory://`.
- `--artifact_service_uri <string>` — artifact service URI; supports `gs://<bucket name>`.
- `--otel_to_cloud [boolean]` — send OTel traces to cloud (default: `false`).
- `--compile [boolean]` — compile TS to JS before execution (default: `true`).
- `--bundle [boolean]` — bundle before execution (default: `true`).
- `--file_type <string>` — `cjs` or `esm`.
- `--a2a [boolean]` — enable A2A (Agent-to-Agent) for the web/api server (default: `false`).
- `--reload_agents [boolean]` — watch agent files for changes and automatically reload them (default: `false`; changes take effect on the next agent run).

Example:

```bash
npx @google/adk-devtools web ./agents --port 3000 --verbose
```

### api_server — start a headless API server (no UI)

Starts the ADK API server. Same options as `web`, just without the UI bundle.

```bash
npx @google/adk-devtools api_server [options] [agents_dir]
```

Options are identical to `web`: `-h, --host`, `-p, --port` (default `8000`), `--allow_origins`,
`-v, --verbose`, `--log_level`, `--session_service_uri`, `--artifact_service_uri`,
`--otel_to_cloud`, `--compile`, `--bundle`, `--file_type`, `--a2a`, `--reload_agents`.

Example:

```bash
npx @google/adk-devtools api_server ./agents --session_service_uri memory:// --artifact_service_uri gs://my-bucket
```

### deploy cloud_run — deploy to Google Cloud Run

`deploy` has three subcommands: `cloud_run`, `agent_engine`, and `reasoning_engine` (the latter
two take identical options — Agent Engine's underlying resource type is "Reasoning Engine").

```bash
npx @google/adk-devtools deploy cloud_run [options] [agents_dir]
```

- `agents_dir` — agent file or directory to serve (same layout/`rootAgent` requirement as `web`).
- `-p, --port <number>` — server port (default: `8000`).
- `--project [string]` — Google Cloud project to deploy to; defaults to `gcloud` config project.
- `--region [string]` — Google Cloud region; defaults to `gcloud` `run/region` config.
- `--service_name [string]` — Cloud Run service name (default: `adk-default-service-name`).
- `--temp_folder [string]` — temp folder for generated Cloud Run source files (default: a timestamped folder in the system temp dir).
- `--adk_version [string]` — ADK version to use in the Cloud Run service (default: `latest`).
- `--with_ui [boolean]` — deploy the ADK Web UI too (default: API server only).
- `--allow_origins <string>` — allowed origins (default: empty).
- `-v, --verbose [boolean]` — verbose level (default: `false`).
- `--log_level <string>` — log level (default: `info`).
- `--session_service_uri <string>` — session service URI; supports `memory://`.
- `--artifact_service_uri <string>` — artifact service URI; supports `gs://<bucket name>`.
- `--compile [boolean]` — compile TS to JS before execution (default: `true`).
- `--bundle [boolean]` — bundle before execution (default: `true`).
- `--file_type <string>` — `cjs` or `esm`.
- `--a2a [boolean]` — enable A2A (default: `false`).

Example:

```bash
npx @google/adk-devtools deploy cloud_run ./agents --service_name my-adk-service --with_ui --project my-gcp-project --region us-central1
```

### deploy agent_engine — deploy to Vertex AI Agent Engine

```bash
npx @google/adk-devtools deploy agent_engine [options] [agents_dir]
```

- `agents_dir` — agent file or directory to serve (same layout/`rootAgent` requirement as `web`).
- `--project [string]` — Google Cloud project to deploy to; defaults to `gcloud` config project.
- `--region [string]` — Google Cloud region; defaults to `gcloud` `run/region` config.
- `--display_name [string]` — display name for the Reasoning Engine (default: agent directory name).
- `--description [string]` — description for the Reasoning Engine.
- `--repository [string]` — Artifact Registry repository name to push docker images; required for agent_engine deploy.
- `--temp_folder [string]` — temp folder for generated source files (default: a timestamped folder in the system temp dir).
- `--adk_version [string]` — ADK version to use (default: `latest`).
- `--with_ui [boolean]` — deploy the ADK Web UI too (default: API server only).
- Plus the same server/build flags as `cloud_run`: `--allow_origins`, `-v, --verbose`, `--log_level`,
  `--session_service_uri`, `--artifact_service_uri`, `--compile`, `--bundle`, `--file_type`, `--a2a`.
  Note: no `-p, --port` flag here (unlike `cloud_run`).

`deploy reasoning_engine` accepts exactly the same options.

Example:

```bash
npx @google/adk-devtools deploy agent_engine ./agents --project my-gcp-project --region us-central1 --repository my-ar-repo --display_name my-agent
```

### integration — run integration and conformance tests

Runs ADK integration and conformance tests. Has one subcommand, `conformance` (run ADK conformance
tests), plus `help [command]`.

```bash
npx @google/adk-devtools integration conformance [options]
```

- `-v, --verbose [boolean]` — verbose level (default: `false`).
- `--log_level <string>` — log level (default: `info`).
- `--agents_dir [dir]` — directory of conformance test agent definitions; recursively searched for `.yaml` files (default: current directory).
- `--tests_dir [dir]` — directory of conformance test definitions; recursively searched for `.yaml` files (default: current directory).
- `--force` — force run skipped tests.

## Common workflows

### 1. Install the SDK and CLI

```bash
npm install @google/adk
npm install -D @google/adk-devtools
```

### 2. Scaffold a new TypeScript agent

```bash
# Interactive — prompts for model, API key, etc.
npx @google/adk-devtools create my_agent

# Non-interactive with explicit options
npx @google/adk-devtools create my_agent \
  --language ts \
  --model gemini-flash-latest \
  --api_key "$GEMINI_API_KEY" \
  --yes
```

### 3. Run the agent in the terminal and save the session

```bash
npx @google/adk-devtools run my_agent/agent.ts --save_session
# Later, resume it:
npx @google/adk-devtools run my_agent/agent.ts --resume session.json
```

### 4. Launch the development Web UI

```bash
# Serves on http://localhost:8000 by default
npx @google/adk-devtools web ./agents

# Custom port + A2A enabled
npx @google/adk-devtools web ./agents --port 3000 --a2a
```

### 5. Deploy to Cloud Run with the Web UI

```bash
npx @google/adk-devtools deploy cloud_run ./agents \
  --service_name my-adk-service \
  --with_ui \
  --project my-gcp-project \
  --region us-central1 \
  --adk_version 1.3.0
```

## Official documentation

- https://github.com/google/adk-js — official source repo; README is the authoritative install/version reference.
- https://github.com/google/adk-js#readme — homepage for both packages.
- https://www.npmjs.com/package/@google/adk — npm page for the runtime SDK.
- https://www.npmjs.com/package/@google/adk-devtools — npm page for the dev tools CLI.
- https://adk.dev/get-started/typescript — official TypeScript getting-started guide (google.github.io/adk-docs redirects here).
- https://github.com/google/adk-samples — official samples repo; TS agents live under `typescript/agents/`.
