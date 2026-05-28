# gcloud service-extensions — Service Extensions

## Overview
Service Extensions lets you insert custom code directly into the data path of Google Cloud networking products — Application Load Balancers, Media CDN, and Secure Web Proxy. It supports two mechanisms: **plugins** (WebAssembly/Proxy-Wasm modules run inline by Google-managed sandboxes, stored as container images in Artifact Registry) and **callouts** (gRPC calls to your own external services on VMs, GKE, or Cloud Run). Reach for it when you need to rewrite headers/bodies, influence CDN caching or backend selection, or delegate authorization without modifying your backends. The `gcloud service-extensions` group manages the resources: `wasm-plugins`/`wasm-plugin-versions` for plugins and four load-balancer extension types (`lb-edge-extensions`, `lb-route-extensions`, `lb-traffic-extensions`, `authz-extensions`) for callouts.

## Quick reference — common workflows

### 1. Create a WasmPlugin with an initial version
```bash
# Enable the backing API (one-time per project)
gcloud services enable networkservices.googleapis.com

# Create the WasmPlugin and its first version (v1), set as the serving version
gcloud service-extensions wasm-plugins create my-plugin \
    --location=global \
    --main-version=v1 \
    --image=us-central1-docker.pkg.dev/PROJECT/REPOSITORY/CONTAINER:TAG \
    --description="My custom plugin" \
    --log-config=enable=True,sample-rate=1.0,min-log-level=INFO
```

### 2. Add a new plugin version and promote it
```bash
# Create v2 from a new image
gcloud service-extensions wasm-plugin-versions create v2 \
    --wasm-plugin=my-plugin \
    --location=global \
    --image=us-central1-docker.pkg.dev/PROJECT/REPOSITORY/CONTAINER:v2 \
    --description="Version 2"

# Promote v2 to the main (serving) version
gcloud service-extensions wasm-plugins update my-plugin \
    --location=global \
    --main-version=v2

# Verify the current state
gcloud service-extensions wasm-plugins describe my-plugin --location=global
```

### 3. Import an LbTrafficExtension (callout) from YAML
```bash
# Define the extension in my-traffic-extension.yaml referencing your
# forwarding rule and a backend service callout, then import it.
gcloud service-extensions lb-traffic-extensions import my-traffic-extension \
    --source=my-traffic-extension.yaml \
    --location=us-central1

# Inspect and list
gcloud service-extensions lb-traffic-extensions describe my-traffic-extension \
    --location=us-central1
gcloud service-extensions lb-traffic-extensions list --location=us-central1
```

### 4. Import an AuthzExtension (delegated authorization)
```bash
gcloud service-extensions authz-extensions import my-authz-extension \
    --source=my-authz-extension.yaml \
    --location=us-central1

gcloud service-extensions authz-extensions list --location=us-central1
```

### 5. Import edge (global) and route (regional) extensions
```bash
# LbEdgeExtension is global
gcloud service-extensions lb-edge-extensions import my-edge-extension \
    --source=my-edge-extension.yaml \
    --location=global
gcloud service-extensions lb-edge-extensions list --location=global

# LbRouteExtension is regional
gcloud service-extensions lb-route-extensions import my-route-extension \
    --source=my-route-extension.yaml \
    --location=us-central1
```

### 6. Inspect and clean up plugin resources
```bash
# List plugins and the versions of one plugin
gcloud service-extensions wasm-plugins list --location=global
gcloud service-extensions wasm-plugin-versions list \
    --wasm-plugin=my-plugin --location=global

# Delete a single non-serving version, then the whole plugin
gcloud service-extensions wasm-plugin-versions delete v1 \
    --wasm-plugin=my-plugin --location=global
gcloud service-extensions wasm-plugins delete my-plugin --location=global
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `service-extensions authz-extensions` | [`authz-extensions.md`](authz-extensions.md) | 4 | manage AuthzExtension resources (delegate authorization to a custom external engine) |
| `service-extensions lb-edge-extensions` | [`lb-edge-extensions.md`](lb-edge-extensions.md) | 4 | manage LbEdgeExtension resources (manipulate request headers earliest, e.g. CDN caching) |
| `service-extensions lb-route-extensions` | [`lb-route-extensions.md`](lb-route-extensions.md) | 4 | manage LbRouteExtension resources (influence backend selection before URL map evaluation) |
| `service-extensions lb-traffic-extensions` | [`lb-traffic-extensions.md`](lb-traffic-extensions.md) | 4 | manage LbTrafficExtension resources (modify request/response headers and bodies) |
| `service-extensions wasm-plugin-versions` | [`wasm-plugin-versions.md`](wasm-plugin-versions.md) | 4 | manage WasmPluginVersion resources (individual versions of a plugin) |
| `service-extensions wasm-plugins` | [`wasm-plugins.md`](wasm-plugins.md) | 5 | manage WasmPlugin resources (Proxy-Wasm modules) |

See [`index.md`](index.md) for a one-line index of all 25 commands.

## Common flags & tips
- **Location is required and resource-specific.** All four LB extension groups and the wasm groups take `--location`. `lb-edge-extensions` are **global** (`--location=global`); `lb-route-extensions`, `lb-traffic-extensions`, and `authz-extensions` are **regional** (e.g. `--location=us-central1`). For `wasm-plugins`/`wasm-plugin-versions`, location defaults to `global` only on some subcommands — pass `--location` explicitly to be safe. You can also encode the location in a fully qualified resource name.
- **`wasm-plugin-versions` always need `--wasm-plugin`** to identify the parent plugin.
- **Create vs. version semantics on `wasm-plugins update`:** if you pass `--image`, you must also pass `--main-version` (a new version is created and promoted) and `--async` is disallowed; without `--image`, only the plugin metadata is updated and `--main-version` must reference an existing version.
- **`--log-config`** (on `wasm-plugins create`/`update`) is a key=value list: `enable`, `sample-rate` (0.0–1.0), `min-log-level` (e.g. `INFO`). Example: `--log-config=enable=True,sample-rate=0.5,min-log-level=INFO`.
- **The LB extensions are import-driven.** There is no `create`/`update` verb — you define the resource (forwarding rules, extension chains, match conditions, callout service) in YAML and use `import`. Omit `--source` to read the YAML from standard input.
- **Long-running operations:** add `--async` to return immediately instead of waiting (not supported on `wasm-plugins update` when `--image` is set).
- **Cleanup caution:** deleting a `wasm-plugins` resource also deletes all of its versions; a version that is the current `main-version` cannot be deleted.
- **Filtering/formatting `list`:** the `list` subcommands support the standard `--filter`, `--sort-by`, `--limit`, and `--uri`. Examples:
  - `gcloud service-extensions wasm-plugins list --location=global --filter="labels.env=prod"`
  - `gcloud service-extensions lb-traffic-extensions list --location=us-central1 --format="table(name,forwardingRules)"`

## beta / alpha
Both `gcloud beta service-extensions` and `gcloud alpha service-extensions` exist and expose the same six command groups as GA; the beta/alpha label reflects overall stability ("might change without notice") rather than a different command set. The **alpha** track additionally lists a `wasm-actions` group (early-access). No GA-absent flags were identified for the 25 GA commands documented here.

## Official documentation
- [Service Extensions docs home](https://cloud.google.com/service-extensions/docs) — product overview, guides, and API reference.
- [Service Extensions overview](https://cloud.google.com/service-extensions/docs/overview) — plugins vs. callouts and when to use each.
- [Cloud Load Balancing extensions overview](https://cloud.google.com/service-extensions/docs/lb-extensions-overview) — LbEdgeExtension, LbRouteExtension, LbTrafficExtension, and AuthzExtension.
- [Callouts overview](https://cloud.google.com/service-extensions/docs/callouts-overview) — ext_proc / ext_authz protocols and user-managed deployment.
- [Plugins overview](https://cloud.google.com/service-extensions/docs/plugins-overview) — WasmPlugin/WasmPluginVersion resources and Proxy-Wasm constraints.
- [Create a plugin (how-to)](https://cloud.google.com/service-extensions/docs/create-plugin) — step-by-step WasmPlugin creation with gcloud.
- [Access control (IAM)](https://cloud.google.com/service-extensions/docs/access-control) — roles and permissions for Service Extensions.
- [gcloud service-extensions CLI reference](https://cloud.google.com/sdk/gcloud/reference/service-extensions) — full command/flag reference.
