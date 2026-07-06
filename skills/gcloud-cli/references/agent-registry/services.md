# gcloud agent-registry services

manage Service resources

Services are the writable side of the registry: a Service manually registers a custom or external agentic component (an agent, MCP server, or endpoint). Agent Registry automatically projects each Service onto the consumer side as a read-only Agent, McpServer, or Endpoint resource for discovery. Service resource name format: `projects/{project}/locations/{location}/services/{service}`.

### `gcloud agent-registry services create`

Register a new service

Creates a writable Service resource for manually registering custom or external agentic components into the registry.

**Synopsis:**
```
gcloud agent-registry services create (SERVICE : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--interfaces=[protocolBinding=PROTOCOLBINDING],[url=URL]]
    [--request-id=REQUEST_ID]
    [--agent-spec-type=AGENT_SPEC_TYPE : --agent-spec-content=AGENT_SPEC_CONTENT
      | --endpoint-spec-type=ENDPOINT_SPEC_TYPE : --endpoint-spec-content=ENDPOINT_SPEC_CONTENT
      | --mcp-server-spec-type=MCP_SERVER_SPEC_TYPE : --mcp-server-spec-content=MCP_SERVER_SPEC_CONTENT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Identifier. The resource name of the Service. Format:
projects/{project}/locations/{location}/services/{service}.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the service resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | User-defined description of a Service. Maximum length: 2048 characters. |
| `--display-name` | DISPLAY_NAME |  | User-defined display name for the Service. Maximum length: 63 characters. |
| `--interfaces` | [protocolBinding=PROTOCOLBINDING],[url=URL] |  | Connection details for the Service: protocol binding and destination URL. |
| `--request-id` | REQUEST_ID |  | Optional request ID (a valid UUID; zero UUID not supported) so the server can ignore duplicate requests for at least 60 minutes. |
| `--agent-spec-type` | AGENT_SPEC_TYPE |  | Type of agent spec content. Choices: `a2a-agent-card` (A2A Agent Card; the interfaces field must be empty), `no-spec` (no spec; content field must be empty). At most one spec group (agent / endpoint / mcp-server) may be specified. |
| `--agent-spec-content` | AGENT_SPEC_CONTENT |  | Content of the Agent spec in JSON format, validated against the schema. Limited to 10KB. |
| `--endpoint-spec-type` | ENDPOINT_SPEC_TYPE |  | Type of endpoint spec content. Only choice: `no-spec` (content field must be empty; reserved for future use). |
| `--endpoint-spec-content` | ENDPOINT_SPEC_CONTENT |  | Content of the endpoint spec (reserved for future use). |
| `--mcp-server-spec-type` | MCP_SERVER_SPEC_TYPE |  | Type of MCP Server spec content. Choices: `no-spec` (content field must be empty), `tool-spec` (MCP Tool Spec following the One MCP specification). |
| `--mcp-server-spec-content` | MCP_SERVER_SPEC_CONTENT |  | Content of the MCP Server spec in JSON format, validated against the schema. Limited to 10KB. |

**Examples:**
```bash
To create an agent service with an interface URL and HTTP+JSON binding, run:

    $ gcloud agent-registry services create my-service --location=us-central1 \
        --display-name="My Agent Service" \
        --agent-spec-type=no-spec \
        --interfaces="url=https://example.com/api,protocolBinding=http-json"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/services/create)

---
### `gcloud agent-registry services delete`

Remove a registered service

Deletes a specific service from the Agent Registry.

**Synopsis:**
```
gcloud agent-registry services delete (SERVICE : --location=LOCATION)
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Identifier. The resource name of the Service. Format:
projects/{project}/locations/{location}/services/{service}.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the service resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | Optional request ID (a valid UUID; zero UUID not supported); the server ignores retried requests with the same ID for at least 60 minutes. |

**Examples:**
```bash
To delete service 'my-service' in location 'us-central1', run:

    $ gcloud agent-registry services delete my-service --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/services/delete)

---
### `gcloud agent-registry services describe`

Get details of a registered service

Retrieves metadata and configuration information for a single writable Service resource used to manually register custom or external agentic components (agents, MCP servers, or endpoints) into the registry.

**Synopsis:**
```
gcloud agent-registry services describe (SERVICE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Identifier. The resource name of the Service. Format:
projects/{project}/locations/{location}/services/{service}.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

  --location=LOCATION
     The location id of the service resource.
```

**Examples:**
```bash
To describe service 'my-service' in location 'us-central1', run:

    $ gcloud agent-registry services describe my-service --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/services/describe)

---
### `gcloud agent-registry services list`

List registered services

Enumerates all writable Service resources used to manually register custom or external agentic components (agents, MCP servers, or endpoints) into the registry.

**Synopsis:**
```
gcloud agent-registry services list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location (`projects/{project}/locations/{location}`). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter expression to each resource item to be listed. See `gcloud topic filters`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by; prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list all manually registered services in location 'us-central1', run:

    $ gcloud agent-registry services list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/services/list)

---
### `gcloud agent-registry services update`

Modify service parameters

Updates properties on a writable Service resource representing a manually registered agentic component (agent, MCP server, or endpoint).

**Synopsis:**
```
gcloud agent-registry services update (SERVICE : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--request-id=REQUEST_ID]
    [--agent-spec-content=AGENT_SPEC_CONTENT --agent-spec-type=AGENT_SPEC_TYPE
      --clear-agent-spec
      | --clear-endpoint-spec --endpoint-spec-content=ENDPOINT_SPEC_CONTENT
        --endpoint-spec-type=ENDPOINT_SPEC_TYPE
      | --clear-mcp-server-spec --mcp-server-spec-content=MCP_SERVER_SPEC_CONTENT
        --mcp-server-spec-type=MCP_SERVER_SPEC_TYPE]
    [--interfaces=[protocolBinding=PROTOCOLBINDING],[url=URL]
      | --add-interfaces=[protocolBinding=PROTOCOLBINDING],[url=URL]
        --clear-interfaces
      | --remove-interfaces=[protocolBinding=PROTOCOLBINDING],[url=URL]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Identifier. The resource name of the Service. Format:
projects/{project}/locations/{location}/services/{service}.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the service resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | User-defined description of a Service. Maximum length: 2048 characters. |
| `--display-name` | DISPLAY_NAME |  | User-defined display name for the Service. Maximum length: 63 characters. |
| `--request-id` | REQUEST_ID |  | Optional request ID (a valid UUID, not all zeros); the server ignores completed duplicate requests for at least 60 minutes. |
| `--agent-spec-type` | AGENT_SPEC_TYPE |  | Type of agent spec content. Choices: `a2a-agent-card` (interfaces field must be empty), `no-spec` (content field must be empty). At most one spec group may be specified. |
| `--agent-spec-content` | AGENT_SPEC_CONTENT |  | Content of the Agent spec in JSON format, validated against the schema. Limited to 10KB. |
| `--clear-agent-spec` |  |  | Reset `service.agentSpec` to its default value. |
| `--endpoint-spec-type` | ENDPOINT_SPEC_TYPE |  | Type of endpoint spec content. Only choice: `no-spec` (content field must be empty). |
| `--endpoint-spec-content` | ENDPOINT_SPEC_CONTENT |  | Content of the endpoint spec (reserved for future use). |
| `--clear-endpoint-spec` |  |  | Reset `service.endpointSpec` to its default value. |
| `--mcp-server-spec-type` | MCP_SERVER_SPEC_TYPE |  | Type of MCP Server spec content. Choices: `no-spec` (content field must be empty), `tool-spec` (MCP Tool Spec following the One MCP specification). |
| `--mcp-server-spec-content` | MCP_SERVER_SPEC_CONTENT |  | Content of the MCP Server spec, validated against the schema. Limited to 10KB. |
| `--clear-mcp-server-spec` |  |  | Reset `service.mcpServerSpec` to its default value. |
| `--interfaces` | [protocolBinding=PROTOCOLBINDING],[url=URL] |  | Set interfaces to a new value (replaces the list). Connection details for the Service; supports shorthand, JSON, or file input. At most one interface-update group may be specified. |
| `--add-interfaces` | [protocolBinding=PROTOCOLBINDING],[url=URL] |  | Add a new value to the interfaces list. |
| `--clear-interfaces` |  |  | Clear interfaces and set it to the empty list. |
| `--remove-interfaces` | [protocolBinding=PROTOCOLBINDING],[url=URL] |  | Remove an existing value from the interfaces list. |

**Examples:**
```bash
To update the display name of service 'my-service' in location 'us-central1', run:

    $ gcloud agent-registry services update my-service --location=us-central1 \
        --display-name="New Display Name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/services/update)

---
