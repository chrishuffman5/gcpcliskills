# gcloud agent-registry bindings

manage Binding resources

Bindings connect a source agent to a target resource (another agent, an MCP server, or an endpoint) or associate an agent with an auth provider for delegated permissions. Binding resource name format: `projects/{project}/locations/{location}/bindings/{binding}`.

### `gcloud agent-registry bindings create`

Create a new binding

Establishes a connection between a source agent and a target resource (another agent, MCP server, or endpoint), or associates an agent with an auth provider for delegated permissions.

**Synopsis:**
```
gcloud agent-registry bindings create (BINDING : --location=LOCATION)
    --source-identifier=SOURCE_IDENTIFIER
    --target-identifier=TARGET_IDENTIFIER [--async]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--request-id=REQUEST_ID]
    [--auth-provider-binding=AUTH_PROVIDER_BINDING
      : --auth-provider-binding-continue-uri=AUTH_PROVIDER_BINDING_CONTINUE_URI
      --auth-provider-binding-scopes=[AUTH_PROVIDER_BINDING_SCOPES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Binding resource - Identifier. The resource name of the Binding. Format:
projects/{project}/locations/{location}/bindings/{binding}.

This must be specified.

  BINDING
     ID of the binding or fully qualified identifier for the binding.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the binding resource.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-identifier` | SOURCE_IDENTIFIER |  | The identifier of the source Agent. Format: `urn:agent:{publisher}:{namespace}:{name}`. |
| `--target-identifier` | TARGET_IDENTIFIER |  | The identifier of the target Agent, MCP Server, or Endpoint. Formats: `urn:agent:{publisher}:{namespace}:{name}`, `urn:mcp:{publisher}:{namespace}:{name}`, `urn:endpoint:{publisher}:{namespace}:{name}`. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | User-defined description of a Binding. Maximum length: 2048 characters. |
| `--display-name` | DISPLAY_NAME |  | User-defined display name for the Binding. Maximum length: 63 characters. |
| `--request-id` | REQUEST_ID |  | Optional request ID (a valid UUID; zero UUID not supported) so the server can ignore duplicate requests for at least 60 minutes. |
| `--auth-provider-binding` | AUTH_PROVIDER_BINDING |  | The resource name of the target AuthProvider. Format: `projects/{project}/locations/{location}/authProviders/{auth_provider}`. |
| `--auth-provider-binding-continue-uri` | AUTH_PROVIDER_BINDING_CONTINUE_URI |  | The continue URI of the AuthProvider, for reauthentication and finalizing the OAuth flow. |
| `--auth-provider-binding-scopes` | [AUTH_PROVIDER_BINDING_SCOPES,...] |  | Comma-separated list of OAuth2 scopes for the auth provider binding. |

**Examples:**
```bash
To create a binding between two agents, run:

    $ gcloud agent-registry bindings create my-binding --location=us-central1 \
        --source-identifier=urn:agent:my-agent-1:projects:123:locations:us-central1:aiplatform:reasoningEngines:123 \
        --target-identifier=urn:agent:my-agent-2:projects:123:locations:us-central1:aiplatform:reasoningEngines:456 \
        --auth-provider-binding=projects/my-project/locations/us-central1/connectors/my-connector
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/bindings/create)

---
### `gcloud agent-registry bindings delete`

Delete a binding connection

Removes an existing binding connection between a source agent and a target resource or auth provider.

**Synopsis:**
```
gcloud agent-registry bindings delete (BINDING : --location=LOCATION)
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Binding resource - The name of the Binding. Format:
projects/{project}/locations/{location}/bindings/{binding}.

This must be specified.

  BINDING
     ID of the binding or fully qualified identifier for the binding.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the binding resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | Optional request ID (a valid UUID; zero UUID not supported) so the server can ignore duplicate requests for at least 60 minutes. |

**Examples:**
```bash
To delete binding 'my-binding' in location 'us-central1', run:

    $ gcloud agent-registry bindings delete my-binding --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/bindings/delete)

---
### `gcloud agent-registry bindings describe`

Retrieve binding details

Retrieves configuration information for a specific binding connection between a source agent and a target resource or authentication provider.

**Synopsis:**
```
gcloud agent-registry bindings describe (BINDING : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Binding resource - The name of the Binding. Format:
projects/{project}/locations/{location}/bindings/{binding}.

This must be specified.

  BINDING
     ID of the binding or fully qualified identifier for the binding.

  --location=LOCATION
     The location id of the binding resource.
```

**Examples:**
```bash
To describe binding 'my-binding' in location 'us-central1', run:

    $ gcloud agent-registry bindings describe my-binding --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/bindings/describe)

---
### `gcloud agent-registry bindings fetch-available`

Fetch bindings

Retrieves available bindings for agents, MCP servers, or endpoints.

**Synopsis:**
```
gcloud agent-registry bindings fetch-available --location=LOCATION
    [--source-identifier=SOURCE_IDENTIFIER]
    [--target-identifier=TARGET_IDENTIFIER] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location (`projects/{project}/locations/{location}`). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-identifier` | SOURCE_IDENTIFIER |  | The identifier of the source Agent. Format: `urn:agent:{publisher}:{namespace}:{name}`. |
| `--target-identifier` | TARGET_IDENTIFIER |  | The identifier of the target Agent, MCP Server, or Endpoint. Formats: `urn:agent:…`, `urn:mcp:…`, `urn:endpoint:…`. |
| `--filter` | EXPRESSION |  | Apply a Boolean filter expression to each resource item to be listed. See `gcloud topic filters`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by; prefix a field with `~` for descending order. |

**Examples:**
```bash
To fetch all bindings, run:

    $ gcloud agent-registry bindings fetch-available
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/bindings/fetch-available)

---
### `gcloud agent-registry bindings list`

List bindings

Enumerates connections between source agents and target resources (downstream agents, MCP servers, endpoints) or auth providers in a targeted location.

**Synopsis:**
```
gcloud agent-registry bindings list --location=LOCATION
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
| `--filter` | EXPRESSION |  | Apply a Boolean filter expression to each resource item to be listed. Flag interaction order: `--flatten`, `--sort-by`, `--filter`, `--limit`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by; prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list bindings in location 'us-central1', run:

    $ gcloud agent-registry bindings list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/bindings/list)

---
### `gcloud agent-registry bindings update`

Modify binding parameters

Updates properties on a binding connecting a source agent to a target resource or auth provider.

**Synopsis:**
```
gcloud agent-registry bindings update (BINDING : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--request-id=REQUEST_ID]
    [--auth-provider-binding=AUTH_PROVIDER_BINDING]
    [--auth-provider-binding-continue-uri=AUTH_PROVIDER_BINDING_CONTINUE_URI]
    [--clear-auth-provider-binding]
    [--auth-provider-binding-scopes=[AUTH_PROVIDER_BINDING_SCOPES,...]
      | --add-auth-provider-binding-scopes=[ADD_AUTH_PROVIDER_BINDING_SCOPES,...]
      | --clear-auth-provider-binding-scopes
      | --remove-auth-provider-binding-scopes=[REMOVE_AUTH_PROVIDER_BINDING_SCOPES,...]]
    [--clear-source] [--source-identifier=SOURCE_IDENTIFIER]
    [--clear-target] [--target-identifier=TARGET_IDENTIFIER]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Binding resource - Identifier. The resource name of the Binding. Format:
projects/{project}/locations/{location}/bindings/{binding}.

This must be specified.

  BINDING
     ID of the binding or fully qualified identifier for the binding.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the binding resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | User-defined description of a Binding. Maximum length: 2048 characters. |
| `--display-name` | DISPLAY_NAME |  | User-defined display name for the Binding. Maximum length: 63 characters. |
| `--request-id` | REQUEST_ID |  | Optional request ID (a valid UUID) for idempotent retries; the server ignores duplicates for at least 60 minutes. |
| `--auth-provider-binding` | AUTH_PROVIDER_BINDING |  | The resource name of the target AuthProvider. Format: `projects/{project}/locations/{location}/authProviders/{auth_provider}`. |
| `--auth-provider-binding-continue-uri` | AUTH_PROVIDER_BINDING_CONTINUE_URI |  | The continue URI of the AuthProvider for reauthentication and finalizing the OAuth flow. |
| `--clear-auth-provider-binding` |  |  | Reset `binding.authProviderBinding` to its default value. |
| `--auth-provider-binding-scopes` | [SCOPES,...] |  | Set auth_provider_binding_scopes to a new value (replaces the list). |
| `--add-auth-provider-binding-scopes` | [SCOPES,...] |  | Append values to the auth_provider_binding_scopes list. |
| `--clear-auth-provider-binding-scopes` |  |  | Clear auth_provider_binding_scopes and set it to the empty list. |
| `--remove-auth-provider-binding-scopes` | [SCOPES,...] |  | Remove existing values from the auth_provider_binding_scopes list. |
| `--source-identifier` | SOURCE_IDENTIFIER |  | The identifier of the source Agent. Format: `urn:agent:{publisher}:{namespace}:{name}`. |
| `--clear-source` |  |  | Reset `binding.source` to its default value. |
| `--target-identifier` | TARGET_IDENTIFIER |  | The identifier of the target Agent, MCP Server, or Endpoint. Formats: `urn:agent:…`, `urn:mcp:…`, `urn:endpoint:…`. |
| `--clear-target` |  |  | Reset `binding.target` to its default value. |

**Examples:**
```bash
To update the display name of binding 'my-binding' in location 'us-central1', run:

    $ gcloud agent-registry bindings update my-binding --location=us-central1 \
        --display-name="Updated Binding Name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/bindings/update)

---
