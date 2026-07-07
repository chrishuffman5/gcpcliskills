---
name: gcloud-network-services
description: >-
  Network Services / Cloud Service Mesh via gcloud (`gcloud network-services`). Manage Network Services resources — endpoint-policies, gateways, grpc-routes, http-routes, meshes, multicast-consumer-associations, multicast-domain-activations, multicast-domain-groups.
---

# gcloud network-services — Network Services / Cloud Service Mesh

## Overview
`gcloud network-services` manages the Network Services API resources that power **Cloud Service Mesh** (formerly Traffic Director + Anthos Service Mesh) and Google Cloud's advanced traffic-routing layer: service meshes, Envoy gateways, route resources (HTTP/gRPC/TCP/TLS), endpoint policies, service bindings, service LB policies, multicast resources, and long-running operations. Reach for it when you need to configure east-west (sidecar / proxyless gRPC) or north-south (gateway) traffic across GKE and Compute Engine workloads, or to manage edge cache and traffic-routing policies declaratively from YAML. Most resources live in the `global` location; multicast and a few regional variants are location-scoped.

## Quick reference — common workflows

### Enable the API (prerequisite)
```bash
gcloud services enable networkservices.googleapis.com
# For mesh workloads on GKE / Compute Engine, also:
gcloud services enable compute.googleapis.com
gcloud services enable container.googleapis.com   # if using GKE
```

### List and inspect resources
```bash
gcloud network-services meshes list --location=global
gcloud network-services gateways list --location=global
gcloud network-services http-routes list --location=global
gcloud network-services meshes describe my-mesh --location=global
gcloud network-services operations list --location=global
```

### Create a proxyless gRPC mesh and attach a gRPC route
```bash
# 1. Author mesh.yaml locally, then import the mesh
gcloud network-services meshes import my-mesh \
    --source=mesh.yaml --location=global

# 2. Author grpc_route.yaml (hostnames, mesh ref, rules), then import
gcloud network-services grpc-routes import my-grpc-route \
    --source=grpc_route.yaml --location=global

# 3. Verify
gcloud network-services meshes describe my-mesh --location=global
gcloud network-services grpc-routes describe my-grpc-route --location=global
```

### Set up an Envoy gateway with HTTP routing
```bash
gcloud network-services gateways import my-gateway \
    --source=gateway.yaml --location=global

gcloud network-services http-routes import my-http-route \
    --source=http_route.yaml --location=global

gcloud network-services gateways describe my-gateway --location=global

# Export the live config for backup / diff
gcloud network-services gateways export my-gateway \
    --destination=my-gateway-backup.yaml --location=global
```

### Create and tune a service LB policy
```bash
# Create with the default waterfall-by-region algorithm and a failover threshold
gcloud network-services service-lb-policies create my-lb-policy \
    --load-balancing-algorithm=waterfall-by-region \
    --failover-health-threshold=70 --location=global

# Switch to keeping traffic zone-local
gcloud network-services service-lb-policies update my-lb-policy \
    --load-balancing-algorithm=waterfall-by-zone --location=global

gcloud network-services service-lb-policies list --location=global
```

### Manage service bindings (Service Directory → mesh)
```bash
gcloud network-services service-bindings create my-service-binding \
    --location=global --description="Binding for checkout service"

gcloud network-services service-bindings list --location=global
gcloud network-services service-bindings describe my-service-binding --location=global
gcloud network-services service-bindings export my-service-binding \
    --destination=my-service-binding.yaml --location=global
```

### Inspect route views and async operations
```bash
# List route views attached to a mesh
gcloud network-services route-views list \
    --mesh projects/-/locations/-/meshes/my-mesh

# Describe a specific gateway route view
gcloud network-services route-views describe \
    --project=$PROJECT_ID --location=global \
    --gateway my-gateway --route-view $ROUTE_VIEW_ID

# Wait on / cancel a long-running operation
gcloud network-services operations wait OPERATION_NAME
gcloud network-services operations cancel OPERATION_NAME
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `network-services endpoint-policies` | [`endpoint-policies.md`](endpoint-policies.md) | 5 | manage Network Services EndpointPolicies |
| `network-services gateways` | [`gateways.md`](gateways.md) | 5 | manage Network Services Gateways |
| `network-services grpc-routes` | [`grpc-routes.md`](grpc-routes.md) | 5 | manage Network Services GrpcRoutes |
| `network-services http-routes` | [`http-routes.md`](http-routes.md) | 5 | manage Network Services HttpRoutes |
| `network-services meshes` | [`meshes.md`](meshes.md) | 5 | manage Network Services Meshes |
| `network-services multicast-consumer-associations` | [`multicast-consumer-associations.md`](multicast-consumer-associations.md) | 5 | manage Network Services MulticastConsumerAssociations |
| `network-services multicast-domain-activations` | [`multicast-domain-activations.md`](multicast-domain-activations.md) | 5 | manage Network Services MulticastDomainActivations |
| `network-services multicast-domain-groups` | [`multicast-domain-groups.md`](multicast-domain-groups.md) | 5 | manage Network Services MulticastDomainGroups |
| `network-services multicast-domains` | [`multicast-domains.md`](multicast-domains.md) | 5 | manage Network Services MulticastDomains |
| `network-services multicast-group-consumer-activations` | [`multicast-group-consumer-activations.md`](multicast-group-consumer-activations.md) | 5 | manage Network Services MulticastGroupConsumerActivations |
| `network-services multicast-group-producer-activations` | [`multicast-group-producer-activations.md`](multicast-group-producer-activations.md) | 5 | manage Network Services MulticastGroupProducerActivations |
| `network-services multicast-group-range-activations` | [`multicast-group-range-activations.md`](multicast-group-range-activations.md) | 5 | manage Network Services MulticastGroupRangeActivations |
| `network-services multicast-group-ranges` | [`multicast-group-ranges.md`](multicast-group-ranges.md) | 5 | manage Network Services MulticastGroupRanges |
| `network-services multicast-producer-associations` | [`multicast-producer-associations.md`](multicast-producer-associations.md) | 5 | manage Network Services MulticastProducerAssociations |
| `network-services operations` | [`operations.md`](operations.md) | 4 | manage Network Services Operations |
| `network-services route-views` | [`route-views.md`](route-views.md) | 2 | view Network Services Route Views |
| `network-services service-bindings` | [`service-bindings.md`](service-bindings.md) | 7 | manage Network Services Bindings |
| `network-services service-lb-policies` | [`service-lb-policies.md`](service-lb-policies.md) | 7 | manage Network Services ServiceLbPolicies |
| `network-services tcp-routes` | [`tcp-routes.md`](tcp-routes.md) | 5 | manage Network Services TcpRoutes |
| `network-services tls-routes` | [`tls-routes.md`](tls-routes.md) | 5 | manage Network Services TlsRoutes |

See [`index.md`](index.md) for a one-line index of all 100 GA commands.

## Common flags & tips
- **`--location`** is required on every `list` and on most resource operations. Meshes, gateways, routes, service bindings, and LB policies are typically created at `--location=global`; multicast and regional variants use a region.
- **Declarative YAML workflow** — meshes, gateways, routes, service bindings, and service LB policies all expose `import` / `export`. Use `export --destination=FILE.yaml` to capture live state, edit, then `import --source=FILE.yaml`. Omit `--destination`/`--source` to use stdout/stdin. Exported YAML omits output-only fields, so it round-trips cleanly.
- **`--async`** on `delete` / `import` (and other mutating commands) returns immediately and hands you an operation you can poll with `gcloud network-services operations wait OPERATION_NAME`.
- **Service LB policy algorithms** (`--load-balancing-algorithm`): `spray-to-region`, `spray-to-world`, `waterfall-by-region` (default), `waterfall-by-zone`. Tune failover with `--failover-health-threshold` (1–99; default 50 for proxyless mesh, 70 otherwise) and drain unhealthy backends with `--auto-capacity-drain`.
- **Route views** are read-only (`list` / `describe` only). `list` requires either `--mesh` or `--gateway`; `describe` additionally requires `--route-view` plus the parent `--mesh`/`--gateway` and `--location`. You can pass a fully qualified resource path (e.g. `--mesh projects/-/locations/-/meshes/mesh1`) instead of separate `--project`/`--location` flags.
- **Filtering / formatting:** standard `--filter`, `--limit`, `--sort-by`, and `--uri` apply to all `list` commands, e.g.
  ```bash
  gcloud network-services meshes list --location=global \
      --filter="labels.env=prod" --format="table(name, createTime)"
  gcloud network-services gateways list --location=global --uri
  ```

## beta / alpha
- **GA (`gcloud network-services`):** all 20 subgroups above, including the `multicast-*` groups.
- **`gcloud beta network-services`:** largely mirrors GA; the beta reference explicitly lists the multicast groups alongside the GA commands.
- **`gcloud alpha network-services`:** adds `regional-multicast-*` variants (e.g. regional-multicast-consumer-associations, regional-multicast-domain-activations, regional-multicast-group-*) and `observability-policies`, which are not in GA. The core service-routing surface (Mesh, Gateway, HTTP/gRPC/TCP/TLS routes) is fully GA.

## Official documentation
- [Cloud Service Mesh docs home](https://docs.cloud.google.com/service-mesh/docs) — product docs: managed / in-cluster control planes, security, observability.
- [Service routing overview](https://docs.cloud.google.com/service-mesh/docs/service-routing/service-routing-overview) — the Mesh / Gateway / HTTPRoute / GRPCRoute / TCPRoute / TLSRoute resource model, required API, and IAM roles.
- [Set up a proxyless gRPC mesh](https://docs.cloud.google.com/service-mesh/docs/service-routing/set-up-proxyless-mesh) — end-to-end `meshes import` + `grpc-routes import` quickstart.
- [gcloud network-services reference](https://docs.cloud.google.com/sdk/gcloud/reference/network-services) — full GA command/flag reference (alpha/beta variants linked from there).

See [`sources.md`](sources.md) for the full citation list.
