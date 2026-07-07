# gcloud agent-registry mcp-servers

manage Mcp Server resources

MCP servers are read-only consumer-side projections of registered Services — discovery only (describe / list / search).

### `gcloud agent-registry mcp-servers describe`

Get details of an MCP server

Retrieve configuration and metadata for a specific MCP server.

**Synopsis:**
```
gcloud agent-registry mcp-servers describe (MCP_SERVER : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
McpServer resource - Name of the resource. The arguments in this group can
be used to specify the attributes of this resource.

This must be specified.

  MCP_SERVER
     ID of the mcpServer or fully qualified identifier for the mcpServer.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the mcpServer resource.
```

**Examples:**
```bash
To describe MCP server 'my-mcp-server' in location 'us-central1', run:

    $ gcloud agent-registry mcp-servers describe my-mcp-server \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/mcp-servers/describe)

---
### `gcloud agent-registry mcp-servers list`

List registered MCP servers

Enumerates all Model Context Protocol servers in a given project and location.

**Synopsis:**
```
gcloud agent-registry mcp-servers list --location=LOCATION
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
To list all MCP servers in location 'us-central1', run:

    $ gcloud agent-registry mcp-servers list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/mcp-servers/list)

---
### `gcloud agent-registry mcp-servers search`

Search MCP servers matching criteria

Finds registered MCP servers matching specified search expressions.

**Synopsis:**
```
gcloud agent-registry mcp-servers search --location=LOCATION
    [--page-size=PAGE_SIZE] [--page-token=PAGE_TOKEN]
    [--search-string=SEARCH_STRING] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location (`projects/{project}/locations/{location}`). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--page-size` | PAGE_SIZE | 20 | Maximum number of MCP servers to return (maximum 100). |
| `--page-token` | PAGE_TOKEN |  | A page token received from a previous SearchMcpServers call, for pagination. |
| `--search-string` | SEARCH_STRING |  | Search criteria to restrict results (e.g. by `mcpServerId`, `name`, `displayName`, or combinations). Supports `=`, `:`, `NOT`, `AND`, `OR`, `()`, and a `*` wildcard suffix. |

**Examples:**
```bash
To search MCP servers in location 'us-central1' whose name starts with 'tool', run:

    $ gcloud agent-registry mcp-servers search --location=us-central1 \
        --search-string="name:tool*"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/mcp-servers/search)

---
