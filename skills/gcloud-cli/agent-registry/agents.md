# gcloud agent-registry agents

manage Agent resources

Agents are read-only consumer-side projections of registered Services — discovery only (describe / list / search).

### `gcloud agent-registry agents describe`

Get details of an agent

Retrieve metadata and properties of a specific agent.

**Synopsis:**
```
gcloud agent-registry agents describe (AGENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Agent resource - Name of the resource. The arguments in this group can be
used to specify the attributes of this resource.

To set the project attribute:
 * provide the argument agent on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AGENT
     ID of the agent or fully qualified identifier for the agent.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the agent resource.
```

**Examples:**
```bash
To describe agent 'my-agent' in location 'us-central1', run:

    $ gcloud agent-registry agents describe my-agent --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/agents/describe)

---
### `gcloud agent-registry agents list`

List accessible agents

Displays all agents accessible by the caller in a given project and location.

**Synopsis:**
```
gcloud agent-registry agents list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location (`projects/{project}/locations/{location}`). The project attribute can be set via `--project` or the `core/project` property. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter expression to each resource item to be listed; the item is listed if the expression evaluates True. See `gcloud topic filters`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by; prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list agents in location 'us-central1', run:

    $ gcloud agent-registry agents list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/agents/list)

---
### `gcloud agent-registry agents search`

Search for agents matching a query

Searches across all accessible agents using search filter expressions.

**Synopsis:**
```
gcloud agent-registry agents search --location=LOCATION
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
| `--page-size` | PAGE_SIZE | 20 | Maximum number of agents to return (maximum 100; values above 100 are coerced to 100). |
| `--page-token` | PAGE_TOKEN |  | A page token received from a previous SearchAgents call, for pagination. |
| `--search-string` | SEARCH_STRING |  | Search criteria to restrict results. If unspecified, all accessible agents are returned. Supports `=`, `:`, `NOT`, `AND`, `OR`, `()`, and a `*` wildcard suffix. |

**Examples:**
```bash
To search agents in location 'us-central1' by display name, run:

    $ gcloud agent-registry agents search --location=us-central1 \
        --search-string="displayName:Gemini Enterprise Core Assistant"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/agents/search)

---
