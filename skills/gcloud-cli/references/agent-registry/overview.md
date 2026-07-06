# gcloud agent-registry — Agent Registry

## Overview

Agent Registry (part of the Gemini Enterprise Agent Platform) is a centralized catalog that lets you store, discover, and govern Model Context Protocol (MCP) servers, tools, and AI agents within Google Cloud. The registry's data model splits into a producer side and a consumer side: you manually register custom or external agentic components as writable **Service** resources, and Agent Registry automatically projects each Service onto the consumer side as a read-only **Agent**, **McpServer**, or **Endpoint** resource for discovery. **Bindings** connect a source agent to a target resource (another agent, an MCP server, or an endpoint) or associate an agent with an auth provider for delegated permissions. Mutating commands (create/update/delete) run as long-running **Operations** you can track with the `operations` group.

## Quick reference — common workflows

### 1. Enable the API and grant access

```bash
gcloud services enable agentregistry.googleapis.com --project=PROJECT_ID

# Predefined roles: roles/agentregistry.admin, roles/agentregistry.editor,
# roles/agentregistry.viewer
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="user:USER@example.com" \
    --role="roles/agentregistry.viewer"
```

### 2. Register an agentic component as a Service

```bash
gcloud agent-registry services create my-service \
    --location=us-central1 \
    --display-name="My Agent Service" \
    --agent-spec-type=no-spec \
    --interfaces="url=https://example.com/api,protocolBinding=http-json"
```

### 3. Discover agents in the registry

```bash
# List all agents accessible by the caller in a project/location
gcloud agent-registry agents list --location=us-central1

# Search agents with a search-string expression
gcloud agent-registry agents search --location=us-central1 \
    --search-string="displayName:Gemini Enterprise Core Assistant"

# Inspect one agent
gcloud agent-registry agents describe my-agent --location=us-central1
```

### 4. Discover MCP servers and endpoints

```bash
gcloud agent-registry mcp-servers list --location=us-central1
gcloud agent-registry mcp-servers search --location=us-central1 \
    --search-string="name:tool*"
gcloud agent-registry endpoints list --location=us-central1
```

### 5. Connect a source agent to a target with a binding

```bash
gcloud agent-registry bindings create my-binding --location=us-central1 \
    --source-identifier=urn:agent:my-agent-1:projects:123:locations:us-central1:aiplatform:reasoningEngines:123 \
    --target-identifier=urn:agent:my-agent-2:projects:123:locations:us-central1:aiplatform:reasoningEngines:456 \
    --auth-provider-binding=projects/my-project/locations/us-central1/connectors/my-connector
```

### 6. Track long-running operations

```bash
gcloud agent-registry operations list --location=us-central1
gcloud agent-registry operations describe OPERATION --location=us-central1
gcloud agent-registry operations wait OPERATION --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `agent-registry agents` | [`agents.md`](agents.md) | 3 | manage Agent resources |
| `agent-registry bindings` | [`bindings.md`](bindings.md) | 6 | manage Binding resources |
| `agent-registry endpoints` | [`endpoints.md`](endpoints.md) | 2 | manage Endpoint resources |
| `agent-registry mcp-servers` | [`mcp-servers.md`](mcp-servers.md) | 3 | manage Mcp Server resources |
| `agent-registry operations` | [`operations.md`](operations.md) | 5 | manage Operation resources |
| `agent-registry services` | [`services.md`](services.md) | 5 | manage Service resources |

See [`index.md`](index.md) for a one-line index of all 24 commands.

## Common flags & tips

- **Everything is regional — `--location` is (nearly) always required.** `describe`-style commands take it as part of the resource argument (`RESOURCE : --location=LOCATION`, or pass a fully qualified name); `list`/`search`/`fetch-available` take it as a required flag identifying `projects/{project}/locations/{location}`.
- **Writable vs read-only resources.** Only `services` (and `bindings`) have create/update/delete. `agents`, `mcp-servers`, and `endpoints` are read-only projections of registered Services — discovery only (`describe`/`list`/`search`).
- **URN identifiers.** Bindings reference resources by URN: source is always `urn:agent:{publisher}:{namespace}:{name}`; targets may be `urn:agent:…`, `urn:mcp:…`, or `urn:endpoint:…`.
- **`search` vs `list`.** `list` supports the standard gcloud `--filter`/`--sort-by`/`--limit`/`--uri` flags. `search` (agents, mcp-servers) uses a server-side `--search-string` supporting `=`, `:`, `NOT`, `AND`, `OR`, `()`, and a `*` wildcard suffix, with `--page-size` (default 20, max 100) and `--page-token` pagination.
- **Mutations are LROs.** `create`/`update`/`delete` accept `--async` to return immediately, and `--request-id` (a unique UUID; zero UUID not supported) for idempotent retries — the server ignores duplicate requests for at least 60 minutes. Follow up with `operations describe`/`wait`.
- **Spec flags on `services create`/`update`.** At most one spec group per Service: `--agent-spec-type` (`a2a-agent-card` | `no-spec`), `--mcp-server-spec-type` (`no-spec` | `tool-spec`), or `--endpoint-spec-type` (`no-spec`, reserved). Spec content is JSON, validated against a schema, limited to 10KB. With `a2a-agent-card` the `interfaces` field must be empty.
- **API surface:** most commands use the `agentregistry/v1` API; the `operations` command pages cite `agentregistry/v1alpha`.

## beta / alpha

There is no `gcloud beta agent-registry` surface (the beta reference page returns 404). An **alpha** surface (`gcloud alpha agent-registry`) mirrors the same six groups and commands as GA with no alpha-only groups documented; it is experimental and may change without notice.

## Official documentation

- **Product docs home:** https://docs.cloud.google.com/agent-registry/overview — Agent Registry overview (Gemini Enterprise Agent Platform).
- **Setup:** https://docs.cloud.google.com/agent-registry/setup — enable `agentregistry.googleapis.com` and grant IAM roles.
- **Quickstart:** https://docs.cloud.google.com/agent-registry/quickstart-register-agent — register your first agent.
- **Data model:** https://docs.cloud.google.com/agent-registry/data-model — Services, Agents, McpServers, Endpoints, Bindings.
- **Key concepts:** https://docs.cloud.google.com/agent-registry/concepts — concepts and terminology.
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/agent-registry — the `gcloud agent-registry` command group.
