---
name: adk
description: >-
  Use for the Google Agent Development Kit (Python) CLI — the `adk` command from
  `pip install google-adk` — for building, running, evaluating, and deploying AI
  agents in Python. STRONGLY prefer this skill whenever the user mentions "ADK",
  "Agent Development Kit", or any `adk` subcommand (`adk create`, `adk run`,
  `adk web`, `adk eval`, `adk deploy`), scaffolds or runs a Google ADK Python
  agent, launches the ADK dev web UI, or deploys an agent to Vertex AI Agent
  Engine, Cloud Run, or GKE. This is the PYTHON ADK; for the TypeScript ADK CLI
  (`adk-devtools`) use that skill instead.
---

# ADK CLI (Python)

The **Agent Development Kit (ADK)** is Google's open-source, code-first Python framework for building, evaluating, and deploying AI agents — supporting multi-agent workflows, tool use, evaluation, and deployment to Cloud Run, GKE, or Vertex AI Agent Engine. The `adk` CLI scaffolds new agents (`create`), runs them locally in the terminal (`run`) or a browser dev UI (`web`) or a headless API server (`api_server`), evaluates them (`eval`, `eval_set`), optimizes prompts (`optimize`), runs conformance/pytest checks (`conformance`, `test`), migrates session databases (`migrate`), and deploys to hosted environments (`deploy`). This skill documents `adk` v2.1.0.

## Install

```bash
pip install google-adk          # installed CLI entry-point: `adk`
```

Requires **Python 3.11+** (the user runs 3.13, fully supported). Optional extras exist (e.g. `"google-adk[extensions]"`, `"google-adk[all]"`, plus `a2a`, `db`, `eval`, `gcp`, `mcp`, `tools`, …); the fuller version/extras matrix is in the repo README and PyPI page.

## Authentication

ADK picks its backend from env vars (typically in a `.env` file in the agent folder, or the shell):

**Option A — Google AI / Gemini API key (simplest, local dev + Agent Engine Express Mode):**
```bash
export GOOGLE_API_KEY="AIza..."        # key from aistudio.google.com
# leave GOOGLE_GENAI_USE_VERTEXAI absent or false
```
`adk run`, `adk web`, and `adk api_server` pick this up automatically. `adk deploy agent_engine --api_key=<key>` uses Express Mode (no GCP project needed).

**Option B — Vertex AI (GCP project; required for Cloud Run, GKE, and non-Express Agent Engine):**
```bash
gcloud auth application-default login          # sets up ADC
export GOOGLE_CLOUD_PROJECT="my-project"
export GOOGLE_CLOUD_LOCATION="us-central1"
export GOOGLE_GENAI_USE_VERTEXAI=true          # force the Vertex backend
```
`adk deploy cloud_run` / `adk deploy gke` always need `--project` + `--region` (or gcloud config defaults) plus ADC.

---

## Commands

Top-level: `api_server`, `conformance`, `create`, `deploy`, `eval`, `eval_set`, `migrate`, `optimize`, `run`, `test`, `web`. Global: `adk --version`, `adk --help`.

A recurring set of service-URI flags appears on `run`, `web`, `api_server`, and the `deploy` subcommands:
- `--session_service_uri` — `agentengine://<id|resource-name>`, `memory://`, `sqlite://<path>`, or any SQLAlchemy DB URL.
- `--artifact_service_uri` — `gs://<bucket>`, `memory://`, or `file://<path>`.
- `--memory_service_uri` — `rag://<rag_corpus_id>`, `agentengine://<id>`, or `memory://`.
- `--use_local_storage / --no_use_local_storage` — use local `.adk` storage when the URIs above are unset (cannot be combined with explicit URIs).

### create — scaffold a new agent app

One-line: creates a new app folder in the current directory from an agent template.

```
adk create [OPTIONS] APP_NAME
```
Options: `--model TEXT` (root-agent model), `--api_key TEXT` (Google AI API key), `--project TEXT` / `--region TEXT` (use Vertex AI as backend).

```bash
adk create my_agent --model=gemini-2.5-flash --api_key=$GOOGLE_API_KEY
```

### run — run an agent in the terminal

One-line: runs an agent interactively, or for a single `QUERY` then exits.

```
adk run [OPTIONS] AGENT [QUERY]
```
Key options:
- `--default_llm_model TEXT` — default model when the agent doesn't set one explicitly.
- `--in_memory` — do not persist session data.
- `--save_session` / `--session_id TEXT` — save the session to a JSON file on exit (prompts for an ID if unset).
- `--replay FILE` — run user queries from a JSON file against a fresh session (no further interaction).
- `--resume FILE` — re-display a previously saved session and continue interacting.
- `--state TEXT` — initial state as a JSON string.
- `--timeout TEXT` — per-turn timeout (e.g. `30s`, `5m`).
- `--jsonl` — emit structured JSONL instead of human-readable text.
- `--enable_features` / `--disable_features TEXT` — comma-separated experimental feature toggles.
- Plus the service-URI flags listed above.

```bash
adk run my_agent                                   # interactive
adk run my_agent "What is the weather today?"      # single turn
adk run my_agent --default_llm_model=gemini-2.5-pro --in_memory
adk run my_agent --replay session_state.json
adk run my_agent --save_session --session_id=sess001
```

### web — browser dev UI

One-line: starts a FastAPI server with the browser-based ADK Dev UI for agents.

```
adk web [OPTIONS] [AGENTS_DIR]
```
`AGENTS_DIR` is a directory whose subfolders are each an agent (`agent.py` or `root_agent.yaml`), or a path directly to a single agent folder. Key options:
- `--host TEXT` (default `127.0.0.1`), `--port INTEGER`.
- `-v, --verbose` (DEBUG logging) / `--log_level [debug|info|warning|error|critical]`.
- `--reload / --no-reload` (auto-reload server), `--reload_agents` (live reload on agent file changes).
- `--a2a` — enable the Agent-to-Agent endpoint.
- `--allow_origins TEXT` — CORS origins (literal or `regex:` prefixed).
- `--default_llm_model TEXT`, `--eval_storage_uri TEXT` (`gs://...`), `--extra_plugins TEXT`.
- `--trace_to_cloud` / `--otel_to_cloud` — telemetry to Google Cloud.
- `--logo-text TEXT` / `--logo-image-url TEXT` — customize the UI logo.
- `--url_prefix TEXT` (mount behind a reverse proxy), `--trigger_sources TEXT` (`pubsub,eventarc`).
- Plus the service-URI flags listed above.

```bash
adk web path/to/agents_dir
adk web my_agent --port=8080 -v
adk web my_agent --session_service_uri=sqlite:///sessions.db
adk web my_agent --reload_agents
```

### api_server — headless FastAPI server (no UI)

One-line: starts a FastAPI server for agents without the Web UI.

```
adk api_server [OPTIONS] [AGENTS_DIR]
```
Same flag family as `web` (`--host`, `--port`, `-v`/`--log_level`, `--reload`, `--a2a`, `--reload_agents`, `--allow_origins`, `--eval_storage_uri`, `--extra_plugins`, `--trace_to_cloud`, `--otel_to_cloud`, `--url_prefix`, `--trigger_sources`, `--enable_features`/`--disable_features`, and the service-URI flags). Additional:
- `--auto_create_session` — auto-create a session if missing when calling `/run`.
- `--with_ui` — also serve the ADK Web UI.

```bash
adk api_server path/to/agents_dir --port=8000
adk api_server my_agent --a2a --port=8000
adk api_server my_agent --artifact_service_uri=gs://my-bucket --otel_to_cloud
```

### eval — evaluate an agent against eval sets

One-line: evaluates an agent given one or more eval sets.

```
adk eval [OPTIONS] AGENT_MODULE_FILE_PATH [EVAL_SET_FILE_PATH_OR_ID]...
```
`AGENT_MODULE_FILE_PATH` is the `__init__.py` that exposes the `agent` module (containing `root_agent`). Append `:case1,case2` to an eval-set file/ID to run only specific cases. Options: `--config_file_path TEXT`, `--print_detailed_results`, `--eval_storage_uri TEXT` (`gs://...`), `--log_level [...]`, `--enable_features`/`--disable_features TEXT`.

```bash
adk eval my_agent/__init__.py my_agent/eval_sets/basic.json
adk eval my_agent/__init__.py my_agent/eval_sets/basic.json:case1,case2
adk eval my_agent/__init__.py my_agent/eval_sets/basic.json \
    --print_detailed_results --eval_storage_uri=gs://my-bucket
```

### eval_set — manage eval sets

One-line: create and populate eval sets. Subcommands: `create`, `add_eval_case`, `generate_eval_cases`.

```
adk eval_set create AGENT_MODULE_FILE_PATH EVAL_SET_ID
adk eval_set add_eval_case AGENT_MODULE_FILE_PATH EVAL_SET_ID
adk eval_set generate_eval_cases AGENT_MODULE_FILE_PATH EVAL_SET_ID
```
- `create` — make an empty eval set. Options: `--eval_storage_uri`, `--log_level`.
- `add_eval_case` — add a case from a conversation-scenarios file. Required: `--scenarios_file FILE`, `--session_input_file FILE`. Plus `--eval_storage_uri`, `--log_level`.
- `generate_eval_cases` — dynamically generate cases via the Vertex AI Eval SDK (auto-creates the eval set if absent). Required: `--user_simulation_config_file FILE`. Plus `--eval_storage_uri`, `--log_level`.

```bash
adk eval_set create my_agent/__init__.py my_eval_set
adk eval_set add_eval_case my_agent/__init__.py my_eval_set \
    --scenarios_file=scenarios.json --session_input_file=session.json
adk eval_set generate_eval_cases my_agent/__init__.py my_eval_set \
    --user_simulation_config_file=sim_config.json
```

### optimize — optimize root-agent instructions (GEPA)

One-line: optimizes the root agent's instructions using the GEPA optimizer.

```
adk optimize [OPTIONS] AGENT_MODULE_FILE_PATH
```
Required: `--sampler_config_file_path FILE` (LocalEvalSampler config with the train/validation eval sets). Optional: `--optimizer_config_file_path FILE` (GEPA config; defaults used if omitted), `--print_detailed_results`, `--log_level [...]` (default `INFO`).

```bash
adk optimize my_agent/__init__.py \
    --sampler_config_file_path=sampler.json \
    --print_detailed_results
```

### test — run agent test JSON files via pytest

One-line: runs pytest on agent test JSON files under a folder.

```
adk test [OPTIONS] [FOLDER]
```
`FOLDER` defaults to the current directory. Option: `--rebuild` (rebuild test files by re-running the real agent with the user messages).

```bash
adk test path/to/agents
adk test path/to/agents --rebuild
```

### conformance — conformance testing tools

One-line: record and replay agent interactions to verify behavior consistency. Subcommands: `record`, `test`.

```
adk conformance record [PATHS]... {none|sse|bidi}
adk conformance test [OPTIONS] [PATHS]...
```
- `record` — generate conformance `test.yaml` files from `input.yaml` specs (`category/name/input.yaml` → `category/name/test.yaml`); defaults to `tests/`. The trailing arg selects streaming mode (`none|sse|bidi`).
- `test` — verify agents against recordings. Options: `--mode [replay|live]` (default `replay`; `live` not yet implemented), `--generate_report`, `--report_dir DIRECTORY`, `--streaming-mode [none|sse|bidi]`. Defaults to the `tests` folder if no `PATHS` given.

```bash
adk conformance record tests/core tests/tools none
adk conformance test tests/core --generate_report --report_dir=reports
```

### migrate — migration utilities

One-line: ADK migration commands. Subcommand: `session`.

```
adk migrate session --source_db_url <url> --dest_db_url <url>
```
Migrates a session database to the latest schema version. Required: `--source_db_url TEXT` and `--dest_db_url TEXT` (SQLAlchemy URLs, e.g. `sqlite:///source.db`). Optional: `--log_level [...]`.

```bash
adk migrate session \
    --source_db_url=sqlite:///old.db \
    --dest_db_url=sqlite:///new.db
```

### deploy — deploy to hosted environments

One-line: deploys an agent. Subcommands: `agent_engine`, `cloud_run`, `gke`.

#### deploy agent_engine — Vertex AI Agent Engine

```
adk deploy agent_engine [OPTIONS] AGENT
```
Key options:
- `--api_key TEXT` — Express Mode key (used only if `GOOGLE_GENAI_USE_VERTEXAI` is true; overrides `GOOGLE_API_KEY`).
- `--project TEXT` / `--region TEXT` — Vertex Mode target (ignored if `--api_key` is set).
- `--agent_engine_id TEXT` — update an existing instance instead of creating one (resource ID with project/region; full resource name with `--api_key`).
- `--display_name TEXT`, `--description TEXT`.
- `--adk_app TEXT` (Python file defining the app; default `agent_engine_app.py`), `--adk_app_object TEXT` (`root_agent` or `app`; default `root_agent`).
- `--env_file TEXT`, `--requirements_file TEXT`, `--agent_engine_config_file TEXT`, `--temp_folder TEXT`.
- `--trace_to_cloud / --no-trace_to_cloud`, `--otel_to_cloud`.
- `--validate-agent-import / --no-validate-agent-import` (or `--skip-agent-import-validation`, the default).
- (`--staging_bucket` and `--absolutize_imports` are deprecated.)

```bash
# Express Mode (API key, no GCP project)
adk deploy agent_engine --api_key=$GOOGLE_API_KEY my_agent

# Vertex Mode (ADC, project + region)
adk deploy agent_engine --project=my-project --region=us-central1 \
    --display_name="My Agent" my_agent

# Update an existing instance
adk deploy agent_engine --project=my-project --region=us-central1 \
    --agent_engine_id=123456789 my_agent
```

#### deploy cloud_run — Cloud Run

```
adk deploy cloud_run [OPTIONS] AGENT
```
Use `--` to separate gcloud args from adk args. Key options:
- `--project TEXT` (required; falls back to gcloud config), `--region TEXT` (required; otherwise `gcloud run deploy` prompts).
- `--service_name TEXT` (default `adk-default-service-name`), `--app_name TEXT`, `--port INTEGER` (default `8000`).
- `--with_ui` — also deploy the Web UI (dev/test only — not for production).
- `--a2a`, `--allow_origins TEXT`, `--trigger_sources TEXT`, `--adk_version TEXT` (default `2.1.0`), `--temp_folder TEXT`, `--log_level [...]`.
- `--trace_to_cloud`, `--otel_to_cloud`.
- Plus the service-URI flags (here `--use_local_storage` defaults to **off**).

```bash
adk deploy cloud_run --project=my-project --region=us-central1 \
    --service_name=my-agent-service my_agent

# pass extra gcloud flags after --
adk deploy cloud_run --project=my-project --region=us-central1 my_agent \
    -- --no-allow-unauthenticated --min-instances=2
```

#### deploy gke — Google Kubernetes Engine

```
adk deploy gke [OPTIONS] AGENT
```
Same family as `cloud_run`, plus GKE-specific:
- `--project TEXT` (required), `--region TEXT` (required), `--cluster_name TEXT` (**required**).
- `--service_type [ClusterIP|LoadBalancer]` (default `ClusterIP`; use `LoadBalancer` for a public IP).
- `--service_name`, `--app_name`, `--port` (default `8000`), `--with_ui`, `--adk_version` (default `2.1.0`), `--temp_folder`, `--log_level`, `--trace_to_cloud`, `--otel_to_cloud`, `--trigger_sources`, and the service-URI flags.

```bash
adk deploy gke --project=my-project --region=us-central1 \
    --cluster_name=my-cluster --service_type=LoadBalancer my_agent
```

---

## Common workflows

**1. Scaffold → run → iterate in the dev UI.**
```bash
adk create my_agent --model=gemini-2.5-flash --api_key=$GOOGLE_API_KEY
adk run my_agent "hello"                     # quick single-turn smoke test
adk web my_agent --reload_agents -v          # iterate with live reload in the browser
```

**2. Run locally with persisted SQLite sessions.**
```bash
adk run my_agent --session_service_uri=sqlite:///sessions.db --save_session --session_id=sess001
# later, resume the saved session interactively:
adk run my_agent --resume sess001.session.json
```

**3. Build an eval set, then evaluate.**
```bash
adk eval_set create my_agent/__init__.py regression
adk eval_set add_eval_case my_agent/__init__.py regression \
    --scenarios_file=scenarios.json --session_input_file=session.json
adk eval my_agent/__init__.py regression:case1,case2 \
    --print_detailed_results --eval_storage_uri=gs://my-bucket
```

**4. Optimize the root-agent prompt against eval sets (GEPA).**
```bash
adk eval_set generate_eval_cases my_agent/__init__.py train_set \
    --user_simulation_config_file=sim_config.json
adk optimize my_agent/__init__.py \
    --sampler_config_file_path=sampler.json --print_detailed_results
```

**5. Local API server, then deploy to Cloud Run (Vertex AI).**
```bash
gcloud auth application-default login
export GOOGLE_CLOUD_PROJECT=my-project GOOGLE_CLOUD_LOCATION=us-central1 GOOGLE_GENAI_USE_VERTEXAI=true
adk api_server my_agent --a2a --port=8000        # verify the headless API locally
adk deploy cloud_run --project=my-project --region=us-central1 \
    --service_name=my-agent-service my_agent \
    -- --no-allow-unauthenticated --min-instances=2
```

**6. Deploy to Agent Engine (Express Mode), then update later.**
```bash
adk deploy agent_engine --api_key=$GOOGLE_API_KEY --display_name="My Agent" my_agent
# after changes, update the existing instance (project/region mode shown):
adk deploy agent_engine --project=my-project --region=us-central1 \
    --agent_engine_id=123456789 my_agent
```

---

## Official documentation

- Docs home: https://google.github.io/adk-docs/ (301 → https://adk.dev/)
- Installation: https://google.github.io/adk-docs/get-started/installation/
- Quickstart (`create` → `run`/`web`): https://google.github.io/adk-docs/get-started/quickstart/
- Deploy to Agent Engine: https://google.github.io/adk-docs/deploy/agent-engine/
- Deploy to Cloud Run: https://google.github.io/adk-docs/deploy/cloud-run/
- Source repo: https://github.com/google/adk-python
- PyPI: https://pypi.org/project/google-adk/
- Vertex AI Agent Engine overview: https://cloud.google.com/vertex-ai/generative-ai/docs/agent-engine/overview
